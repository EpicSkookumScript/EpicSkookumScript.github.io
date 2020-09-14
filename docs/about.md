---
layout: page
section: about
title: What is it?
footer: false

---

![Epic Games](/images/epic-games-logo-white-sm.png){:.right-margin .height4em} SkookumScript is owned by Epic Games and [maintained by the SkookumScript community][forum]. Its full source is [available][setup] and it has the same [license as Epic's Unreal Engine 4][license].
{:.focus}

## SkookumScript is a game programming language

SkookumScript is an embedded programming language and tool suite dedicated to the creation of gameplay in video games. With key game concepts built directly into the language, SkookumScript enables video game developers to quickly and easily convert their ideas into awe-inspiring interactivity, level design and AI. SkookumScript is the scripting solution for every genre of video game, on every platform, everywhere.

[![SkookumIDE during debugging](/images/galleries/SkIDE-callout.jpg){:.pic-full}](/images/galleries/SkookumIDE_Pro.png)

The SkookumIDE during debugging. [Click on image to see higher resolution with no text callouts.]
{:.caption}

SkookumScript is the [culmination of over two decades](/about/origin/) of problem-solving in the game industry trenches. Simple yet powerful, SkookumScript is a revelation to experienced programmers, yet readily accessible to those with no programming experience. SkookumScript is a powerful language designed to deliver the performance demanded by professional game development.

SkookumScript is an embedded language that generally (though not not necessarily) binds to a game engine written in a C++ host language. SkookumScript itself is written in a combination of C++ and SkookumScript.

SkookumScript gives people the power to unleash their creativity directly. Unlike the general-purpose languages commonly used to create games (such as C++, C# and Objective-C) and even non-game-specific scripting languages (such as Lua), SkookumScript allows people to focus on *what* they want to occur in a game, rather than spend most of their time describing to the computer *how* to do it. SkookumScript can turn anyone on a development team into a gameplay master.

<div markdown="1" class="note info">

### Why create a domain-specific language for video games?
Domain-specific languages are available for many different fields, including webpage layout, databases, geography, and graphics. In spite of being decades old and now a US$100+ billion industry, video games still don't have a specialized, gameplay-centric language—traditionally, gameplay components are written from scratch in a general-purpose language for each game, and are not designed to be reused. SkookumScript fills the “gap” of a reusable gameplay authoring tool, which will save video game developers substantial time and money.
</div>

With its focus on clarity of idea expression and rapid turn-around time, SkookumScript keeps developers "in flow" while being as unobtrusive as possible. SkookumScript's logical time-flow feature is truly unique -- language-level concurrency is a game-changer (in every sense) for authoring interactive content. Additional stand-out features of SkookumScript include built-in game concepts, sophisticated integrated development environment (IDE) and visual debugger, intensely useful script console, dynamic compile-time checking with live updating, game-optimized speed and memory, secure "sandboxing" around gameplay commands, and [much more](/about/features/). SkookumScript adapts in countless ways to a project’s setup—world editors, pipeline tools, processes, automation, smoke-tests and other libraries or tech can be plugged in as desired.

## Using SkookumScript

SkookumScript can be used to develop any type of game and is compatible with all PC, console and mobile game systems. The SkookumScript Integrated Development Environment (SkookumIDE) connects to the game on its target platform and can interact with the game remotely—you can run commands, make changes and debug live as the game is running. Its dynamic and versatile visual tools scale to any team or project size, from tiny indie projects to massive studio productions—such as the award-winning open-world hits <em><a href="http://www.sleepingdogs.net/">Sleeping Dogs</a></em> and <em>Sleeping Dogs: Definitive Edition</em>.

<div markdown="1" class="popround pad1">

### SkookumScript showcase: _Sleeping Dogs_
{:#sleeping-dogs}
![Sleeping Dogs - Logo](/images/SleepingDogsPortrait.jpg){:.right-margin}

<em><a href="http://www.sleepingdogs.net/">Sleeping Dogs</a></em> is an open-world game developed by Vancouver-based <a href="https://en.wikipedia.org/wiki/United_Front_Games">United Front Games</a>.<br>
<br>
The project took four years—plus an additional two years developing downloadable content (DLC)—with a 160-person team at its height. SkookumScript was its backbone, with approximately 20 level designers and scripters using SkookumScript as their primary development tool to create the game's missions. The second-most-intensive group of users were the audio designers and composers, who used SkookumScript to add interactivity to the music and audio.<br>
<br>
![Sleeping Dogs - Temple](/images/about/SleepingDogs-sm1.jpg){:.left-margin}
Everyone on the team used SkookumScript daily to some degree: to jump to progression points in the game, to enable or disable various settings, to test game scenarios, and to run SkookumScript-authored automated smoke-tests for every check-in. Team members were constantly swapping useful SkookumScript code snippets to make each other's lives easier.<br>
<br>
![Sleeping Dogs - Street](/images/about/SleepingDogs-sm7.jpg){:.right-margin}
<em>Sleeping Dogs</em> was published in August 2012 by <a href="http://www.square-enix.com/">Square Enix</a> on Microsoft Windows (online via Steam), Microsoft Xbox 360, Sony PlayStation 3 and Cloud OnLive. Through Fall 2014 it was frequently refreshed with new missions and other DLC created with SkookumScript, which became part of the hit follow-up title <em>Sleeping Dogs: Definitive Edition</em> (2014) on Microsoft Xbox One and Sony PlayStation 4.<br>
<br>
The <em>Sleeping Dogs</em> team had a great experience using SkookumScript.
</div>

## A sweet tool suite: components

SkookumScript is an "embedded scripting language" that works together with other common "low-level" game languages such as C++. SkookumScript is used for gameplay and other interactive logic, while the low-level languages in the game engine render graphics, crunch numbers for physics, and apply audio effects. It is easy to hook up SkookumScript to the game engine so the engine can call SkookumScript or vice versa. Don't let the "Script" part of "SkookumScript" give you any performance worries—SkookumScript is compiled (not interpreted) and is lightning-fast during compilation and while running the game.  

SkookumScript is a pure object-oriented language (like [Smalltalk][]), though it is very easy to type simple-yet-powerful commands without ever needing to create a typical "class" infrastructure. It uses compile-time type-checking, and the types are inferred so you usually don't have to specify them.

SkookumScript's main components include:

  - __Language__ -- the language itself (grammar, syntax, semantics, <em>etc</em>.) for the text-based code written in SkookumScript;
  - __Libraries__ -- the commands and classes written in the language. This is generally split into the core (standard) SkookumScript library, a company-wide (cross-project) library, and libraries specific to a project. Libraries can take as long or longer to learn than the language itself—*Sleeping Dogs* had something like 8000 library commands and 1700 classes!
  - __Compiler__ -- makes an optimized form of the code for the computer to read, and checks for any errors in the code;
  - __Runtime__ -- the C++ library that is embedded as a part of the game engine to efficiently run SkookumScript code and call engine commands from SkookumScript code;
  - __IDE (Integrated Development Environment)__ -- includes a code editor, class hierarchy browser, console (for running commands live), output and results log, visual debugger with stepping and breakpoints, and much more. The IDE can also call or be called by other favored tools or pipeline utilities, including other editors and IDEs. It is versatile and powerful.


<div markdown="1" class="focus">

## SkookumScript is evolving
  
SkookumScript is already notoriously nifty, and it is always being improved. The *Sleeping Dogs* team and our subsequent users have offered invaluable feedback, which has helped us make SkookumScript exponentially more awesome. Drop by the [SkookumScript Forum][forum] to check out the latest suggestions for improvements to SkookumScript, and to make suggestions of your own.
</div>


[setup]: /docs/ue4/setup/ "Download and setup SkookumScript UE4 plugin"
[forum]: https://skookum.chat "The SkookumScript Community Run Forum"
[license]: https://www.unrealengine.com/en-US/eula
[SkookumScript team]: /about/team/ "The SkookumScript Team"
[Smalltalk]: http://en.wikipedia.org/wiki/Smalltalk "Smalltalk - Wikipedia"
