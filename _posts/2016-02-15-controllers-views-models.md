---
layout: post
current: post
navigation: True
title: "What are Models, Controllers, and Views"
excerpt: "MVC and what they're all about."
categories: Programming
tags: [ruby, backend]
date: 2016-02-15
class: post-template
comments: false
subclass:
author:
---

Models are ruby files where you define unique classes and methods for those classes. You create one model per unique class. When you're utilizing active record, the model also correlates to each table that is defined in the database schema.

Controllers are your directions for the servers. When a user clicks a link or types in the browser, your controller is what communicates to the server which page to show the user and the server sends that page back.

Views are the pages that the user sees. They contain HTML and often also include embedded ruby (which is why the file type is .erb ). You can use your embedded ruby to show data from your database.