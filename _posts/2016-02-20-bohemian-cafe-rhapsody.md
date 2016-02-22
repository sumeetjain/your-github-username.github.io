---
title: Bohemian Cafe Rhapsody 
---

Warning: The following does NOT include any discussion of Bohemian Rhapsody, Queen's opus maximus. I'm using "rhapsody" more generically in this case, as an enthusiastic expression of feelings. 

In the first entry on this blog, I pledged to try to tell the truth. So, here's a truth: This entry, and some others that will come along throughout, is not just me reflecting on Omaha Code School ("OCS") and/or my random encounters with web technology. Sometimes Sumeet provides a topic. Today's topic: models, controllers and views. Explain them to somebody who has one week less of experience with them than you do. 

You may not know that you know what models, controllers and views are, but you do know. They are players in the request-response cycle through which internet business is conducted. They are also quotidian in business, not just internet business, and there may even be something like them in some plain old interpersonal reactions. 

The prosaic and web-specific answer is that models, controllers and views are elements in the web's request-and-response cycle of doing business. The request is everything we as web users ask the internet to do for us, from buying 1,000 shares of Facebook to adding a "Like" to a cat photo. Those and a grandillion (ok I made that one up) other things we do on the internet all start as requests. 

Anyway, the request goes to the controller, which tries to formulate a response to it. What the controller actually "controls" is internal distribution of work. It assigns work, especially to the models. 

Models interact with the database. The database is the warehouse of information we are attempting to manipulate to fulfill the request. Every database is its own little North Korea. It can't see out, and most of our program cannot see in. Models, and models alone, have the methods necessary to interact with the database. 

Views are what we as web users see. The controllers have done their best to interpret the request, the models have done their best to follow those instructions if they have anything to do with the database, and sent what they got back to the controller, who passed it on to the views. The views have packaged up whatever the controllers sent to them and presented it to the user who made the request. Perhaps with nervous, hopeful smiles on their faces. 

This seems like a good time to set aside the internet for a minute and reclaim the request-response cycle for the tangible world. To see it in action, walk with me about half a block south, down the surprisingly wide sidewalk from Omaha Code School, to a gracefully aging and kind of tarted up matron of a Czech restaurant called The Bohemian Cafe. The proximity of The Bohemian is a mixed blessing for those of us who need to watch our carb intake, but it also serves up a satisfying, made-to-order plateful of analogy. 

If you walk through the front door of the Bohemian Cafe with food on your mind, you will interact first with a kroje-wearing member of the wait staff, who takes your order. Then a cook prepares your meal, with your choice of mashed potatoes or dumplings. You don't go back and meet the cook but you'll get to sample their work. And, for the sake of this analogy, let's say somebody other than your wait person, like a day manager, brings you your food. It would be sexist to only describe what the women of the wait staff are wearing (and women they all are at the tradition-bound Bohemian Cafe) so I'll make up a day manager that's a he. He is wearing a burgundy blazer and his voice is a little too loud for the room. Perhaps he has a nervous, hopeful smile as he delivers your food. 

And just like that, your trip to the Bohemian covers all of the request-response bases, and exercises the controllers, models and views therein.

Placing an order is a request. Your wait person is the controller. (Remember to tip your controller.) The controller distributes work, in this case to the cook. The cook is not dressed like a model, but is the equivalent of the model. The cook gets instructions from the wait person. Instead of manipulating a database using lines of code, the cook manipulates an inventory of ingredients using recipes to try to give you what you ordered. The person who presents your food to you is the view. Good news! Your food is on a plate, not on a web page. It is the response.

The Bohemian is just the nearby example. Maybe it would be overreach but close to accurate to say that in business, the controller is in management, the models are in product development, and the views are in sales. And if you are Sumeet or a (not grandillion) other small business owners, you get to be all three. 




 
