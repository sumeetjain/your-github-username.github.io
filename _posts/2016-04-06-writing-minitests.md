---
layout: post
current: post
navigation: True
title: "Writing Ruby MiniTests for custom database queries"
excerpt: "Everything you wanted to know about testing."
categories: Programming
tags: [tests, ruby]
date: 2016-04-06
class: post-template
comments: false
subclass:
author:
---


Let me preface this by saying that I FRAKKING LOVE TESTS. With Unit testing, I get to clearly & objectively prove that my code is awesome and works as intended. And there’s very little I love more than proving I’m right.

So a thing that you should do as a developer is test all of the methods in your models. That’s called unit testing. I’m going to use a Sinatra project to show you how to test a method using the MinitTest gem. MiniTest uses assertions to determine whether or not a method functions successfully. Here is a guide to the different assertions available: [MiniTest Assertions](http://ruby-doc.org/stdlib-2.0.0/libdoc/minitest/rdoc/MiniTest/Assertions.html)

One thing you should know about the MiniTest gem is that it creates a separate database to test your methods. This will be important later, when we set our tests up. The great thing about MiniTests is that it not only sets our DB up for us, but it also tears it down once our tests run.

Here is the method that I want to test. It searches for a Movie object with a specific title from our database:

```
   def Movie.movie_search_title(search_text)
    movie_match = Movie.where({"title" => search_text})
    if movie_match.empty?
      return nil
    else
      return movie_match
    end
   end

```
So what we need to do is test this method. Tests act independently from our application though and as I said, they create a new database. So the first thing we’ll do, is seed ( or ‘create’) a new database specifically to test this method. For this method, we need Movie objects in order to test it out. Let’s create a few Movies.  If you’ve ever created a controller for a new object, it probably looks similar to those blocks below. You create a new object, then you assign it certain parameters that correspond to your database columns, and then follow up by saving it to the database.


```
require 'test_helper'

class MovieTest < Minitest::Test
  def setup
    super
    @movie1 = Movie.new
    @movie1.title = "Barfi"
    @movie1.director = "Some dude"
    @movie1.critic_rating = "100"
    @movie1.save

    @movie2 = Movie.new
    @movie2.title = "Hello Beth"
    @movie2.director = "Some lady"
    @movie2.critic_rating = "100"
    @movie2.save

    @movie3 = Movie.new
    @movie3.title = "Hello Class"
    @movie3.director = "Some dude"
    @movie3.critic_rating = "50"
    @movie3.save
  end
```

Okay, that wasn’t so bad. You’ve got your database seeded. Now what?
Well, we can start writing tests. One thing to remember about testing a method is that there is more than one possible outcome. For this method there happen to be two possible outcomes. You can either find a movie that matches the input, or you can’t. We should test both outcomes. Let’s start with finding a match.

1. First, you should define your test name so it’s obvious which outcome of which method you are testing. 

   ```
def test_movie_search_title
```
2. Next, we need to tell our test what this method should return based on our database, so we’ll use an assertion called `assert_includes`. With this assertion, we expect that this search with the input of `”Barfi”` should return the Movie object `@movie1`:

   ```
assert_includes(Movie.movie_search_title("Barfi"), @movie1)
```

3. Another testable item, is to check if a certain movie is _not_ returned when we search for `”Barfi”`, so we’ll use the `refute_includes` assertion:

   ```
refute_includes(Movie.movie_search_title("Barfi"), @movie2)
```

4. Make sure to end your test!:

   ```
def test_movie_search_title
   assert_includes(Movie.movie_search_title("Barfi"), @movie1)
   refute_includes(Movie.movie_search_title("Barfi"), @movie2)
end 
```

5. So we’ve tested our method when it should return a result, because there is a matching Movie object in the database, but what about when there is no matching Movie object? Well, that will look a little something like this. We start the same way, by defining the name of the test so it’s clear what we’re testing. In this case, we’re testing what happens when the result is nil:

   ```
   def test_movie_search_title_nil
   ```

6. Next, we’ll use a new assertion called `assert_nil`. There is no movie with the title `“hi derek”` in our database so our method should return `nil`:

   ```
   assert_nil(Movie.movie_search_title("hi derek"))
   ```

7. Don’t forget to end the method _and_ the test object!:

   ```
   def test_movie_search_title_nil
      assert_nil(Movie.movie_search_title("hi derek"))
   end
end
```

