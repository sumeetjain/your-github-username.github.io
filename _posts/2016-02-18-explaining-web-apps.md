---
title: Models, Controllers, and Views, Oh My!
---

The internet is magic. It encapsulates practically the entirety of human knowledge reached by just a few keystrokes and clicks. Instant access to information has become so prevalent that we take it for granted. Today, we take a look at the inner workings of a single Google (the universally accepted verb it has become, not the information oligarch from whence it came). How can you type a few words in a text field, hit 'enter', and be whisked away to a world of your choosing?

Well, for starters, there's a vast and complex physical infrastructure holding it all together, but we're going to ignore that for now. What we're interested in is that near-instanteous exchange this infrastructure allows. We'll start with you, the user, typing away in one search engine or another: 'C', 'A', 'T'. Once you hit 'enter', the magic begins. At this point you've made what is known by those in the know as a 'request'. And so begins our Odyssey (but, you know, a million times faster and much fewer mythical beasts)...

From here your request, assuming your route matches one in existence, is passed to a Controller. Think of this little guy as a traffic cop you've asked for directions. He takes a look at the request you've made almost like directions on a road map and matches it to the corresponding Controller Action. This Controller Action acts like a piece of the map, matching the directions you have. At this point our Controller cop might notice that you need some tools to complete your journey. This is where the fabled Model comes into play.

The Model is aptly named as it acts like a replica of a defined piece of a Database. Combined with a bunch of built-in actions (think verbs), and you have a template for how you can interact with the Database (well, not you the user, but the controller).

So your request has been directed by a Controller that acts as a go-between to the Model. In this case, your request for 'CAT' is a GET. Just as it sounds, you're requesting the Database to 'get' some information for you. While you wait with Controller cop, the data is retrieved, packaged up all neat, and returned. Now Controller cop receives your precious 'CAT' data pacakge and points you on your way. But wait, you, or your browser for that matter, don't understand how the seemingly jumbled bunch of 0's and 1's in this package translates into the fluffy kitties you requested. We need something to make sense of all of this. Views to the rescue. 

Our precious polyglot translator, the View takes the package passed from the Model and makes sense of it all. Depending on whatever coding language we're dealing with, the View unpackages the info and lays it out all neat so the browser and ultimately you, can read it. Once everything is in its place, back to Controller cop we go.

Now that the View has translated all of the garbled data from that Database for us, Controller cop points us back to our browser with all of our data in tow. Nevermind that this data is bundled up separately in neat little packages. And so we're at the final leg of journey. A split-second ago, you typed in 'CAT', hit 'enter', and now your internet browser is crawling with cuteness. All it took was the concerted effort of our friends Controllers, Models, and Views.

Now, there may be more seasoned coders among our readership smirking at this explanation. I am admittedly a n00b to all of this and this is just my understanding of the magic that is the Internet, so don't take my word for it.
Enjoy!