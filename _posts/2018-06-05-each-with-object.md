---
layout: post
current: post
navigation: True
title: "each_with_object"
excerpt: "each_with_object"
categories: Programming
tags: [journal]
date: 2018-06-05
class: post-template
comments: false
subclass:
author:
---

I've been wrestling with a slightly nasty refactor story recently. The following is my first iteration of a method that loops through a hash of `@nameservers` and for each one assigns the `host` to an instance variable in the class, then loops through each IP in the `info` hash and adds the output from a private method in the `@results` hash.
That's a lot of looping.


```ruby
def check
    @results = {}
    @nameservers.each do |host, info|
      @host = host
      info[:ips].each do |nameserver_ip|
        @results[nameserver_ip] = ip_check(nameserver_ip)
      end
    end

    @results
+end
```
`@nameservers` is a hash that looks something like this:
```ruby
{
            "Google" => {
        :country => "USA",
            :ips => [
            [0] "8.8.8.8",
            [1] "8.8.4.4"
        ]
    },
           "OpenDNS" => {
        :country => "USA",
            :ips => [
            [0] "208.67.222.222",
            [1] "208.67.220.220"
        ]
    },
         "Fortalnet" => {
        :country => "Brazil",
            :ips => [
            [0] "189.90.16.20",
            [1] "189.90.16.21"
        ]
    },
    "Probe Networks" => {
        :country => "Germany",
            :ips => [
            [0] "82.96.64.2",
            [1] "82.96.65.2"
        ]
    }
}
```
What's the best way to simplify that method? Well, another dev turned me on to the `each_with_object` method. Instead of defining and returning the `@results` hash explicitly, it can be incorporated into one of the loops. How it works?

```ruby
			def check
				@nameservers.each_with_object({}) do |(host, info), results|
					info[:ips].each do |nameserver_ip|
						results[nameserver_ip] = ip_check(host, nameserver_ip)
					end
				end
			end
```
When you call `each_with_object` on `@nameservers` I'm passing an empty hash as the argument. (It doesn't need to be an empty hash. It can be a pre-existing hash or even an array). Inside the block you pass the object or objects to loop over, in this case `host` and `info`, and then the variable name you want to assign the object you passed in as an argument. So my hash will be returned as `results`. 
The second loop in my method remained almost exactly the same, except that I decided to pass `host` through to my private `ip_check` method as well so that the state wasn't leaking into the rest of the object. 