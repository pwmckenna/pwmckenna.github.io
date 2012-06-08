---
layout: post
title: Working with vertical backbone.js data structures
---

#{{ page.title }}

Backbone.js seems to generally be used to represent database tables on the client side. Collections can contain Models, but anything deeper is a bit unwieldy. Imagine you have a Model, to which you set an attribute with a Collection as the value. That Collection contains Models, which each also have Collection attributes and so on and so forth. The goodness of the add/remove event binding starts to break down a bit.

Along comes [Backbrace.js](https://backbrace.github.com/pwmckenna/).

Backbone enables jQuery-esque *live* calls to detect adds of Models or Collections regardless of how deep in the tree they are, regardless of whether any intermediate level exists yet.

For example:
@@@
var model = new Backbone.Model;
var callback = function(val) {
  console.log('I only care about d in c in b in a...nothing in between');
};
model.live('a b c d', callback);

model.set('a', new Backbone.Model);
model.get('a').set('b' new Backbone.Model);
model.get('a').get('b').set('c', new Backbone.Model);
model.get('a').get('b').get('c').set('d', new Backbone.Model);

//Your callback was just called!
@@@

Currently the main limitation is that the callbacks only get the leaf value, while the entire series (especially in the cases of wildcards) would be useful. Coming soon...