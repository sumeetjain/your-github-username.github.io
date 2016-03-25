---
title: Introducing Brian Poole and the Tremeloes
---

On New Year's Day, 1962, a band called The Tremeloes auditioned in London for a recording contract with Decca Records. The Tremeloes had a following in England as dance-hall favorites that loved American rock-and-roll and played a lot of Buddy Holly covers. The audition was something of a formality. Decca signed the Tremeloes, with the proviso that they change their name to Brian Poole and the Tremeloes, to follow the syntax of Buddy Holly and the Crickets. 

Another up-and-coming band, also influenced by Buddy Holly, auditioned at Decca that day. They performed 15 songs, but did not get a recording contract. That band was The Beatles. 

As we roar into the last third of our Omaha Code School experience, we are excited about our current team projects. At the same time, we have one eye on the next step, the job search. We will be the up-and-comers, auditioning for jobs. And if you look at the potential and not just the resume, we might be The Beatles.

Our group projects tell interesting stories about capability and somebody's belief in us. One group is developing an online archive of any information available about vinyl recordings by Nebraska artists, from the actual music to album covers and liner notes.  One group is tackling creation of a resource for employers and other interested parties to provide self-paced learning. My own group is developing an online nomination and voting process for the Theater Arts Guild (TAG) Awards. 

Code School ends in 3.5 weeks, so there is no wasted time right now. We need to immediately apply Ruby on Rails, even as we learn it, to the current projects. And depending on the project, we may need to call on the CSS (Cascading Style Sheets) we learned last week, HTML learned the week before, and Javascript learned the week before that, to get these projects done. Beyond the languages, we need to be bands, not individual musicians. There's no other way to get 15 songs ready for an audition in this amount of time. 

CSS may have been my favorite thing all semester. Not because it makes sense, because in plenty of ways it is a winged camel on ice skates. I like it because I can see it immediately. You change the color of something, you go out to your local server, and voila. You may hate it and change it back immediately, but at least you know. 

CSS is how we "pretty up" websites with positioning, color, borders and other properties that we assign to the elements on the site. There's nothing especially intuitive about the process, which makes seeing it as you go all the more important. By way of example, let me try to describe positioning. There are four properties for positioning an element using CSS: static, relative, absolute and fixed. Three of those (static, absolute and fixed) sound as though they describe the same thing, but they don't. Once an element has been assigned one of these properties, you can position it using top-bottom-left-right properties. Except of course for static elements, which are oblivious to top-bottom-left-right. More on that soon.

Let's get at this with a small visual aid: The Tournament of Roses Parade. You are a spectator at the Tournament of Roses Parade, in your bleacher seat on Colorado Boulevard, a block or so from Orange Grove Boulevard. 

Static Position

Let's say nobody is really organizing the parade order. The bands, people on horseback, the floats, the cars full of dignitaries and so on just got in line in whatever order in which they showed up at the starting point. Nobody is going to reposition them, and in CSS terms, top-bottom-left-right properties mean nothing to them. There would still be a Rose Parade, just kind of an unimpressive one.

Relative Position

Now let's say somebody did decide to organize the parade order. They had a bullhorn and started barking out orders, like "You, you members of The Best Damned Band in the Land, I need you all to move about 30 feet up Orange Grove from where you are now. If somebody is already standing there make a friend. I will get to them pretty soon." (Aside: "The Best Damned Band in the Land" is the self-applied moniker for the Ohio State University marching band.) In CSS terms, the band is now in "relative" position. It is relative to where it was in the static position, and a set of left-right-top-bottom instructions has been applied to it. In CSS code:

.the best damned band in the land {
  position: relative;
  top: 30 feet;
}

Absolute Position

The parade organizers have also hired a substantial event staff. One staff member, let us call her Matilda, has been assigned to walk 10 feet to the left of the City of Burbank float and talk loudly into a headset if the float has to stop, is careening out of control, is being approached by an ice cream truck the driver of which was oblivious to the event, or other disturbances. From your position, you will see Matilda enter your field of vision and eventually leave it, like anything else in the parade. In CSS terms, Matilda is in absolute position. Code in the html file has identified the City of Burbank float as a "parent" of Matilda. Her "absolute" position has been assigned as 10 feet left of her nearest positioned ancestor, in this case, the float. If for some reason the City of Burbank float did not show up for the parade, Matilda would move up the ancestral ladder, and as a last resort, could end up 10 feet to the left of the Chairperson of the Tournament of Roses Parade.

.event staffer Matilda {
  position: absolute
  left: 10 feet
} 

Fixed Position

And now let's say a member of the Pasadena police force has been stationed on the edge of the street at the corner of Orange Grove and Colorado. You can see them, and you know why they are there, so no big deal. That member of Pasadena's Finest is in "fixed" position. They are in your view, but they don't move with the parade. In CSS terms, an element in "fixed" position is "fixed" to a particular location in your browser window. A lot of navigation bars and similar elements are in fixed position. You recognize them in your browser window because they don't move when you scroll.

Accounts differ, but The Beatles may have been undone by poor positioning. The Tremeloes were local for London-based Decca. Signing The Beatles, based on the opposite coast of England in Liverpool, would mean higher travel expenses.  

It's not the first time a business has "played it safe" and missed a game-changing opportunity. William Orton of Western Union famously informed Alexander Graham Bell that his invention, the telephone, was an interesting novelty but had no practical value. M&M Mars passed on a product placement in a movie about an alien and some kids, and the makers of Reese's Pieces reaped the benefits of taking that placement in "E.T.: Extra Terrestrial." A total of 15 publishers passed on a new author named Joanne Rowling and her story about a boy wizard named Harry Potter. 

In the home stretch of OCS, I am reminded that in the first entry in this blog, I said I would tell the truth. The truth is that every classmate I have on this adventure is really smart, likes to master and apply new information, will be "up to speed" in an evolving business in a hurry, and will be an asset to whoever employs them. Not saying any of us are going to be the JK Rowling, or Alexander Graham Bell, or The Beatles of web development. But we might be. There's only one way for an employer to find out. 

 






