---
layout: post
current: post
navigation: True
title: "Fun query"
excerpt: "Fun query"
categories: Programming
tags: [journal]
date: 2018-07-11
class: post-template
comments: false
subclass:
author:
---


Right now we're preparing to move our customers' sites to our new platform, which means scheduling upgrades and repointing DNS. To make it easier on everyone, we're building a platform upgrade dashboard that lists all of a customer's site upgrades by status. For each of the three different statuses, there is a section where the sites within those sections are listed alphabetically. I'm in charge of writing the query.

Here's an imaginary customer's sites:
```
{
    :id => 129,
    :name => "Shart Attack",
    :owner_id => 1
},
{
    :id => 234,
    :name => "Fart of Gold",
    :owner_id => 1
},
{
    :id => 245,
    :name => "Farty McFly",
    :owner_id => 1
},
{
    :id => 312,
    :name => "Fart Corner",
    :owner_id => 1
}
```
And here is a list of PlatformUpgrades::SiteUpgrade objects
```
{
    :id => 1,
    :site_id => 234,
    :status => "scheduled"
},
{
    :id => 2,
    :site_id => 129,
    :status => "unscheduled"
},
{
    :id => 3,
    :site_id => 245,
    :status => "upgraded"
},
{
    :id => 4,
    :site_id => 312,
    :status => "scheduled"
}
```

So I want to return the PlatformUpgrades::SiteUpgrade objects in the correct order based on their status _and_ site name. I ended up creating a new class to set up and run the query. 

I also got to use a bit of Arel directly for the first time. It's a library to help manage SQL for Ruby. In fact, it's the framework that ActiveRecord is built on.

You'll see I initialized the class with a user and scope. Currently this query is only being used in one place, so I set the default scope to _all_ PlatformUpgrades::SiteUpgrades. I also made a custom ordering method.


```ruby
module PlatformUpgrades
	# Gathers SiteUpgrades for a user and orders them correctly (unscheduled, scheduled, upgraded)
	#
	# Examples:
	#
	# 	PlatformUpgrades::SiteUpgradeQuery.new(user: user)
	#
	class OrderedSiteUpgradeQuery < Query
		# Public: Instantiates a new query.
		#
		# user - The user who owns the sites associated with the site upgrades.
        #        Include sites where they are collaborators or members
		# scope - The scope from which we base the query.
		def initialize(user:, scope: PlatformUpgrades::SiteUpgrade.all)
			@user = user
			@scope = scope
		end

        # Public: Runs a query
		#
		# Returns: An ActiveRecord::Relation 
		def find
			scope.joins(:site)
                 .where(sites: { id: user.all_sites.select(:id) })
                 .order(order_by_status)
                 .order(sites[:name].asc)
		end

		private

		attr_reader :user
		attr_reader :scope

		table_alias sites: Site, upgrades: PlatformUpgrades::SiteUpgrade

		def order_by_status
			Arel::Nodes::Case
				.new(upgrades[:status])
				.when("unscheduled").then(0)
				.when("scheduled").then(1)
				.else(2)
		end
	end
end
```
So now when I run `PlatformUpgrades::SiteUpgradeQuery.new(user: User.find(1)).find` I get my PlatformUpgrades:SiteUpgrade Objects back in the correct order:

```
{
    :id => 2,
    :site_id => 129,
    :status => "unscheduled"
},
{
    :id => 4,
    :site_id => 312,
    :status => "scheduled"
},
{
    :id => 1,
    :site_id => 234,
    :status => "scheduled"
},
{
    :id => 3,
    :site_id => 245,
    :status => "upgraded"
}
```