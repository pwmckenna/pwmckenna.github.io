---
layout: post
title: Automatically `yeoman build` into gh-pages using travis-ci
draft: true
---

#{{ page.title }}

##Goal:
This blog is is written in Jekyll. Github automatically builds the site when I commit, and what you are reading is the built version. I want that for normal web apps, but I want to use yeoman. The end result being, every time I commit to the master branch, I want the `yeoman build` output to land in my gh-pages branch. In this case, I'm using travis-ci.org to do the building, and I want to use a yeoman generator to do the setup for me, so that getting auto build/deploy working on new projects is as simple as:

```
yeoman init travis-ci:gh-pages
```



<a href="https://twitter.com/pwmckenna" class="twitter-follow-button" data-show-count="false">Follow @pwmckenna</a>
<script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0];if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src="//platform.twitter.com/widgets.js";fjs.parentNode.insertBefore(js,fjs);}}(document,"script","twitter-wjs");</script>
