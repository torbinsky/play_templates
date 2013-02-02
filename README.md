play_templates
==============

Learning repo for understanding how advanced use cases of Playframework UI templates can be done.


Description:
==============

Previously in other templating frameworks I have been able to nest templates, similar to class inheritance in Java.
This allowed for generic pieces of UI code to be defined once in one, root template. This makes updating views easy
(i.e. adding a root level style/script).

Design Approach:
==============
Similar to other templating frameworks, template inheritance would allow common pieces of UI code to be shared
without requiring duplicated code which is difficult and error-prone to update.

Main template: 
--------------

Contains very basic HTML features, no structure. Primarily for including scripts like JQuery and styles
such as Twitter Bootstrap etc...

Primary structure template:
--------------

An example of what this could be used for is a common type of page layout. This might include some navigation widgets and
other common pieces of UI that the implementing pages would share in common.

* Defines many of the basic structural components.
* Needs ability to push additional header content (CSS/JS)
* Needs ability to push page content

Leaf node 1 (or this could continue nesting):
--------------

For brevity, in this example the 3rd level is the final level (leaf node pages). This last level is a page that has unique
content that is not shared with other pages. For example, this might be an account details page or some type of CRUD form.

* Further adds to page structure as required by specific use cases
* Needs ability to push additional header content (CSS/JS)
* Needs ability to push page content

Example Scenario:
==============

* The site _Example Co._ has an admin interface and some public pages which have different structures.
* The public pages have different structure than the admin pages.
** The public pages don't need to be implemented for the example. They are mentioned for illustrative purposes only.
* All of the pages (both admin and public) share a few common resources (some CSS, HTML, javascript, etc...).
* The admin pages have a two-pane structure where the left pane contains navigation links.
** The navigation links and structure is specific to the admin pages and should not be shared with the public pages

PSEUDO'sh Scala Template Code:
--------------

main.scala.html:
	@(title: String)(content: Html, headerContent: Html = Html(""))
	<html>
		<head>
			<title>@title</title>
			@headerContent
		</head>
		<body>
			@content
		</body>
	</html>

admin.scala.html:
	...?
	@main(...?)
	...?

users.scala.html:
	...?
	@admin(...?)
	...?