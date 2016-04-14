---
layout: post
title: "Event Listeners"
description: ""
category: articles
---

Have you ever wondered how a web page reacts to your actions? When you’re typing your address into a form and the zip code appears as soon as you’ve finished entering your city and state; when you click on a ‘More Info’ link and a new window pops up; when you click ‘Next’ on a list and get taken to the next page -- these instances are all thanks to JavaScript Event Listeners.

Event listeners play a vital part in how JavaScript allows a user to interact with a page. They tell the website that, when the user takes some specific action, a specific reaction should follow. 

Event listeners have two main components that are of importance to programmers: the “event”, the user action that will enact whatever code is inside of the listener, and the “callback”, the program’s reaction to the event.

Here is one example of an event listener:

``` js
var textField = document.getElementById(“input_text”);

textField.addEventListener("keyup", function() {
  var echoField = document.getElementById("greeting");

  echoField.innerHTML = ("Hello " + textField.value + ".");
}); 
```

In this instance, “keyup” is the user’s action (the “event”) that will enact the rest of the code. When a key has been pressed and then released, it will trigger the reaction (the “callback”). These are some of the most common event listeners (from http://digitalarts.bgsu.edu/):

“click” -- when the mouse is clicked
“mousemove” -- when the cursor is moving while over an object
“mouseover” -- when the cursor is moved onto an element
“mouseout” -- when the cursor is moved off of an element
“keyup” -- when a key is released
“keydown” -- when a key is pressed
“focus” -- when an element gets focus
“blur” -- when an element loses focus
“select” -- when some text has been selected
“load” -- when an object has been loaded

In the example above, the event listener is called on the variable “textField”. This means that the block of code is listening for a key release specifically when something is typed into “textField”, not just anywhere on the page.

The second part of an event listener (the “callback”) contains the bulk of the code and functionality. The callback should include whatever code is vital to the functionality of the event listener’s feature. This can include setting variables, checking user input against a database, showing or hiding certain elements, auto-completing a text field, and anything else that can be written in JavaScript.
