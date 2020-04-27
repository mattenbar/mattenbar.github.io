---
layout: post
title:      "CLI Project - Quarantine Live Streams"
date:       2020-04-27 11:00:51 -0400
permalink:  cli_project_-_quarantine_live_streams
---


It's day 7,562 (really only 43 but feels like 7,562) of quarantine and today feels a little brighter and more optimistic. No quarantine isn't over and no we cant go back to normal life but today i finished my first Ruby program that i made entirely from scratch.

![](https://i.chzbgr.com/full/2590969088/hF77B983F/i-can-see-the-light)

**ABOUT THE PROJECT:**

Before all the quarantine madness my profession (and luckily for me my passion)  has been photographing music concerts and events. While no events are going on there has been an interesting rise in a new trend of live stream performances from artists. As a music lover this excited me. At a hard time in everyones lives these musicians are selflessly streaming FREE and LIVE performances from their homes that we would normally have to pay hundreds of dollars for.

So where does my project come in? No its not as fancy as hosting live streams but it can help you find them! My program scrapes the internet to return to you upcoming live streams that you can look forward to. in just a few simple steps you can get information like, date, time, genre, and a link to view those performances.

**Getting Started**

Probably the most daunting part of this (and any project) is where do to begin and immediately feeling lost staring at a blank page.

![](https://miro.medium.com/max/1400/1*6vFBPhHBK_vva5nOoGEwcw.png)

Prior to now everything we have been programing has been bit size chunks that are easily digestible. Creating a dish from scratch can be difficult but if you know the ingredients (methods, classes, objects etc...) its a simple as following a recipe.

For my projects the ingrdients were simple enough (or so i thought).

Ingredients: 
  - CLI class that will be the face of out program and what the user will interact with
  - Scraper class, a class that will implement Nokogiri to scrape a website and get us all the information we need
  - Event class, that will take everything from our scraper and create objects.


**Building out my Project**

After realizing the my program is not some giant illusive thing i started to tackle 1 class at a time.

Scraper class:
   the scraper class implements nokogiri to scrape (read through the website code) a website (in my case i used NPR) to return  JSON node-sets that we can then use to find information. To explain better it gives you a magnet so you can find that needle in the haystack
	 
![](https://static1.squarespace.com/static/58261c4020099e94eacfcb0b/58348de54402438234b94ec4/5d8b7312c0a64117821c27ac/1569506079215/haymagnet1500w.jpg?format=1500w)

	 
Now that i have all the needles i need it's time to get sewing. I took that information and created hashes with information for each event and stored them neatly and nicely in an array
	 
	 
Event class:
    Once we have all our information the Event class takes the array and creates instances of of the event class. each instance is now its own living thing. It knows its name, its genre, the date , the time etc...
		
![](https://stevetobak.com/wp-content/uploads/2018/12/its-alive.jpg)
		
Cli class:
    Now that everything is done and we have these objects its time to create how the user interacts with the program. The CLI is responsible for presenting the user with choice asking them what they want and then returning to them what they asked for.
		For example: When it starts up it asks the user if they would like to see a list of all events, all genres or all the dates available. If someone were to select dates or genres it would return a list of either one and then the user could pick Rock as a genre if they wanted. Once they have selected their genres they receive a list of live streams (event objects) that they can choose from to get more information on.
		
**GIVE IT A TRY**

Here you will be able to find my project. I hope you enjoy [https://github.com/mattenbar/QLS](https://github.com/mattenbar/QLS)

