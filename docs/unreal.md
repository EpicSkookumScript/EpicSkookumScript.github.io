---
layout: page
section: unreal
title: SkookumScript Unreal Engine 4 Plugin
sidebar-page: none
sharing: false
footer: false
permalink: /unreal/

---

SkookumScript is a text-based programming language and tool suite for creating performance-critical, real-time gameplay. It is available as a free turn-key plugin for [Unreal Engine 4 (UE4)][UE4]. 

[![SkookumIDE running alongside UE4 Editor](/images/galleries/Screens-sm.png){:.pic-full}](/images/galleries/Screens.png)
The SkookumIDE while debugging running alongside the UE4 Editor. Click picture to enlarge.
{:.caption}

The SkookumScript Unreal Engine 4 Plugin integrates with the Unreal Engine, allowing you to jump right into developing your game. SkookumScript's addictively useful [Workbench command console](/docs/v3.0/ide/workbench/) turbocharges your workflow (at any stage of development) by enabling you to run code snippets to query and manipulate any UE4 project -- even projects not coded in SkookumScript -- as it runs on any desktop, console or mobile device.

<div markdown="1" class="note">

### Get it now!
See the [SkookumScript UE4 Plugin installation and setup instructions](/docs/ue4/setup/).
</div>


[![SkUE4 pic2](/images/Unreal/SkookumIDE2017-2.jpg){:.pic-full}](/images/Unreal/SkookumIDE2017-2.jpg)

The SkookumIDE in action. Click picture to enlarge.
{:.caption}

SkookumScript has key game concepts such as concurrency built in at the language level. It is fully integrated with Blueprints -- SkookumScript methods and coroutines can be placed as custom nodes in Blueprint graphs, and seamlessly integrated into your existing game logic. Unlike Blueprint nodes, the integrated SkookumScript code can be live-updated and modified while the game is running. Blueprints and Blueprint variables are automatically exposed to SkookumScript as classes and data members, where they can readily used. The C++ API makes it easy to call from SkookumScript into C++ or vice versa. SkookumScript is optimized to meet the performance demands of today's games, and it has a small memory footprint -- it even allows scripts to be [loaded and unloaded on demand][Sk demand] based on game progression and other factors.

The SkookumScript Integrated Development Environment (SkookumIDE) enables live code changes and remote debugging while connected to a running game on any platform, allowing near-instantaneous turnaround. SkookumScript scales painlessly and facilitates large-scale content creation. Its modular, data-driven design adds value to shipped games by facilitating downloadable and user-created content, modding, add-ons and patches.

[![SkUE4 pic3](/images/Unreal/SkookumIDE2017-3.jpg){:.pic-full}](/images/Unreal/SkookumIDE2017-3.jpg)

SkookumScript can easily call or be called by Blueprints and C++. Changes to SkookumScript commands are reflected immediately in Blueprint graphs and nodes, and the SkookumIDE Workbench console allows live interaction with Blueprints while your game is running. Click picture to enlarge.
{:.caption}

Mighty and feature-rich yet simple and easy to learn, SkookumScript transforms team composition by empowering the entire development team (including light coders such as mission, audio, and UI designers) to create compelling and sophisticated gameplay with just a few lines of code. SkookumScript streamlines the very thought processes of video game production, and is ideal for titles of any size, game type or genre.

[![SkUE4 pic4](/images/Unreal/SkookumIDE2017-4.jpg){:.pic-full}](/images/Unreal/SkookumIDE2017-4.jpg)

The SkookumScript UE4 Plugin uses the same C++ meta tagging mechanism as Blueprints to bind more than 8000 Unreal Engine commands -- whenever UE4 commands are added or changed, the Plugin automatically updates to reflect them. SkookumScript also has powerful game-specific constructs not found in traditional languages, such as native handling of concurrency. Click picture to enlarge.
{:.caption}

Battle-tested on major titles such as the open-world hits *[Sleeping Dogs]* (Windows, X360, PS3) and [*Sleeping Dogs: Definitive Edition*][SDDE] (Windows, Xbox One, PS4), SkookumScript is lovingly crafted by a [team of veteran game developers][Sk team] dedicated to filling your development experience with cackles of megalomaniacal glee.

[![SkUE4 pic5](/images/Unreal/SkookumIDE2017-6.jpg){:.pic-full}](/images/Unreal/SkookumIDE2017-6.jpg)

The SkookumIDE has a [powerful command-line interface][Sk cmd] that makes it easy to give scripting superpowers to other applications. Click picture to enlarge.
{:.caption}


## More info

- [SkookumScript UE4 Plugin installation and setup instructions](/docs/ue4/setup/)
- [SkookumScript blog: Unreal Engine posts][SkUE4 blog]
- Help or be helped by the growing SkookumScript community in the [Unreal Engine 4 category of the SkookumScript forum][SkUE4 forum]

<div markdown="1" class="note info">

### Using SkookumScript with other engines?
If you aren't using the Unreal Engine, fear not! The SkookumScript Unreal Engine 4 Plugin contains source code examples and C++ API libraries that you can use to connect SkookumScript to another engine. [Download it here](/docs/ue4/setup/).
</div>


[Sk cmd]: /docs/v3.0/ide/command-line/ "Give other applications scripting super powers"
[Sk demand]: /docs/v3.0/rt/demand-loading/ "Demand Script Loading"
[Sk IDE]: /docs/v3.0/ide/workbench/ "SkookumIDE documentation"
[Sk team]: /about/team/ "The SkookumScript Mad Scientist Team"
[SkUE4 blog]: /blog/categories/unreal/ "SkookumScript blog"
[SkUE4 docs]: /docs/integrations/ue4plugin/ "UE4 Integration in Documentation"
[SkUE4 forum]: https://skookum.chat/c/unreal4-plugin "UE4 Category in SkookumScript forum"
[SkUE4 pic2]: /images/Unreal/SkookumIDE2017-2.jpg "The SkookumIDE in action" 
[SkUE4 pic3]: /images/Unreal/SkookumIDE2017-3.jpg "SkookumScript can easily call or be called by Blueprints and C++" 
[SkUE4 pic4]: /images/Unreal/SkookumIDE2017-4.jpg "SkookumScript's UE4 Bindings" 
[SkUE4 pic5]: /images/Unreal/SkookumIDE2017-6.jpg "Give other applications scripting superpowers" 
[Sleeping Dogs]: /about/#sleeping-dogs "Sleeping Dogs - SkookumScript Showcase"
[SDDE]: https://www.youtube.com/watch?v=XvESN76BUe4 "Sleeping Dogs: Definitive Edition - Launch Trailer"
[Triad Wars]: http://www.unitedfrontgames.com/games/triad-wars/ "Triad Wars - massively multiplayer open-world action adventure"
[UE4]: https://www.unrealengine.com/en-US/ "Unreal Engine 4 Site"
