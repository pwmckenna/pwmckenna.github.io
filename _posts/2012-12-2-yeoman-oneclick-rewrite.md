---
layout: post
title: Rewriting OneClick Chrome extension using Yeoman
---

#{{ page.title }}

Its been >6 months since I build and released OneClick, and in that time Google has changed (http://developer.chrome.com/extensions/manifestVersion.html#manifest-v1-changes)[the requirements for installing extensions]. They've also had a team busy building (Yeoman)[http://yeoman.io] which looks like a great development/scaffolding tool. They have a generator for chrome apps, and I know there's a grunt plugin for building crx files, and I want to use all these things!

So I'm going to blog while I do the rewrite using these tools. Here it goes.

__(Sun 4:52 PM)__


<a href="https://twitter.com/pwmckenna" class="twitter-follow-button" data-show-count="false">Follow @pwmckenna</a>
<script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0];if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src="//platform.twitter.com/widgets.js";fjs.parentNode.insertBefore(js,fjs);}}(document,"script","twitter-wjs");</script>Find