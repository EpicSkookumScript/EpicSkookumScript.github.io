---
layout: post
title: "SkookumScript UE4 Plugin updated on Unreal Engine Marketplace"
sidebar-page: none
categories: Unreal

---

The SkookumScript UE4 Plugin was updated to version 3.0.3078 on the Unreal Engine Marketplace today. If you haven’t installed any version of the plugin yet, by Jove, now is the perfect time! <a href="https://www.unrealengine.com/marketplace/skookumscript">Download it here.</a> If you have a previous version installed, <a href="https://skookum.chat/t/3-0-3078-now-up-on-the-marketplace-with-a-caveat-though-please-read/874">read this post on the SkookumScript Forum</a> for important cleanup instructions. Enjoy!

![](/images/blog/2016-04-26_UE4LogoBlackBackground.jpg){:.pic-full}


<strong>Thrilling new features</strong>

Since the SkookumScript Unreal Engine 4 Plugin’s April launch on the Unreal  Engine Marketplace, the mad computer scientists of the SkookumScript team have been working around the clock (not to mention on top of and even inside the clock) to make a stupefyingly vast range of improvements. In less than four months, we have taken the plugin all the way from version 3.0.2470 to version 3.0.3078—that’s 608 separate versions, folks. And now, an exhaustive (not to mention completely exhausting) list of all 608 improvements!

Just kidding. Here’s a quick rundown of the niftiest features that have been added to the plugin since its Marketplace debut:

- the number of engine modules we support out-of-the-box has leaped from 2 to 37! This includes UMG (in game UI), AIModule, MoviePlayer, and many more!

- hot reload of a game module now also recompiles, reloads and rebinds the SkookumScript class hierarchy

- UE4Editor standalone mode supported

- multiplayer mode now supported by allowing multiple game worlds

- C++ projects are now supported by the engine version of the SkookumScript plugin, so you can get the full power of SkookumScript without needing to move the plugin to your project folder. This is accomplished via a new major refactor of the plugin and its generated binding system

- the `SkookumScriptComponent` has been replaced with three types of components: the `SkookumScriptClassDataComponent`, `SkookumScriptMindComponent`, and coolest of all, the `SkookumScriptBehaviorComponent`, which allows you attach awesome SkookumScript behavior to any actor

- `!new` constructor to `Entity` allows entities (`UObjects`) to be created on the fly

- `Debug.print_memory_execution()` prints runtime memory usage to the console

<strong>Meanwhile, on GitHub: support for Unreal Engine 4.13 Preview 2</strong>

We now support Unreal Engine 4.13 Preview 2, so all of you bleeding edge users are covered! Get the 4.13 compatible SkookumScript UE4 Plugin from our <a href="https://github.com/EpicSkookumScript/SkookumScript-Plugin">GitHub repository</a> or as a good old <a href="https://skookum.chat/t/downloads-latest-plugin-and-demos/419">precompiled zip file</a> for Epic Games Launcher (<a href="https://skookum.chat/t/installing-and-updating-the-skookumscript-plugin-for-unreal-engine-4/153">installation instructions</a>).
