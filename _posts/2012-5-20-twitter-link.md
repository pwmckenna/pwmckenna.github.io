---
layout: post
title: Twitter Link
---

#{{ page.title }}

Hosting my blog on github means I don't think twice about loading in js dependencies to do something awesome. I can just do it! 

Why link to twitter when you can use their handsome [Web Intents?](https://dev.twitter.com/docs/intents)

<img height="300px" src="../../../images/intent.png" />

Just include this javascript file  

{% highlight javascript %}
<script type="text/javascript" src="//platform.twitter.com/widgets.js"></script>
{% endhighlight %}

Then place these where ever you'd like to link from  

{% highlight javascript %}
<a href="https://twitter.com/intent/user?screen_name=pwmckenna">@pwmckenna</a>
{% endhighlight %}

results in <a href="https://twitter.com/intent/user?screen_name=pwmckenna">@pwmckenna</a>