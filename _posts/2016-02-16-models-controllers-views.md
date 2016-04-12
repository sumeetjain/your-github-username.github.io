---
layout: post
title: "Models, Controllers, and Views"
description: ""
category: articles
---

Models, controllers, and views are the three main facets of a website developed with Ruby on Sinatra. They all play vital roles in controlling what a website looks like and how it functions.

**Models:** Models have proven to be the most difficult part of our recent project for me to understand, and I'm far from alone in our class. They exist so that a developer can create classes for each table the database contains, and to write methods for the class to be able to access.

**Controllers:** Controllers are like the switchboard of a website. They take input in the form of a link, form, or url submitted by the user, and they tell the program what to do with that input and where to send the website next. It's a good idea to organize controllers and models in the same way for the sake of organization, because once a website becomes complex enough, it's easy to get lost in lists of files.

**Views:** These files, saved as .erb filetype (which is HTML but which can also read Ruby with the correct tags), are the actual pages sent to the website that the user will view. The controller will direct the user to one of these views, and whatever is written on the view file is what will appear to the user on the page.