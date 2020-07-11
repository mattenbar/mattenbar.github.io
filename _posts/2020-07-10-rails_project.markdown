---
layout: post
title:      "Rails Project"
date:       2020-07-11 00:20:28 +0000
permalink:  rails_project
---


For my rails project i decided to build off my sinatra project and continue with Live Streams. While doing the project what struck me as particularly interesting was the major differences between Rails and Sinatra. 

Personally i enjoyed Sinatra a bit better. While Rails is fantastic, all the "magic" behind it i feel can be a double edge sword. Sinatra on the other hand can be a bit more clunky and tedius because of the lack of helper methods and macros (comparitavely). 

A big difference to me would start off with how routes work in each. In Sinatra while tedius because you have to write out each individual route (which also makes your code base a larger) everything is clearly defined right there in the controller and the logic that occompanies that route is define underneat. With Rails however our routes are now located in the 'config/routes.rb' file. With that change though we then still have to use our controller to create methods and put our logic into. Personally i believe not having to jump back and forth between files is easier.

Differnece and preferances aside working on this project i did feel i was able to acomplish a lot. I tackled the project first by starting off with users, events, and genres. Users had many events, events belong to users ,events have genres. My next step was too allow users to comment on events. I acoomplished this by making comments a join table with events and users. Comments then had an attribute of content that users were able to write.

The last bit of my code i added was a model for artists that followed the same relationship as genres.

Finally i added a search functionality that was able to search through events, genres, and artists and provide links for each where you could see related info to whichever you select

