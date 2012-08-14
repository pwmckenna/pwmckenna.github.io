---
layout: post
title: Hosting Torque Apps on GitHub For Fun (and Profit?)
---

#{{ page.title }}

__TL;DR:__ Go to [https://github.com/bittorrenttorque/onehash.com](https://github.com/bittorrenttorque/onehash.com) and hit the Fork button. In minutes, the entire site will be publicly hosted via your [github pages](http://github.com) at [https://USERNAME.github.com/onehash.com](https://USERNAME.github.com/onehash.com) (replace *USERNAME* with your github username)  
<span style="font-size:8pt">\*I've forked the onehash.com repo into my personal account and it is now hosted at [https://pwmckenna.github.com/onehash.com](https://pwmckenna.github.com/onehash.com)\*</span>

All of our [Torque Demo Apps](https://torque.bittorrent.com) are built using [btapp.js](https://github.com/bittorrenttorque/btapp), and while they communicate with a background torrent client via http interface, there is no traditional backend server to any of the apps. They're just a collection of static javascript/html/css. Because all the files that we're serving are static, we can take advantage of GitHub's gh-pages branch, to publicly serve our web apps directly from the repositories that we do developement in. 

For instance: [http://onehash.com](http://onehash.com) is actually just pointing to [http://bittorrenttorque.github.com/onehash.com](http://bittorrenttorque.github.com/onehash.com)


 If you think this is swell/stupid/confusing, or you're a programmer hoping to get started with btapp.js, feel free to drop me a line. I'm happy to help.  
<a href="https://twitter.com/intent/user?screen_name=pwmckenna">@pwmckenna</a>