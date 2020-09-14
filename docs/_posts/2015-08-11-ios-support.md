---
layout: post
title: "Apple iOS (iPhones and iPads) + tvOS (Apple TV) now supported!"
sidebar-page: none
author: <a href="/about/team/#markus-breyer">Markus Breyer</a>
categories: Runtime Unreal Engines

---

![Sk iOS](/images/blog/Sk-iOS.jpg){:.pic-full}

Use SkookumScript to develop for all your iDevices.
{:.caption}

SkookumScript now supports the Apple iOS platform so you can create iPhone, iPad and iPod Touch games and applications using SkookumScript.

You can use the SkookumScript Integrated Development Environment (IDE) to [run code snippets][SkWorkbench], make code changes, and perform sophisticated remote debugging -- all live while remotely connected to a running iOS game.

If you have been frustrated with the long turn-around time to make even the smallest modifications during mobile development, we are sure that making live changes -- without needing to stop the game, modify, recompile, transfer the binary to your device, get to the progression point that you want to test, etc. -- will be a refreshing improvement that will transform your workflow.

<div class='embed-container'>
  <iframe src="//player.vimeo.com/video/133828708" frameborder='0' webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>
</div>

56 seconds into this teaser video you can see examples of SkookumScript and the Unreal Engine running on an iPad showing off its iOS support.
{:.caption}

__2015-09-10: SkookumScript now also supports Apple TV (tvOS)__{: .hdr}<br>
With yesterday's Apple event announcing the arrival of the new [![AppleTV](/images/blog/AppleTV.png){:.pull-right height6em}][Apple TV] we thought it would be cool to ensure that the SkookumScript runtime can be built and run on this new platform. We are happy to say that the latest version of SkookumScript can now target Apple TV / [tvOS](https://developer.apple.com/tvos/)!<br/>
<br/>
Until Apple TV development kits are available, we can only do a compilation rather than a full test -- but the conversion was pretty simple and should run without any issues.<br/>
<br/>
So that means that the SkookumScript runtime can currently target: Microsoft Windows / Xbox One / Xbox 360, Sony PlayStation 3 / 4, Apple iOS / tvOS. Additional platforms will be added in the future and should be easy to support.<br/>
<br/>
Note that SkookumScript still requires a game engine (such as Unreal Engine 4) that can also target Apple TV -- and SkookumScript will be ready.
{: .note .soon}

__Extra Info on the UE4 Plug-in__{: .hdr}<br>
[![SkookumScript + Unreal](/images/Unreal/SkookumAndUnreal_trans.png){:.pull-right height6em} ][SkUE4]
For additional information on the SkookumScript Unreal Engine plug-in see the [SkookumScript + UE4 landing page][SkUE4].<br/>
<br/>
If you would like to hear about the latest happenings with SkookumScript, sign up for the [SkookumScript forum][forum].
<br class="clear-all"/>
{: .note .info}


[Apple TV]: http://www.apple.com/tv/ "Apple TV"
[SkWorkbench]: /docs/v3.0/ide/workbench/ "IDE Workbenches - Read-Eval-Print Loop (REPL)"
[signup]: /download/ "Instructions to download and setup SkookumScript"
[forum]: https://skookum.chat/ "SkookumScript forum"
[SkUE4]: /unreal/ "SkookumScript Unreal Engine 4 plugin landing page"
