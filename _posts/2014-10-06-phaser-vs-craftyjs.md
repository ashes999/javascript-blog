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

## CraftyJS Wins

I picked CraftyJS, for one major reason: architecture. CraftyJS was built from the ground-up to use an entity-component system. In Phaser, this is impossible (currently with Phaser 2.1).

What does this mean? Practically, CraftyJS entities are just:

- Component bags
- Events that trigger (inter-component processing)
- A mix of pre-made and custom components

Phaser, on the other hand, requires you to pass around a global `game` variable, and classes tend to be singleton and/or monolithic. Not cool for bigger and more complex games.

My conclusion? CraftyJS for now.
