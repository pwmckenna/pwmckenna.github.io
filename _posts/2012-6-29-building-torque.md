---
layout: post
title: Building Torque
---

#{{ page.title }}

TLDR:  
We're building web apps with [btapp.js](http://github.com/bittorrenttorque/btapp)  
Our other stuff is here: [http://github.com/bittorrenttorque]()

Six months ago, Kyle and I created a new team with the goal of building an api on top of our existing client that would make it simple for web developers to interact with our torrent clients. At the time, I was working on the team that develops uTorrent, and Kyle was a one man army in charge of our Remote feature. And while we wanted to utilize our existing client, the ultimate goal was for web devs to simply load in our Backbone library and write code that assumed that the client was installed, running, and ready for action. And while we're far from done, we have a library that I enjoy building my own apps on top of.

In those six months, we built out the Torque executable, the plugin that lets you assume that everything is ready to go, and a Backbone.js library that gives you access in two lines of code. 

		var btapp = new Btapp;
		btapp.connect();

At the same time we were all being "Inspired" by [Marty Cagan](https://twitter.com/cagan), and even though we're not building a consumer product, we made user testing a priority. We've held a meetup (thank you SFJS!), supported the release of a product built on top of our api, and helped other BitTorrent devs with smaller projects for our 2 day coding paloozas. I would highly recommend all of those things for those building out an api, as it really is impossible to see all the sharp edges without fresh eyes. 

I think what we have now is a pretty powerful tool for anyone that wants to move files around the web. All we needed was a way to show it off...

Well hello there [PaddleOver](../../../2012/06/29/making-of-paddle-over.html)...

