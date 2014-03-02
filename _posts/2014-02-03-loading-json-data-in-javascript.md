---
layout: post
title: "Loading JSON Data in Javascript"
description: ""
category: 
tags: []
---
{% include JB/setup %}

Applications and games use tons of data. In an HTML5 world, you would probably store your data in JSON, and then read it back. Easy, right?

Not so fast! Between [same origin policy](http://en.wikipedia.org/wiki/Same_origin_policy) restrictions and browser security, you probably can't do this as easy as you think -- especially if you're locally debugging your application. If you've ever seen the dreaded `Cross origin requests are only supported for HTTP` error, you know what I mean.

What's more, is that `jQuery`, `minified.js`, and other libraries use the same solution: `XmlHttpRequest` objects. It doesn't work.

**The solution:** simply wrap your JSON in a variable, like so:

{% highlight javascript %}

var main_map = {
  title: "The World",
  tiles: [0, 1, 0, 0]
}

{% endhighlight %}

Save this in a javascript file like `data/maps/world.js` and nclude them like any other javascript file. Variable-name collisions aside, this provides an excellent, simple solution.

If you wanted to avoid the variable-name collision, you could wrap it in a function:

{% highlight javascript %}

function mainMap() {
  var data = {
    title: "The World",
    tiles: [0, 1, 0, 0]
  }

  return data;
}

{% endhighlight %}
