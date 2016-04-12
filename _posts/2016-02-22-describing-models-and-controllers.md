---
layout: page
title: Describing Models, Views, and Controllers
---
<h3>Describing Models, Views, and Controllers</h3>

Within the context of a database drivin web application Models, Views, and Controllers are basically the 3 main functions of your website.  

*Views*
These are pages that in the end are translated to text and sent back to the user.

*Models*
Models are pages that store your methods for each table you create in your database, all behind the scenes.  Basically, a page where you can define extra actions your tables know how to perform.

*Controllers*
Controllers are the tricky ones.  If you have code that cant be used in a Model because it's singular to the situation you can put it in the controller. When the user sends a request to view a webpage the first thing that happens is the controller matching that request is found. If you have stipulated that Ruby code needs to run in the controller, then that is it's next step. The controller then figures out the webpage to display as a response (which is the erb view file).  As a bonus any ruby code ran in the controller you display _in_ the view file because the very last thing it does is it runs any ruby code on the view file converts the file to text and then sends it back to the user. 