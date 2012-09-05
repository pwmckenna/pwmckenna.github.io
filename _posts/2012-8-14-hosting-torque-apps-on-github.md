---
layout: post
title: Hosting Torque Apps on GitHub For Fun (and Profit?)
---

#{{ page.title }}

__TL;DR:__ Go to [https://github.com/bittorrenttorque/onehash.com](https://github.com/bittorrenttorque/onehash.com) and hit the Fork button. In minutes, the entire site will be publicly hosted via your [github pages](https://help.github.com/articles/what-are-github-pages) at [http://YOURGITHUBUSERNAME.github.com/onehash.com](http://YOURGITHUBUSERNAME.github.com/onehash.com).  
__WARNING:__ Either delete the CNAME file or delete its contents. GitHub pages hosting will fail if it thinks two repos are serving the same domain.
<p style="margin:0px;font-size:10px;font-variant:small-caps;">* I've forked the onehash.com repo into my personal account and it is now hosted at <a href="http://pwmckenna.github.com/onehash.com">http://pwmckenna.github.com/onehash.com</a></p>
<p style="margin:0px;font-size:10px;font-variant:small-caps;">* This works for most <a href="https://github.com/bittorrenttorque">https://github.com/bittorrenttorque</a> repositories. Try <a href="https://github.com/bittorrenttorque/paddleover.com">https://github.com/bittorrenttorque/paddleover.com</a></p>
<br>
-----------------
<br>
__A__ll of our [Torque Demo Apps](https://torque.bittorrent.com) are built using [btapp.js](https://github.com/bittorrenttorque/btapp), and while they communicate with a background torrent client via http interface, there is no traditional backend server to any of the apps. They're just a collection of static Javascript/HTML/CSS. Because all of the files that we're serving are static, we can take advantage of [github's gh-pages branch](http://pages.github.com/), to publicly serve our web apps directly from the repositories that we do develop in. 

__For instance:__ [http://onehash.com](http://onehash.com) points to [http://bittorrenttorque.github.com/onehash.com](http://bittorrenttorque.github.com/onehash.com), which is always up-to-date because we do developement in the *gh-pages* branch rather than *master*.

So that's it! We've built these apps largely as examples, but we encourage you to take them wholesale if you feel you can give them an audience. Each of the apps are covered under the MIT software license, so don't worry about any limitations or obligations. That being said, I do love an appreciative <a href="https://twitter.com/intent/user?screen_name=pwmckenna">tweet</a> :)


 If you think this is swell/stupid/confusing, or you're a programmer hoping to get started with btapp.js, feel free to drop me a line. I'm happy to help.  

<a href="https://twitter.com/pwmckenna" class="twitter-follow-button" data-show-count="false">Follow @pwmckenna</a>
<script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0];if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src="//platform.twitter.com/widgets.js";fjs.parentNode.insertBefore(js,fjs);}}(document,"script","twitter-wjs");</script>