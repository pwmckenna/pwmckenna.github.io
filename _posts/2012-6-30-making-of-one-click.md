---
layout: post
title: The Making of OneClick
---

#{{ page.title }}

OneClick is more an idea than a particular project, and has existed in a couple forms here at BitTorrent over the last six months or so. And the idea is this:

__Users already are accustomed to the download path of their browser. Instead of training them on a whole new way of downloading files, we should find a way to fit into their existing flow. In other words, torrent downloads should take the same number of clicks as a normal download. One.__

During a BitTorrent Palooza (2 day hackathons) several months ago, I talked Art Yerkes and Kyle into joining me with the goal of building out the first version of OneClick. It was going to leverage some pretty powerful [LSP](http://en.wikipedia.org/wiki/Layered_Service_Provider) code that Art had written previously to catch all socket connections on your machine, and silently divert all your torrent downloads to your invisible Torque client, which would then pump the torrent contents into the listening end of your socket. Art and Kyle flexed some pretty powerful networking fu for two days while I acted as glorified cheerleader, and in the end we had a functional demo that won us the competition. 

The thrill of victory wasn't able to mask a few glaring limitations however. With the palooza over, we needed to justify it as a product, and the combination of being Windows only and quite invasive was too much to overcome. So OneClick was shelved. 

Time passed. Kyle and I continued to build out the [btapp.js](http://github.com/bittorrenttorque/btapp) library that sits on top of our Torque plugin/client, in preparation for the release of our public api. Then late afternoon some Friday, I stumbled upon the Chrome Extension [webRequest](http://code.google.com/chrome/extensions/webRequest.html) api that gives you access to all the http headers for requests in Chrome. Which meant that not only could I filter for .torrent file requests, but I could go one step farther and just wait for a server to serve up a file with the *application/x-bittorrent* mime type before springing into action.  I immediately slowed my ascent up Balmers peek, declined the co-worker invite to Zeitgeist (apparently it was quite the evening), and dove in. 

Writting Chome extensions is actually fairly simple. Despite my failure to deliver on the foolishly bold claim I made to Art, saying that I'd have OneClick rewritten as a extension before he left for the day, it really wasn't too much work. Their [getting started page](http://code.google.com/chrome/extensions/getstarted.html) is really precise, and their documentation and examples are really thorough, especially for [webRequests](http://code.google.com/chrome/extensions/webRequest.html).

Like every other app, I started with the following [btapp.js](http://github.com/bittorrenttorque/btapp) code:
{% highlight javascript %}
	var btapp = new Btapp;
	btapp.connect();
{% endhighlight %}

Then when someone was served back the torrent mime type, I'd grab the url and load the torrent into the Torque client like so:
{% highlight javascript %}
	btapp.get('add').torrent(url);
{% endhighlight %}

There are a couple ways that the downloads could have been handled due to torrents potentially representing many files. In the end, I just opened tabs pointing to the urls for the specific files being served by the Torque client, and forced a *Content-Dispostion* header to ensure they were immediately converted to file downloads.

Creating a tab for each file in the torrent looked a little bit like the following:
{% highlight javascript %}
	torrent.get('file').each(function(file) {
		var url = file.get('properties').get('streaming_url');
		chrome.tabs.create({
	        url: url,
	        selected: false
	    });
	});
{% endhighlight %}