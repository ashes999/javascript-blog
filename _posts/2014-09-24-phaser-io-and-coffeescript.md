---
layout: post
title: "Cross-Platform HTML5 Games with Phaser.io and CoffeeScript"
description: ""
category: 
tags: []
---
{% include JB/setup %}

I recently proved that [Phaser.io](http://phaser.io) and [CoffeeScript](http://coffeescript.org) can co-exist to create awesome HTML5 games in Javascript.

This blog post contains some caveats and other information gleaned along the way through trial-and-pratice.

## The Goal: JS on Android, iOS, and Windows

My goal was to find a Javascript-based language that allowed me to build Android, iOS, and Windows games from a single code-base.

Why Javascript? Actually, I intended to try out CoffeeScript instead. It's like Ruby syntax that transpiles into Javascript. Why not TypeScript? Because I prefer a Ruby-like syntax, and CoffeeScript brings that to the table.

Phaser.io seemed an ideal choice, because their home page claims: `if it doesn't perform well on mobile then we don't add it into the core.`

## First: Hello World in CoffeeScript

The default "Hello World" phaser.io project is pretty simple; it just displays an image on-screen. Actually, it utilizes two event handlers in the app life-cycle (create and preload), and relies on their state mechanism.

The final Coffee Script code:

{% highlight coffeescript %}
class State
  constructor: () ->
  
  preload: () ->    
    game.load.image('logo', 'assets/graphics/phaser.png')

  create: () ->
      logo = game.add.sprite(game.world.centerX, game.world.centerY, 'logo')
      logo.anchor.setTo(0.5, 0.5)

window.onload = () ->  
  @game = new Phaser.Game(800, 600, Phaser.AUTO, '', new State)
  
{% endhighlight %}

This almost faithfully reproduced the current "hello world" phaser project, in Coffee Script.

## Android and iOS

I need my game to run on Android and iOS. After searching through several solutions, I ended up using [PhoneGap's cloud build](http://build.phonegap.com).

### What About CocoonJS?

CocoonJS provides a similar, unlimited-use, upload-and-compile model; non-premium users get ~2 minutes delay before any compilation starts, and can only upload apps up to 30MB.  CocoonJS provides online compiling, and they email you the built binaries.

I only tested their Android APK, but it worked quite well. (Scaling to display didn't work.) Unfortunately, for a small (100kb) app, the resulting APK weighed in at *almost 20MB*. Definitely not the way to go for mobile.

PhoneGap also has a confusing build system (launcher or no launcher? Which to build, when, why?), and for some reason, builds fail frequently (the only recourse is to open a support ticket).

I couldn't test iOS, due to lack of familiarity with the device.

Overall, not an experience I would care to repeat.

### PhoneGap: One-Step Process

In contrast, PhoneGap provided a one-step process: upload a zip, click build, and in a few seconds (usually around 20-30 seconds) I can click links to download the APK of my game. And the XAP (for Windows phone). 

iOS builds require a signing key, so I declined to try this.

Also in contrast to PhoneGap, the final APK weighs in around 400KB. That's a pretty small amount of overhead.

## Windows Executables

Windows users are still a huge market-share of gamers (just ask Steam). I need my game to run on Windows, too.

As it turns out, CocoonJS also provides a "Chromium" bundled app, but it didn't work -- I got back the same zip file that I uploaded.

Instead, I turned to [Web2Executable](https://github.com/jyapayne/Web2Executable), a node-kit wrapper around phaser.io. Although nodekit clocks in at around 60MB, I successfully created a self-contained EXE file (with a couple of DLLs) for my game.

One caveat I ran into is that Chrome, by default, renders the `body` HTML tag with an 8px margin. I removed this via inline css.

## Concluding Thoughts

Phaser.io + CocoonJS + Web2Executable provide a theoretical case for a common Javascript code-base and four major platforms (web, Android, iOS, and Windows). I feel the downsides don't really justify the stack (long compile times with an online compilation model, 60MB for hello world in desktop, and 20MB on Android).

On the flip side, Phaser.io + PhoneGap provide an excellent, fast, lightweight process to build Javascript games for web and mobile. I will continue to experiment with phaser.io for web or mobile development.
