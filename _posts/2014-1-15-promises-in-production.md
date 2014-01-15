---
layout: post
title: Production Promise Exception Handling
---

#{{ page.title }}

I use [Q](https://npmjs.org/package/q) everywhere. Here's a few things that I wish I had known before using promises at work in a production environment (nodejs). 

## Don't call anything until you're in a promise chain.
Start everything with `q.resolve()`.  

This way exceptions thrown by the first function will be treated as rejected promises, rather than uncaught errors that will blow your server up. __Instead of starting your promise chain by calling a function, start with a resolved promise__ so every function in your chain is treated like a promise callback (converting values into resolved promises, converting thrown exceptions into rejected ones), and most importantly, propegating __every__ exception to your fail handlers.

{% highlight javascript %}
q.resolve().then(firstFunction).then(secondFunction);
// you better be pretty confident firstFunction
// cannot throw an exception to write the following
//
// if you're working on a team, you'll just have to hope no one
// does something as well intentioned as adding parameter validation
// to that function...
firstFunction().then(secondFunction);
{% endhighlight %}

#### Pleasant Side-Effect

Because promises convert returned values into promises resolved with that value, and convert thrown exceptions into promises rejected with that error, you gain some flexibility by ensuring that every function will be treated like a promise callback. For instance, the following poorly written function could never start your promise chain, but does just fine as a callback:

{% highlight javascript %}
var divideByTwo = function (a) {
    if (typeof a !== 'Number') {
        throw new Error('NaN');
    }
    if (!a) {
        return NaN;
    }

    return q.resolve(a / 2)
};
{% endhighlight %}

There is all kinds of return value nonsense in there. But if you started with `q.resolve`, no problem!

## Trailing exception handler
`.then(onSuccess).fail(onError)` not `.then(onSuccess, onError)`  

Same issue as above, but on the tail end (and instead of blowing your server up, they'll silently disappear).

Exceptions thrown by `onSuccess` will not be handled by the `onError` handler of the same promise. If your `onSuccess` handler could possibly throw an exception, you need to have another `.fail` handler outside of it to deal with those.

__Example__: If you're dealing with http requests, your success handler might check the result object for the status code, and assert that it is 200. You'll need a trailing `.fail` handler for that. The fail handler for the request itself will only be called if the server is not reached.

## Accidentally swallowing exceptions

Its always tempting to introduce `.fail` handlers throughout your code to get a better idea of specifically where things are going wrong. I'm constantly writing functions that have fail handlers to get better visibility into where errors are coming from. __But its important that your logging doesn't inadvertantly result in a resolved promise like below.__

{% highlight javascript %}
var doTasks = function () {
    return q.resolve().then(function () {
        return func1();
    }).then(function () {
        return func2();
    }).then(function () {
        return func3();
    }).fail(function (err) {
        console.warn(err);
    });
};
{% endhighlight %}

That `.fail` hander doesn't re-throw the error, and doesn't return a promise, so the implicit `return;` is treated like a resolved promise. So `doTask` swallows all of its own errors. Make sure your teammates and your future self don't mind being blindsided by errors if you add code like this.

## Intentionally throwing exceptions

`.done` vs `.then`

Using `.done`, rather than `.then` means that if there's a rejected promise that is never handled via a promise failure handler, the promise chain will throw the exception. This means that you'll never silently swallow exceptions (good!), but it also means that there's an exception floating around, likely either crashing your process or leaving it in an unstable state (bad!).

__If you are using `.done`, make sure you're intentionally ["failing fast"](http://servantofchaos.com/2008/11/the-fail-first.html)__. If you're using `.done` so you never silently swallow exceptions, try the approachs above instead!

## Thoughts?

Know of improvements, or a better way altogether? Have you run into your own issues with promises? Let me know!

<a href="https://twitter.com/pwmckenna" class="twitter-follow-button" data-show-count="false">Follow @pwmckenna</a>
<script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0];if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src="//platform.twitter.com/widgets.js";fjs.parentNode.insertBefore(js,fjs);}}(document,"script","twitter-wjs");</script>