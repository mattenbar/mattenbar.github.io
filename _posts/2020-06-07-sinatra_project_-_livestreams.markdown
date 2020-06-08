---
layout: post
title:      "Sinatra Project - LiveStreams"
date:       2020-06-08 00:59:19 +0000
permalink:  sinatra_project_-_livestreams
---


For my sinatra project i decided to expand on my CLI project and take it from a gem to what is essentially a Content Management System (CMS) .

Since I was building off my last project I was able to take my scraper from my gem and implement to use for seed data in my new project. In order for my scraper to work i needed to build out the same Event class. Active Record made this simple and with just one migration I created a table with the same attributes as my Event class from my gem.

Once my seed data and events were ready it was time to start out building the controllers. The first controller I made was the Application Controller which all other controllers inheritted from. Inside i enabled sessions for users and created some helper methods to check if a user is logged in and one to return who the current user is. After i created a Session controller to allow users to sign up as well as log in.

Now that users were able to log in my next controller was the Events Controller. This is where the main logic and get requests come from. The event controller housed the routes for creating, edited deleating and viewing all the events.

I was able to implement a lot of features in this project like editing events and even favoriting events so you could keep track of events you like. Like with anything there could always be more features. If i were to continue to build this out some features i would like to implement would be a search feature so i could see all event of a specific genre
