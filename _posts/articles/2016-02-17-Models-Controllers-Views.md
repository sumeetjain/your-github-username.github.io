---
layout: post
title: "models! controllers! views!"
modified:
categories: articles
excerpt: what are these WORDS you keep USING
tags: []
image:
  feature:
date: 2016-02-17T15:39:55-04:00
---

Models, Controllers, and Views are all about database manipulation, and database manipulation is what makes the web go round. 

As is the case with 99% of the things you're learning, you interact with Models, Controllers, and Views all the time. You just didn't know their names or all the magical little things they were doing to load your twitter page. 

Models are Classes with superpowers. You can write helpful methods within them, but they also come with the database access capabilities of ActiveRecord (ActiveRecord is a supreme act of kindness from someone who figured out a lot of super handy database shortcuts and decided to share those with you). For every unique kind of information stored in your database, you should have a Model. For example, in a Swim Tournament database, you'd want at the very least a Model for Swimmer and one for Event. Then as you figure out the needs of your application, you can add things like Registration and School. 

Models organize nicely in my brain. I call much fewer methods on inproper objects, because Models feel so...real. A good question to ask when you're stuck is "who am I asking for this information?" Sometimes you realize you're asking an Event what school it goes to and you need to rethink things.

Controllers are where your Ruby happens. It takes every click on a page and uses that to do your bidding. It finds all that pesky information that's hiding in the belly of your database and returns it (or runs a method on it, or updates it) and sends the user to the appropriate View.

Views are just that--places where the user views information--information that you sent there via your Models and Controllers. A view might let a user fill out a form or vote on something, but views don't actually do any work. Controllers do all the work. Views get all the glory.

It doesn't sound very flashy, but once you wrap your brain around them you're going to be excited about these. They're gonna make some very exciting things possible for you.


