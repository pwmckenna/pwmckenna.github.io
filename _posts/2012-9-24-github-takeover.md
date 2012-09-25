---
layout: post
title: GitHub Page Takeover Post Mortem
---

#{{ page.title }}

<img src='../../../images/gh-pages.png' style="width:400px;"></img>

Look familiar? At around 11 pm on September 4th I saw this visiting [http://coffeescript.com](http://coffeescript.com) and knew I could take over the domain. Here's how, and what you can do to protect your domain.


There are a variety of cases where this appearing is perfectly fine. For instance, you'll see it at [http://pwmckenna.github.com/idontexist.html](http://pwmckenna.github.com/idontexist), which makes sense because there I don't have a repository called <i>idontexist</i> with a index.html file in the <a href="http://pages.github.com"><i>gh-pages</i></a> branch.

Where this is a problem is when you see this on a custom (non-github) domain. It means that they've configured their dns to point to the github pages servers (in this case, <a href="https://help.github.com/articles/my-custom-domain-isn-t-working">an A record pointing to 204.232.175.78</a>). And unfortunately this means its up for grabs, first come, first serve.

To serve the custom domain from your repository, you simply need to have a file called <i>CNAME</i> in the root directory, which contains the domain you wish to serve. ie: 

<a href="https://raw.github.com/pwmckenna/coffeescript.com/master/CNAME"><i>CNAME</i></a>  
```
coffeescript.com
```

There's currently no way for GitHub to verify that the creator of the <i>CNAME</i> file is the administrator of the domain, so its possible for anyone to create one. In fact, if you do this before the administrator creates their <i>CNAME</i> file, your page will continue to be served, rather than the owners! 

__What should I do?__

I created [a repo with a <i>gh-pages</i> branch](https://github.com/pwmckenna/coffeescript.com/tree/gh-pages), and commited the CNAME file above, as well as an <i>index.html</i> that simply redirected to <a href="http://coffeescript.org">coffeescript.org</a>. I waited a few minutes, still not quite believing it would work. But then a refresh directed me to coffeescript.org!

__Then I got scared.__

I admire Jeremy Ashkenas as much as the next guy, and I was of course only trying to help. But then again, so was <a href="http://arstechnica.com/business/2012/03/hacker-commandeers-github-to-prove-vuln-in-ruby/">Egor Homakov</a>. I shot off emails to GitHub and Jermey, and headed to irc to sound the alarm, but no one was awake, so I headed to bed very worried about being discovered. 

__All is well that ends well__

Turns out that Jeremy was appreciative, and Shawn Davenport over at GitHub was very responsive. Its a tough problem to solve, and it is still possible to fall into the same trap, but Shawn updated the [gh-pages custom domain page](https://help.github.com/articles/setting-up-a-custom-domain-with-pages) to include the following warning:

*Good to know: create this file and wait for the notification from GitHub that your Page was built successfully before making DNS changes in the next step.*

The A record has since been updated to redirect to coffeescript.org via dns, but it was kind of exciting to have such a popular domain at my fingers. Be careful, or your domain might be next!

__Lesson!__

Set up your github repo first, with a CNAME file in your gh-pages repository. Make sure there's only a single entry, otherwise your page might build successfully without actually serving the additional domains. If you don't receive a notification saying that it built successfully, DO NOT SET UP YOUR DNS. It is possible to squat on domains via private (impossible for you to find) repos, so go ahead and assume if you can't build its because I have a repo with your name on it :)

