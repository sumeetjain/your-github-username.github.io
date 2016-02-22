---
title: Models, Views, and Controllers
---

We started playing around with ActiveRecord and databases recently and this led us into contact with three new beasties for our menagerie of coding creatures.  In particular these are models, views, and controllers(MVC).  So far as I can tell, these three things work in conjuction to expand the functionality of HTML while allowing one to avoid too much SQL coding.

HTML is great at displaying text and images, but isn't set up to really crunch numbers in the same way that a language like Ruby, Java, etc is.  So, if you want your page to do something other than just display text and images you need to find a way to incorporate the something like ruby into the page.  Of our three, ruby lives in the models and controllers, moreso in the models.  

**Models** are essentially Ruby classes that have inherited a whole bunch of methods from ActiveRecord that are geared towards dealing with databases.  This inheritance is accomplished with the following bit of code:

{% highlight ruby %}
class RandomClass < ActiveRecord::Base
end
{% endhighlight %}

This basically tells the computer that the RandomClass class has all the methods at the disposal of the ActiveRecord superclass.  While we've not delved into the nitty gritty of what makes this work, it's a fun little trick as Ruby, by itself, doesn't have a whole slew of native methods for dealing with creating, reading, updating, and deleting (CRUD) database information.  That sort of thing is better suited to a programming language like SQL, but since it might not always be convenient to pick up a whole other language, and we are beginners after all, the functionality that's added by ActiveRecord functions as a useful bridge.  

**Controllers**, as the name suggests, control requests for information and generally tell that information where to go.  The server makes a request and the controllers steer the information to the appropriate view.  While Ruby code does show up here as well, I get the impression that the majority of the heavy lifting codewise is supposed to be done primarily by the models.  A controller looks like this:

{% highlight ruby %}
MyApp.get "/" do
  erb :"main/main"
end
{% endhighlight %}

The top line basically says, "If you get a request from the server for '/', then do this".  The "this" it's referring to is the erb tag, which in this case is directing server to the main/main view.  Remember, as we said, HTML doesn't know what to do with Ruby, to HTML, Ruby code is just text.  In the end, that's all the HTML will see it as.  The MVCs together, take in data, either from a database or user input, send it to the models, and to a lesser extent, the controllers, the Ruby is interpreted there, the output sent back as _just_ text and HTML, knowing how to deal with text, displays that text.  The controllers manage this process.

**Views** are probably the most straightforward of the three.  They're simply what is ultimately displayed on the page, written up with HTML.  Scattered throughout a view you'll find ERB tags.  They look like this:

{% highlight ruby %}
<%= Ruby code %>
{% endhighlight %}

ERB stands for Embedded RuBy and indicates where a bit of Ruby code is to be run somewhere other than on the page itself and the result of that code gets displayed between the ERB tags as text.

Altogether, this process, that I admit I'm still trying to fully grasp greatly extends the capabilities of HTML and allows us, through the integration of databases and all the CRUD fun to be had there, to do a lot more than we were before now.  For me, this answers a question I'd had about how we integrate programs into HTML.
