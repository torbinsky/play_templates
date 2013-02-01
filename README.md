play_templates
==============

Learning repo for understanding how advanced use cases of Playframework UI templates can be done.


Description:
==============

Previously in other templating systems I have been able to nest templates, similar to class inheritance in Java.
This allowed for generic pieces of UI code to be defined once in one, root template. This makes updating views easy
(i.e. adding a root level style/script).


Example Use Case:
==============

Main template: 
--------------

Contains very basic HTML features, no structure. Primarily for including scripts like JQuery and styles
such as Twitter Bootstrap etc...

Primary structure template:
--------------

Defines many of the basic structural components. May need to include more CSS/JS. 
For example, this may be where the layout for a two-pane page with header and footer is defined. Possibly
some navigation widgets etc...

Leaf node 1 (or this could continue nesting):
--------------

As 3 levels should be all that is required for the example, this last level is a specific implementation page. 
For example, this might be an account details page or some type of CRUD form.
This page may also need to include some additional CSS/JS resources.

PSEUDO'sh Scala Template Code:
--------------
main.scala.html:


