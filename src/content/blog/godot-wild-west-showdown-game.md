---
title: Godot Wild West Showdown Game
author: Michael Erb
description: Getting into Game development and created a basic game
date: 11-03-2026
draft: false
img:
  src: /src/imgs/postImgs/godot-showdown.png
  byName: ""
  byUrl: ""
  origSrc: ""
excerpt: This game is a test of your reaction time aganst another player. Both sit at the same keyboard and wait for the sign to say 'shoot!'. Then whoever kits their button first wins the round! But don't push the button too soon, your character will fumble for a time giving your opponent an opportuity to shoot you first. Has been a lot of fun making it and playing with the family.
category: godot
tags: [godot, game-dev, programming]
---

## Got my 2nd practice game out

Using Godot has been so much fun! GDScript is a lot like python, just some keyword differences. The documentation of Godot helps it a lot too. So much detailed information and links to related objects. Just very well done.

This game is a test of your reaction time aganst another player. Both sit at the same keyboard and wait for the sign to say 'shoot!'. Then whoever kits their button first wins the round! But don't push the button too soon, your character will fumble for a time giving your opponent an opportuity to shoot you first. Has been a lot of fun making it and playing with the family.

This one was a little more simple in terms of features than the WackaGodot game. But learned a lot about Godot's animation player and how powerful it is.

## Release - Try it out

Here is the relase files. I do not have a machine with windows so have only tested Mac and Linux. Though I did test the `.exe` build using Steam's `proton` tech that is a compatibility layer to run windows software/games on Linux. It worked perfectly using that.

github: <a href="https://github.com/M-erb/showdown-godot-game" target="_blank">github.com/M-erb/showdown-godot-game</a>

### MacOS

Due to it not being signed you may need to disable the quarantine after unziping it in the same folder it is in. Otherwise you may get a message like "app may be broken".

```bash
sudo xattr -dr com.apple.quarantine 'Showdown.app'
```

**Download:** <a href="https://assets.merb.dev/showdown/mac/Showdown.zip" class="btn __sm" download>Showdown.app</a>

### Linux

**Download:** <a href="https://assets.merb.dev/showdown/linux/Showdown.zip" class="btn __sm" download>Showdown.x86_64</a>

### Windows

Again the app is not signed but I did not look up how to get around it on windows. I did test using `proton`, Steam's compatibility tech, on Linux and it worked great.

**Download:** <a href="https://assets.merb.dev/showdown/windows/Showdown.zip" class="btn __sm" download>Showdown.exe</a>
