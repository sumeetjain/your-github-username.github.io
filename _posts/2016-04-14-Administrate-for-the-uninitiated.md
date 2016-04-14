---
layout: post
title: Administrate for the uninitiated… 
---

Many of us, when we’re first clawing our way through the muck of CRUD functions, find ourselves tearfully wishing there were a better way.  Well, turns out that there is. It’s called [Administrate](https://rubygems.org/gems/administrate/versions/0.0.2) and it’s a charming little gem that you can add to your Rails project to get you all that wonderful back-end functionality that previously you’d spent hours trying to make from scratch. When paired with [Devise](https://rubygems.org/gems/devise/versions/3.5.6), another useful gem, you can add user verification to the mix with relatively few headaches.  

In this post, I’ll focus mostly on Administrate and a few useful things I’ve figured out about incorporating it into Rails projects.For the purposes of this article, I’ll be assuming that Devise is already installed.

## Getting started

Thoughtbot does a really good job of explaining install and what have you so, rather than reinvent the wheel, I’ll just urge you to checkout Thoughtbot’s [install instructions](https://github.com/thoughtbot/administrate#getting-started) on Github.

## Next steps

Once you’ve got the gem itself installed, be sure to bring up your local host and check out how much work that little line of code has saved you.  You’ll have CRUD functions for all of your tables, a customizable interface for interacting with your database, and far less stress in getting there. Pretty cool, right?  Now, in looking at what you’ve got you’ll notice a few things you _don’t have_ right out of the gate.  

- The views and forms it produces for you might not be quite as you’d like them and they’ll require some adjustment.
- It will be necessary to connect up the user authentication you’ve got through Devise with Administrate.  
- Amusingly enough, once you figure out how to do that you’ll need to figure out how to include a logout.  
- Additionally, I’ve found that adding in dropdowns and how it displays its data are important to really ensuring the user experience is a good one.

## Customizing Dashboards

You’ll notice in the lists and forms that Administrate provides that you don’t always see what you’d like to see or in the format that you’d like to see it.  As with many things on Administrate, customizing this isn’t that hard to do.  Running the `rails g administrate:install` command during set-up added a bunch of files to your project.  Among these, you’ll find a slew of dashboard files for all the tables in your database schema.  The dashboard files have a lot of good documentation in them as to what each section does and how best to alter them.  It is however worth noting a few things:

1. The format for setting the attributes is `fieldname: Field::Fieldclass`  So, if you wanted to indicate a field for email it’d look like `email: Field::Email`  
2. Thereafter, you refer to the attribute by fieldtype:  So, our email attribute would just be `email:`
3. `Field::fieldclass` allows you to specify a number of types of `Field` classes.  In particular: BelongsTo, Boolean, DateTime, Email, HasMany, HasOne, Image, Number, Polymorphic, and String.  Each of these can be further specified by using the `.with_options` class. Details on this can be found [here](http://administrate-prototype.herokuapp.com/customizing_dashboards).
4. As you move down through the sections of the dashboard files, you’ll want to think critically about what it is you really want stored in your database and what you want displayed.  If you installed Administrate after Devise, you’ll have an attribute for the `encrypted_password` that will will display for every user you’ve got.  Obviously, this is probably not something you want to have on display.
5. The last thing to make note of with your dashboards is a commented out bit at the very bottom that looks like this:

{% highlight ruby %}
# Overwrite this method to customize how abouts are displayed
# across all pages of the admin dashboard.
#
# def display_resource(about)
#   "User ##{user.id}"
# end
{% endhighlight %}
  
As the comment says, this little bit of code, when uncommented, will dictate how this particular resource is viewed throughout the admin dashboard.  So, if you were to uncomment this and leave it be, your user would be referred to by their id number throughout the whole of Administrate.  If you’d rather have that user’s name on display, here’s the place to change it.

## Joining up with Devise

Adding in the user authentication provided by Devise proved to be easier than I’d thought.  To restrict access for all of Administrate to just registered users, you add the following line of code to the **admin/application_controller** controller:
{% highlight ruby %}
before_action :authenticate_user!
{% endhighlight %}
As an added bit of fun, if you want to restrict certain admin functions to particular users, do the following:

Add an admin boolean to the table for the resource you’re trying to restrict.
If, for example, you were trying to restrict user creation, then after adding a boolean to the users table that indicates true or false if they have admin privileges, you’d add the following line to your **admin/users_controller** controller:

{% highlight ruby %}
    before_filter :authenticate_admin, only: [:new, :edit]
{% endhighlight %}
This restricts access to user creation and editing to only those users with admin privileges.

Then, you add this method to your users_controller.rb file:
  
{% highlight ruby %}
def authenticate_admin
        If current_user.nil? || !current_user.admin?
        redirect_to '/admin', {alert: "You are not authorized to edit or create users."}
end
{% endhighlight %}  
  
This will authenticate their privileges and kick up a message to anyone who doesn’t have them telling them that they’re not allowed to alter that resource. Pro tip:  Make sure you’ve got a user created with admin privileges before you uncomment the above lines of code. 

## Logging out

Now that you can log in, it’s rather important that you can log out again.  You’ll want to have a simple link your user can push to accomplish this::

{% highlight ruby %}
<%= link_to "Log Out", destroy_user_session_path, method: :delete %>
{% endhighlight %}

Where to put it is a bit of a puzzle though, or at least it was for me.  However, delving into the documentation, it turns out that Administrate will happily generate views for you of almost anything you can think of.  While you could put the above link in several places, the ideal place would be accessible via every page of Administrate and clearly visible -- perhaps the sidebar that lists all of our tables. 

However, even a cursory glance through the views created when you first install Administrate will show you that there’s not such a view in evidence.  Not to worry.  Administrate is very good at generating the requisite views. In command line, run`rails g administrate:views sidebar` and the gem will create just the view we’re looking for.  There, you’ll find a nice little loop that displays all the aforementioned tables.  I chose to stick the logout link right below this loop.  You’ll notice when you refresh the page that the link shows up, though it is without styling.

## Dropdowns

One last little thing that I found useful in my time with administrate: dropdown menus.  It’s really nice when you’re creating a new user or what have you to not have to type everything in by hand.  It is also much more useful to be able to select a value that’s not a foreign key, but rather an actual name or type. Conveniently, in Administrate these are accomplished quite handily through the use of ActiveRecord associations.  Simply put, if you’ve got an association going between two models, the dropdowns are generated automatically.  

##In conclusion

This is just a small sampling of what administrate seems capable of and I’d highly encourage you to take a close look at the documentation that Thoughtbot’s provided for this.  Almost none of it, with the exception of where to stash the logout link, took more than a few minutes of fumbling around in the code.  If you’ve any questions or have something else you’d like to add, I’d be happy to hear it. 
