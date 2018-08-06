---
layout: post
current: post
navigation: True
title: "HoneyBadger exceptions and the engineers who raise them."
excerpt: "HoneyBadger exceptions and the engineers who raise them."
categories: Programming
tags: [journal]
date: 2017-12-18
class: post-template
comments: false
subclass:
author:
---

I've been on EE (Escalate to Engineering) duty the past few days, which means it can be hard to focus on a larger story when I have no idea when I'll get interrupted to fix an issue with the app. Not a big deal. There's no better time to bite off a few Honey Badger errors. I tend to track down the LetsEncrypt-associated errors since I still feel a sense of ownership over Simple SSL, despite over a year having passed since building it and seeing multiple engineers adding their own _touches_ (i.e. bug-fixes). 

Today was no exception. It's been a while since I dug into HoneyBadger and there was quite a backlog to work with. About 30k exceptions had been raised in the past few months due to some faulty code in one of our workers. A couple of objects were being passed incorrectly named keyword arguments and in some cases, one or two of the required arguments weren't getting passed in at all. It was a pretty straightforward fix. While I was in there I made sure to default the arguments to nil and also update the calls made to the method in the worker so they were using the correct keyword argument names.

A watered-down example of my changes...

Before:

```ruby
class Workers:LetsEncrypt

    def notify(msg:, detail:)
        Honeybadger.context(certificate_id: @certificate.id, detail: detail)
        Honeybadger.notify(error_message: msg)
    end

    def raise_and_report_error(error_type, error_detail, ip_address)
        if error_detail.include? "Foo"
            notify msg: "Acme::Client::Error #{error_type} Foo.", activity: "Foo failed. #{error_detail}"
        elsif error_detail.include? "Bar"
            notify msg: "Acme::Client::Error #{error_type} Bar."
        end
    end
end
```

After:

```ruby
class Workers:LetsEncrypt

    def notify(msg: nil, detail: nil)
        Honeybadger.context(certificate_id: @certificate.id, detail: detail)
        Honeybadger.notify(error_message: msg)
    end

    def raise_and_report_error(error_type, error_detail, ip_address)
        if error_detail.include? "Foo"
            notify msg: "Acme::Client::Error #{error_type} Foo.", detail: "Foo failed. #{error_detail}"
        elsif error_detail.include? "Bar"
            notify msg: "Acme::Client::Error #{error_type} Bar."
        end
    end
end
```

Notice that in first conditional of the `raise_and_report_error` method in the **Before** example, the `notify` method was getting passed a keyword argument named `activity` despite the method having no such named argument. And the second conditional was no better really. Only one of the two required keyword arguments was getting passed.

In the **After** example, I just had to rename the incorrectly named keyword_argument and I also ensured that an argument could get left off of the call and the method would still run by adding a default to both of the `notify` method arguments.