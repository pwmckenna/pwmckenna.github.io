---
layout: post
title: Hosting Torque Apps on GitHub For Fun (and Profit?)
---

#{{ page.title }}

__TL;DR:__ Go to [https://github.com/bittorrenttorque/onehash.com](https://github.com/bittorrenttorque/onehash.com) and hit the Fork button. In minutes, the entire site will be publicly hosted via your [github pages](http://github.com) at [https://USERNAME.github.com/onehash.com](https://USERNAME.github.com/onehash.com) (replace *USERNAME* with your github username)  
* I've forked the onehash.com repo into my personal account and it is now hosted at [https://pwmckenna.github.com/onehash.com](https://pwmckenna.github.com/onehash.com)  
* This works for most [https://github.com/bittorrenttorque](https://github.com/bittorrenttorque) repositories. Try [https://github.com/bittorrenttorque/paddleover.com](https://github.com/bittorrenttorque/paddleover.com)  

All of our [Torque Demo Apps](https://torque.bittorrent.com) are built using [btapp.js](https://github.com/bittorrenttorque/btapp), and while they communicate with a background torrent client via http interface, there is no traditional backend server to any of the apps. They're just a collection of static javascript/html/css. Because all the files that we're serving are static, we can take advantage of [github's gh-pages branch](http://pages.github.com/), to publicly serve our web apps directly from the repositories that we do developement in. 

For instance: [http://onehash.com](http://onehash.com) is actually just pointing to [http://bittorrenttorque.github.com/onehash.com](http://bittorrenttorque.github.com/onehash.com), which is always up to date because we do developement in the *gh-pages* branch rather than *master*.

So thats it! We've built these apps largely as examples, but we encourage you to take them wholesale if you feel you can give them an audience. The apps are each covered under the [MIT software license], so don't worry about any limitations or obligations. That being said, I do love an appreciative <a href="https://twitter.com/intent/user?screen_name=pwmckenna">tweet</a> :)


 If you think this is swell/stupid/confusing, or you're a programmer hoping to get started with btapp.js, feel free to drop me a line. I'm happy to help.  
<a href="https://twitter.com/intent/user?screen_name=pwmckenna">@pwmckenna</a>