---
layout: post
title: Welcome to OneHash
---

#{{ page.title }}

OneHash allows you to stream audio and video directly from a torrent swarm.

Take torrent information of any variety (torrent file, magnet link, info hash) and just put it after #, and the site will start to download the content, and let you watch or listen in your browser. 

Take the DJ Shadow BitTorrent bundle for example (definitely worth a listen). This is the url to the torrent file:

<a href="http://featuredcontent.utorrent.com/torrents/DJShadow-BitTorrent-b.torrent">http://featuredcontent.utorrent.com/torrents/DJShadow-BitTorrent-b.torrent</a>

To listen using OneHash, just append the torrent information after #:

<a href="http://onehash.com#http://featuredcontent.utorrent.com/torrents/DJShadow-BitTorrent-b.torrent">http://onehash.com#<span style="font-weight:bold;">http://featuredcontent.utorrent.com/torrents/DJShadow-BitTorrent-b.torrent</span></a>

<img width="100%" src="../../../images/onehash.png" />

You can of course enjoy the same torrent content using just the info hash:

<a href="http://onehash.com#DFD0A2D3D2AD601388900A344507BA368D56ACE2">http://onehash.com#<span style="font-weight:bold;">DFD0A2D3D2AD601388900A344507BA368D56ACE2</span></a>

There are still some kinks to be worked out, as we're still fine tuning Torque's streaming capabilities, and HTML5 video/audio support remains ever in flux, but its easy to see the potential here.


What happens when we get this stuff working as well as other streaming services? Will Louis C.K. become [the rule](https://buy.louisck.net/purchase/live-at-the-beacon-theater), instead of the exception? If you can stream from torrent swarms, there won't even be the hosting/bandwidth costs that C.K. had to deal with. 

Maybe we'll know sooner than later. Like every other [Torque app](http://torque.bittorrent.com) that we've written, we've made it [open source](https://github.com/bittorrenttorque/onehash.com) for other programmers to improve and use to their liking. And for the folks that are curious about the torrenting that's happening under the hood, you can expand the torrent section to inspect the usual info, open the folder on disk or delete the torrent if you're done with it. There's an ongoing conversion about torrent persistance when using torque apps, so hopefully this will provide greater insight for our users.

I'd love to know what you think, and if you're a programmer hoping to get started, feed free to drop me a line. I'm happy to help.

<a href="https://twitter.com/intent/user?screen_name=pwmckenna">@pwmckenna</a>