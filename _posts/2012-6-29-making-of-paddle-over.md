---
layout: post
title: The Making of PaddleOver
---

#{{ page.title }}

For a bit of background, see [Building Torque](../../../2012/06/29/building-torque.html)...

__Torque__

An important tidbit about the Torque api that led to building [PaddleOver](http://paddleover.com), is the fact that you can use the [btapp.js](http://github.com/bittorrenttorque/btapp) Backbone library to connect to your local machine...or any other machine in the world. For instance, if you give me access, I can open a web page and play with files on your computer the exact same way that I could on my own computer. For the developer, it makes no difference.

__Engineer + Beer + Btapp.js__

Originally I wanted to write a file distribution management tool that would allow software companies to distribute files to their servers [the same way that Facebook does.](http://torrentfreak.com/facebook-uses-bittorrent-and-they-love-it-100625/) I was also getting pretty obsessed with [Bret Victor's]() work at the time, and thought that I'd take a swing at building an interface that had a singular goal of being easy to use. All it was suppose to do was allow any of the involved parties to move files from one computer to another.

After taking advantage of the keg here at BitTorrent for a bit one night, I started trolling around domain registrars and scored the awesome domain [http://beamitover.com](). I was starting to envision a site simple enough to be used on a touch screen, with the asthetic of early Star Trek control panels. As this site was going to be showing off our api to other software devs, a sci-fi theme seem appropriate.

__But then we built it.__ And it was so fun and easy to use. And I realized that it might be the first thing I've ever built that my mom might enjoy using. I couldn't miss this opportunity.

The redesign started with a gorgeous background by [James Gately](http://www.istockphoto.com/user_view.php?id=2715153). From there it was simply a matter of adding in a few easter eggs, sliding in some [Robv](https://twitter.com/intent/user?screen_name=thisisrobv) approved wood panelling and calling it a day. The site is quite simple both in terms of the UI and whats happening under the hood. My hope is that there's a javascript dev out there that is inspired enough to take a peek at [btapp.js](http://github.com/bittorrenttorque/btapp) and build something themselves.

And I'll tell you what. Build something awesome and I'll just give you [http://beamitover.com](). It deserves a good home.