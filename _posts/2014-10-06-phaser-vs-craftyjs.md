---
layout: post
title: "Phaser.io vs. CraftyJS"
description: ""
category: 
tags: []
---
{% include JB/setup %}

How do you choose between Phaser.io and CraftyJS? I decided to draft up some comparative points. (NB: I used CraftyJS for about five months, and Phaser.io for about a week.)

## Points of Commonality

Both contain several similar points:

- Natively create JS games that work in your browser
- Sprites (including alpha/rotation/scale) 
- Spritesheets (animation)
- Audio (OGG and MP3)
- Collision Detection (AABB and more)
- Text support
- Canvas and WebGL
- A way to manage screens/scenes/states
- Actively developed

## Architecture

CraftyJS, wins in one major area: architecture. CraftyJS was built from the ground-up to use an entity-component system. In Phaser, this is impossible (currently with Phaser 2.1).

What does this mean? Practically, CraftyJS entities are just:

- Component bags
- Events that trigger (inter-component processing)
- A mix of pre-made and custom components

Phaser, on the other hand, requires you to pass around a global `game` variable, and classes tend to be singleton and/or monolithic. Not cool for bigger and more complex games.

## Stability

If you look at the [commit history for Phaser](https://github.com/photonstorm/phaser/graphs/commit-activity) and the [commit history for Crafty](https://github.com/craftyjs/Crafty/graphs/commit-activity), as of 2014, there's a huge difference. Phaser averages something like 40+ commits a week, while Crafty is currently in a lull (averaging 5-10 commits per week).

Numbers don't indicate quality necessarily, but it's hard to ignore such a huge difference.

## In Conclusion

Which one should you use? I honestly don't know. CraftyJS seems more modular (because of the entity system). But is it dead? Perhaps it just needs another change of leadership.

I suggest trying both to see which one you like more.
