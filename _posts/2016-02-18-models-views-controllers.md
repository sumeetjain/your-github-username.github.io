---
layout: post
title: Models and Views and Controllers! Oh My!
description: "Learning from my mistakes..."
category: articles
tags: [web, technical, internet]
---

Today we're going to talk about the purpose of models, controllers, and views and how they work (mainly within the context of Sinatra). So grab a cup of coffee (or the caffeinated beverage of your choice) and get yourself cozy.

First we'll start with models (for no particular reason other than the fact that "Models" is the first word in the title of this journal). It should be said that models (in Sinatra) are nothing more than Ruby code in a .rb file. In that sense, there's nothing really special about models (code-wise). What we use models for, however, is quite specific and can be vital in making a web app do the things we want it to do. 

If we want our classes (I'll use 'classes' and 'models' interchangeably from here on out) to get all of the nice magic and functionality that ActiveRecord offers, we will need to make sure we give each model ActiveRecord inheritance. Once we do this, lots of nice things will be done for which we won't have to write any code (Lazy? Perhaps. But very smart!)! 

In our model files, we'll need to add any additional methods that we want each of our classes to have. Say we're writing a database for an online shoe store and we want a class dedicated to shoe brands. That's great, but we'll want to make sure we can connect the shoe's brand to many other tables/classes so we keep things in good order (and present our customers with more information than just the brand.) This is where our models can come in handy. They can allow us to write methods that give us access to other tables and their respective data. Or perhaps our shoe store stops carrying a certain brand altogether. In this case we could write a method in our model that we can use to delete only the appropriate information from other tables (we probably wouldn't want to delete all information). The possibilities are pretty much endless. Just know that in your models, you'll include methods for any of the "heavy-lifting" that you'd like your class to have.

Views are... well they're for viewing. I don't know how else to put it. Views are ultimately what we want our users to see. To display "hello world" somewhere on a web page, we'd want a view file to do this. Our view files are saved as "erb" (Embedded RuBy), which allow us to use bits of ruby code throughout the view, which would otherwise normally be just HTML/CSS (the stuff that makes website look pretty). Using Ruby in our views allows us to have a bit of control over what in the page the user might see (which can be very handy at times).

Controllers are necessary for pretty much anything to "happen" so to speak,(especially so far as the user is concerned). There's a reason they have their name. I think of controllers as being kinda like air traffic controllers, but with controllers, web pages wouldn't crash into each other, they would just be quite static and boring (and clicking on links and buttons would do nothing other than throw an error message).


If we were going to make an extremely simple web app that only displayed the cliché  "Hello world," we would still need a controller to make this happen. To do this, we would have to use the "get" method in our controller. The "get" method would basically say "If someone types this address into the URL, or clicks a link with this URL, do the following stuff." Since we're wanting to give the user a page that says "hello world," we would have that controller return the file in our "views" that contains the page with our "hello world" message.

Any page that we want our users to see will require us to use a controller of some sort. When we only need our users to view pages (as opposed to submitting or changing data or information), we will use the "get" method we mentioned above. If we are needing information from the user, or if they're changing or deleting something from our database), in these cases we would want to use the "post" method in our controllers. Either way, the controller is what allows us to get stuff from and back TO the user (back and forth from the database). 

I hope this helps clarify the very basics of why we use models, views, and controllers. 





