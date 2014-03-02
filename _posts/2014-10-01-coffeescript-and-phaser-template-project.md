---
layout: post
title: "CoffeeScript and Phaser.io Template Project"
description: ""
category: 
tags: []
---
{% include JB/setup %}

I believe strongly in template projects. Any project should be encapsulated into an easy, one-click deployment that you can reuse. Complex configuration should be minimized; this way, you have a DRY way to setup new projects, while including all the lessons learned from past projects.

I love [CoffeeScript](http://coffeescript.org). One common problem I see with HTML frameworks like [Crafty](http://craftyjs.com) and [Phaser](http://phaser.io) is a lack of information about whether these frameworks work with CoffeeScript. (Obviously, they do, because CoffeeScript compiles one-to-one to Javascript.)

Accordingly, below is the Hello World project for Phaser, in CoffeeScript.

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
