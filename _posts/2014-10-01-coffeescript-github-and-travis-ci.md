---
layout: post
title: "CoffeeScript, GitHub, and Travis CI"
description: ""
category: 
tags: []
---
{% include JB/setup %}

It's quite simple to setup Travis CI to build your CoffeeScript game into Javascript binaries, despite Travis-CI not natively supporting CoffeeScript (see their language-setup pages).

## Step 1: .travis.yml

Add this configuration file to your repository:

{% highlight yaml %}
language: node_js
node_js:
  - 0.8
before_script:
  coffee --compile -o lib src
before_install:
  - npm install coffee-script
{% endhighlight %}

Explanation:

- You're using `node_js` to build your CoffeeScript code. v0.8.
- `before_install` installs the CoffeeScript command line for you to use in your build.
- `before_script` builds the actual Javascript (into `lib` from `src`)

## Step 2: package.json

You also need to add a separate dependency list in `package.json`, like so:

{% highlight json %}

{
  "devDependencies": {
    "coffee-script": "latest"
  }
}

{% endhighlight %}

## Step 3: Done

Configure your project as usual in Travis-CI, and you're done.

I still haven't figured out how to extract the built binaries, though. It would be nice to auto-publish them to a `gh-pages` branch on GitHub for a continuous, daily/nightly build of my CoffeeScript game.
