---
title: Riding the Lone Tree Ferry
---

The Bob Kerry Pedestrian Bridge arches across the Missouri River at a point just 1.8 miles from Omaha Code School. It's walking distance on a nice day. 

The total bridge project, including both landings, measures 3,000 feet. The walking deck is 15 feet wide, with a 4.5-foot-tall railing on each side. 

It is a cable-stayed bridge. Two tower-like pylons rise 210 feet in the air. The base of each pylon is buried 80 feet into the bedrock below. Cables leading from the pylons support the walking deck. 

At the bridge's highest point, in the center, people stand about 60 feet above the Missouri River, which is 25 feet deep, give or take a flood like the one in 2011, which closed the entrance on the Iowa side. 

From the center of the bridge, a MacBook Air (13.3 inch screen, 2.96 pounds) dropped over the railing after a brief ceremony would hit water in 1.93 seconds. 

I have not gone so far as to take my MacBook Air to the bridge, but obviously I had the thought. Less frequently than in weeks 1-6 of OCS, but occasionally still. As I inch down the miles-long Path of the Coder, more knowledge equals less frustration. But it is my understanding that temporary failure and frustration will never go away. It is part of the career.

It is also possible that the MacBook Air, not quite sentient today but wait until the 2018 models come out, is thinking the same thing about me. I, after all, am the one making the mistakes. 

3-28-2016 Keep Staring at the Screen and the Answer Will Come to You

Week 9 merges its many feature branches into week 10, and I am working on front-end for a group project to produce an online nomination and voting system for the Theater Arts Guild (TAG) Awards. At the moment of this writing, I have scrapped the very hip dropdown menus I was working on, which hide the dropdown elements under normal conditions and expose them when you hover over the dropdown heading. I scrapped them after some consultation with Sumeet because of the minor detail that they don't work. I have switched to dropdowns using the more familiar but uglier <select> html tag which, at the moment, are also not working. I'm pretty sure I will end up scrapping that plan also, and end up with a link farm that looks like the Yahoo home page did in 2001.

I mention this current failure because, in keeping with the promise made and remade throughout this blog, it's an effort to tell the truth. I also mention this because of the utterly irrational degree to which it matters to me. I can't guarantee that I can explain it, and I'm a good 'splainer. I have written for a living for a long time. And I see the big picture. I understand the insignificance of my problem, measured against wars and discoveries and starvation and peacemaking and ever-more-creepy viruses and undiluted kindness and exploding airports and brilliant art and everything else in the world that I have been holding at arm's-length for the duration of Code School. But damnit, I want the links in my dropdown menu to take me where I want to go. I want it enough to contemplate a ceremony ending in the water burial of a MacBook Air at the Bob Kerrey Pedestrian Bridge, near the former landing site of the Lone Tree Ferry.  

The Lone Tree Ferry, supposedly named for the single tree that defined the Nebraska side landing point, opened for business in 1850. Eventually renamed the Council Bluffs and Nebraska Ferry Company by founder William D. Brown, it connected Council Bluffs, Iowa, and Omaha, Nebraska. It was an inelegant but functional solution to the problem of crossing the river. It got people where they wanted to go. My current task is to make my page as functional as well as the Lone Tree Ferry. My future task is to make my page as attractive as the Bob Kerrey Pe--er, well, make my page more attractive than it is now. 

The Bob Kerrey Pedestrian Bridge is the longest pedestrian bridge in the United States that connects two states. It cost $22,000,000 to build, with $18 million of that coming from a federal budget earmark procured by then-Senator Bob Kerrey. Since its opening, approximately 150 miles of bike trails on both sides of the river have been extended to connect to the bridge, and the Gallup organization has built Gallup University nearby. The bridge may be a boondoggle, but it's an attractive boondoggle that seems to be working, which is more than I can say for my code.

3-28-2016 Code Red

There are lots of ways to fix my dropdowns, apparently. A Google search reveals several, and several others who say Solution A will not work, you need Solution B. TA Wendy has Googled and sent me three, one of which involves some Javascript. Her suggestion is that I do all three and write a blog entry comparing them. She's right, it would be a good entry, but first I would have to execute not one, but three, ways to fix my dropdowns. TA Wendy is a fabulous asset of Omaha Code School, as is TA Steven. They share the after-hours (5p.m. to 8p.m.) shift at OCS, helping those of us who don't seem to ever complete the work and exit at 5 with Sumeet. It's like knowing the 9-1-1 operator. 

In the long run, the best solution to my problem has come from a teammate, who suggested I just get rid of the damned dropdowns and live with the links for now. I did that. It's still ugly as sin, but it functions. Take the small victories.

I have learned lots of ways not to do front-end web development in the past week. I have also been reminded how smart and capable my classmates are. I hope they can worry less about employment and enjoy the last few weeks of Code School, because if I was in position to do so, I would hire them in a heartbeat.

3-30-2016 Update: All It Needs is a Little Pixel Dust

Life is a Disney movie, and birds are teaching themselves to sing my name. Links hibernating in uncomfortable dropdowns now function, and can be styled with css. More to the point, I talked through the real goal with Sumeet, which was to have the links easily available to the person who is trying to use the massive nomination ballot for the TAG Awards. (There is room to make 180 nominations, not counting "special award" nominations, on this ballot.) I wanted to fix the position of the links so they would always be at the top of the page, available to the user. Unfortunately the fixed position, which is outside of the general page flow (see last week's exciting entry for more details on fixed position elements) meant the box 'o links moved right into the heading and covered up the client's logo. Fortunately, Sumeet has helped me with some new javascript that has fixed the fix. 

My page now sports an Event Listener, listening for "Scroll," specifically for 93 pixels worth of scrolling. The page header, sartorially resplendent with TAG logo, is 93 pixels in height. Not enough to damage a falling MacBook Air, but enough to damage the user experience on a page. So now, thanks to the Event Listener, the link information moves with the scrolling pageflow for 93 pixels, then, after the heading has scrolled out of view, the list of links is fixed in place in the upper left of the page, always available to the person filling out the ballot. With the links, the user can bring any nomination category to the top of their view, instead of having to scroll all the way to Kansas to nominate a Lighting Tech for a job well done. 

In the big scheme of things, zzzzzzzzzz. For me, another small victory.  

At the peak of the Bob Kerrey Pedestrian Bridge, on the north side, is an Emergency Help Phone. Press the button and connect to 9-1-1. Just having it there might be enough to remind the wayward soul that help is available and people can be on the way if you want it. And if you are on that bridge, whatever you do, don't consider a drop down.  




