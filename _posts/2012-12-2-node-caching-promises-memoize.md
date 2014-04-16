---
layout: post
title: Node Http Request Caching Using Promises + Memoize
---

#{{ page.title }}

I've been playing around with promises recently, and while they've been amazing for helping organize asynchronous code in general, I've only just now discovered my favorite use.

__Cache external resource requests, and easily handle duplicate in-flight requests.__

Here's how:

If you need to request an external resource (such as an image) to satisfy a request to your server, simply make the function that you make the request in return a promise object. Then memoize that function (using ```_.memoize``` for instance). You get the benefits of using memoize for caching, but you also treat everything as a promise, so if the second request occurs before the first resolves and is cached, you still are safe. In that case, both requests will simply be returned the same deferred object, and they'll be resolved at the same time.

An example of this can be seen in my project [image_resize](https://github.com/pwmckenna/image_resize), which takes a image href, and returns a scaled version. There are opportunities for caching both at the remote resource requests, but also after the resizing itself. Both functions return deferred objects and are memoized, so we don't need to think very hard to dramatically improve performance.

For example, here's the function that requests the images.

{% highlight javascript %}
// memoizing here works as a cache...but its even better than that.
// when you call for the second time with the same url, it doesn't
// matter if the first request has resolved or not. Both requests will
// get the same promise object, which will be resolved at the same time.
// so no timing issues to worry about...
// the caching is of the promise object, so dups of the results aren't
// stored in memory, and the storage of the objects themselves is in some
// tidy underscore closure

var request = require('request');
var q = require('q');
var assert = require('assert');

var requestImage = _.memoize(function(url) {
    var defer = q.defer();
    request({
        encoding: 'binary', // binary encoding means the body is a Buffer object
        uri: url
    }, defer.makeNodeResolver());
    return defer.promise.spread(function (res, body) {
        assert(result.staticCode === 200);
        return res;
    });
});
{% endhighlight %}

This is just a simple usage of deferred objects, as they're only being used as callback aggregators. Got any uses that you want to share?

<a href="https://twitter.com/pwmckenna" class="twitter-follow-button" data-show-count="false">Follow @pwmckenna</a>
<script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0];if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src="//platform.twitter.com/widgets.js";fjs.parentNode.insertBefore(js,fjs);}}(document,"script","twitter-wjs");</script>