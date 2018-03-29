---
layout: post
title: "Journal Entry - March 26, 2018"
excerpt: "A new (to me) Enumberable method"
categories: Programming
tags: [journal]
date: 2018-03-29
comments: false
---

So I was helping one of our front-end devs on a view the other day and he needed a collection of objects to be in a very specific order. The problem was that it required a very ugly and somewhat confusing query:
```ruby
@in_progress = migration_request_group.current_migration_requests.sort_by { |x| x.in_progress_in_group? ? 0 : 1 }.sort_by { |x| x.pending? ? 0 : 1 }
```
It first sorts the `current_migration_requests` so that if the request currently being looped over is `in_progress_in_group?`, it gets moved to the first position in the array, otherwise it's moved to the second position. And _then_ it checks if that request is pending. If so, it get's moved into the first position. If you're just looking at the code for the first time, it's not easy to understand at all. 

I knew there had to be a better way. I just didn't know what that better way was... 

Fortunately, I'm on a team of seasoned Ruby developers who helped me out. It turns out there's this method called `partition` that's actually been around a while. 

```ruby
pending, rest = migration_request_group.current_migration_requests.partition(&:pending?)
in_progress, rest = rest.partition(&:in_progress_in_group?)
@in_progress = pending + in_progress + rest
```

Here's how it works:
There are two arrays: `pending` and `rest`. The first one, `pending`, will store any objects that the block finds true, while `rest` will store the rest of the objects. Then I do another partition block where I take that existing `rest` array and split it into two more arrays: `in_progress` and, again, `rest`.
Then I combine the arrays in the required order. It may take up three lines of code instead of one, but I believe it's much clearer.
