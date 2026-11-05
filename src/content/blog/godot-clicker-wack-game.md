---
title: Godot Clicker Wack a Mole Game
author: Michael Erb
description: Getting into Game development and created a basic game
date: 10-14-2026
draft: false
img:
  src: /src/imgs/postImgs/godot-bg.webp
  byName: ""
  byUrl: ""
  origSrc: ""
excerpt: Diam nginx maecenas uUpellentesque diam volutpat commodo sed egestas. Nisi est sit amet facilisis magna etiam tempor orci. Habitant morbi tristique senectus et netus et. Sed augue lacus viverra vitae congue eu consequat ac. Egestas purus viverra accumsan in nisl. Risus pretium quam vulputate dignissim suspendisse in est ante. Turpis egestas pretium aenean pharetra magna ac.
category: godot
tags: [godot, game-dev, programming]
---

## Decided to dip my toes in game development

This has been something I have wanted to do since I was young. Probably not something unquie to me, especially those that work in the information technology industry. None the less, I finally set aside some time to dive into it. Just like when I started learning programming and web development almost 10 years ago, I feel like a noob. Hosestly though, it has been a breath of fresh air dispite being overwhelmed with all of the new information.

The first step to diving into something like this is choosing what are called a `game engine`. I am, by no means, an expert in this area but I would define a game engine as this. A `Game Engine` is a tool that gives you the basic elements that most games have to kick start creating a game. There are several popular ones but some have risen to the top such as `Unreal Engine`, and `Unity`. Both amazing and professional tools that many have created successful projects with. I decided to go a different route though. I landed on <a href="https://godotengine.org/" target="_blank">`Godot`</a>, mostly because I am a sucker for a good open source project. It has been such a joy working with and their specialized `GDScript`, which is very python like.

## Created a basic clicker game

I was able to fit a few features in this:

- Custom background music using <a href="https://www.beepbox.co" target="_blank">Beepbox.co</a>
- Changing scenes
- Simple UI menus
- Leaderboard that saves to `json` file

This was so much fun to make! My family has been having a blast trying to beat eachother as well with the leaderboard to keep track of scores.

## Release - Try it out

Here is the relase files. I do not have a machine with windows so have only tested Mac and Linux.

github: <a href="https://github.com/M-erb/godot-clicker-game" target="_blank">github.com/M-erb/godot-clicker-game</a>

### MacOS

Due to it not being signed you may need to disable the quarantine after unziping it in the same folder it is in.

```bash
sudo xattr -dr com.apple.quarantine 'WackaGodot.app'
```

<a href="/assets/wackagodot/mac/WackaGodot.app.zip" download>WackaGodot.app</a>

### Linux

<a href="/assets/wackagodot/linux/wackaGodot.x86_64.zip" download>wackaGodot.x86_64</a>

### Windows

<a href="/assets/wackagodot/windows/WackaGodot.exe.zip" download>WackaGodot.exe</a>
