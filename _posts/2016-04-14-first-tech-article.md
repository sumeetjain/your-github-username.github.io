---
layout: post
title: Using JavaScript Event Listeners
description: "Introduction to JavaScript Event Listeners and How to Use Them."
category: articles
tags: [general, time frame]
---


Almost no one wants a website that doesn’t let the user make at least some sort of interaction with the content. It goes without saying that we want to give the user the impression that they are doing something with or to the website and that things are actually happening before their very eyes as they click, type, or scroll through the page.

Thankfully, web browsers allow us to make some pretty neat things happen when a user does something (as opposed to an action occurring upon the loading of a page) thanks to JavaScript and all of its magic.

Enter the JavaScript event listener. Event listeners are what allow us to tell our pages what kinds of events to listen for (hence the name) so that a particular action may then follow, as designated by a block of code in the Event Listener itself. 

Let’s say, for example, we know that we want something to happen only when a particular button on our page is clicked on by the user. Let’s also say that we want to set it it up so that when the button is clicked, an alert is then displayed to the user that says “Banana!” One example of how we could prepare the page to anticipate the user’s click, and make the alert show is as follows:

```javascript
var bananaButton = document.getElementById("bananaButton");
bananaButton.addEventListener(“click”, function(){
     alert(“Banana!”);
});
``` 
The first part of the code uses the `getElementById` method to specify the exact element we want to work with. In this case, we’ve stored the element into a variable called `bananaButton` (we’ll pretend like we already assigned an `id` of “bananaButton” to the button in our HTML file). It isn’t a requirement to first store the target as a variable, but it helps clean up the code a little bit. 
We then call the `addEventListener` method on the `bananaButton` target so that the browser knows that it needs to anticipate a certain event pertaining to this specific button. While the addEventListener method technically takes in more than just two arguments, we’ll just focus on the two most commonly used two arguments.
The first argument is the event type, and in our example we used `“click”` to tell the browser that we want the code to be executed when the button is actually clicked on. There are far more event types out there other than just “click,” and I highly recommend you try a quick Google search to so see the many types of events we can reference to trigger a desired action. 
Next, we have the block of code that we want to run when the event occurs (written as an anonymous function, or in other words a function without a name). The code block is important because it’s what indicates exactly what we want to happen when an event occurs. In this simple example, we’ve provided code that will tell the browser to display an alert once the button is clicked. It’s important to know that this code will not actually be run until the button itself is clicked, which is what we want. This is why we need to put the code block as an argument in the event listener. It ensures that the specified event is the very thing that triggers action to follow. 
The important thing to take away here is that making a successful event listener involves creating a target element (either stored as a variable or simply chained to the `addEventListener` method using `getElementById`), passing an event as the first argument (i.e. `“click”`, `“keyup”`, `“scroll”` etc…) and finally, passing in the block of code (using JavaScript’s anonymous function syntax) that you want to run once the event is triggered. 
That’s it! Give it a try. This is a very simple example and there are many more complex and powerful things we can do with the DOM (Document Object Model). 
