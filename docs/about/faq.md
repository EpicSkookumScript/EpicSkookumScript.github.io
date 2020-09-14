---
layout: page
section: about
title: Frequently asked questions
sharing: false
footer: false

---

{: .toc-levels}
- [General topics](#general-topics)
  - [What does "skookum" mean?](#qst-skookum)
  - [Can SkookumScript be used "out-of-the-box"?](#qst-oob)
  - [Can SkookumScript be used for anything other than gameplay?](qst-other-uses)

- [Libraries and add-ons](#libraries-and-add-ons)
  - [Is SkookumScript already integrated into game engines and APIs?](#qst-engines)
  - [Can the SkookumScript IDE be used by my product’s end users to customize or extend my product?](#qst-enduser)

- [Integrated development environment](#integrated-development-environment)
  - [Can I use an IDE or editor of my choice to edit SkookumScript source code?](#qst-my-ide)

- [The language](#the-language)
  - [What programming paradigm does SkookumScript use?](#qst-paradigm)
  - [Is SkookumScript object-oriented?](#qst-oop)
  - [What does SkookumScript do to maximize code reuse?](#qst-code-reuse)
  - [Does SkookumScript provide a mechanism to describe common functionality between classes like multiple inheritance, interfaces and protocols, traits or mixins?](#qst-common-class-func)
  - [Are there advantages of text over visual "node"-based languages?](#qst-txt-vs-vis)
  
- [Technical details](#technical-details)
  - [Is SkookumScript compiled or interpreted?](#qst-compiled)
  - [Does SkookumScript use a virtual machine (VM)?](#qst-vm)
  - [Can I choose which components of the SkookumScript API I'd like to use, or is it all-or-nothing?](#qst-modular)
  - [How long will it take to initially integrate SkookumScript into my project?](#qst-integration)

<br/>
_Have a question that is not answered here? Put it to us in the [SkookumScript forum][forum]._

## General topics

{: .faq}
<span id="qst-skookum"/>What does "skookum" mean?

  : "Skookum" is Canadian for large, powerful, excellent, first-rate, and generally *awesome*. It has its origins in <a href="https://en.wikipedia.org/wiki/Chinook_Jargon" title="Chinook Jargon on Wikipedia">Chinook jargon</a> of the U.S. Pacific Northwest and Canada's West Coast, where SkookumScript creator Conan Reis grew up and SkookumScript development originated. (Also see <a href="http://en.wikipedia.org/wiki/Skookum#Principal_meaning" title="Wikipedia article on meaning of the word 'skookum'">Wikipedia</a> and <a href="http://dictionary.reference.com/browse/skookum" title="Dictionary.com entry for 'skookum'">Dictionary.com)
  
<span id="qst-oob"/>Can SkookumScript be used "out-of-the-box"?

  : Yes! With the turn-key [SkookumSript Unreal Engine 4 Plugin](#qst-engines).

<span id="qst-other-uses"/>Can SkookumScript be used for anything other than gameplay?

  : SkookumScript is primarily designed for video games, but it is very powerful and versatile. Just as SkookumScript can be hooked up to a game engine, it can be used in other technologies requiring interactivity or real-time automation, including:
  
    - user interface authoring and control
    - world editor commands
    - smoke-testing
    - application scripting and extension
    - testing (quality assurance)
    - settings (tweaking variables on load or during development)
    - simulations
    - medical and architectural imaging
    - embedded control logic
    - artificial intelligence, machine learning, intelligent assistants
    - robotics
    - aeronautics, space vehicles
    - amusement park rides, wristwatches, toasters
    - Internet of Things (IoT)

    
## Libraries and add-ons
    
{: .faq}
<span id="qst-engines"/>Is SkookumScript integrated into game engines and APIs?

  : Yes. SkookumScript is available as a turn-key plugin for Unreal Engine 4.
  
    [![SkookumScript + Unreal](/images/Unreal/SkookumAndUnreal_trans.png){:.pic-full}][UE4plugin]
    
    With the [SkookumSript Unreal Engine 4 Plugin][UE4plugin], you can write SkookumScript code without writing code in any other language.

    SkookumScript is also used in proprietary game engines, such the ones developed at [United Front Games]. Awesome games such as *[Sleeping Dogs]* and *Sleeping Dogs: Definitive Edition* were created with SkookumScript.
  
    You can also integrate SkookumScript into other top-tier game engines or your own custom engine. Hooking up SkookumScript to a game engine requires a certain amount of C++ proficiency—you must use the SkookumScript API to [hook up](#qst-integration) to a framework. This is fairly straightforward and most engineers "get it" by simply looking at a few examples.

{: .faq}
<span id="qst-enduser"/>Can the SkookumScript IDE be used by my product’s end users to customize or extend my product?

  : Yes! You can release a game editor for your game that uses SkookumScript to make new game logic. A key advantage of SkookumScript is that it facilitates the creation of user-generated content.

## Integrated development environment

{: .faq}
<span id="qst-my-ide"/>Can I use an IDE or editor of my choice to edit SkookumScript source code?

  : Yes. While the SkookumScript Integrated Development Environment (SkookumIDE) has features that you will likely find incredibly useful, there are probably features in *Your Favourite Editor&trade;* that you can't live without. The SkookumScript language and IDE are designed to exist seamlessly in a hybrid development environment comprised of many different tools and applications..

    The SkookumIDE has many cool features that other IDEs will not support, because these features are tied to unique properties of the SkookumScript language. The SkookumIDE also can give your favorite text editor or alternate IDE scripting superpowers, providing much of the same functionality and other mechanisms of cross-program communication. For example, it is trivial to set up a hotkey toggle to switch back and forth from editing in the SkookumScript IDE and the editor of your choice.
  
## The language

{: .faq}
<span id="qst-paradigm"/>What programming paradigm does SkookumScript use?

  : SkookumScript primarily uses an [object-oriented](#qst-oop) [paradigm](http://en.wikipedia.org/wiki/Programming_paradigm), though it allows for some mixed (hybrid) models such as [functional programming](http://en.wikipedia.org/wiki/Functional_programming) using constructs, such as <a href="http://en.wikipedia.org/wiki/Closure_%28computer_programming%29">closures</a>.

<span id="qst-oop"/>Is SkookumScript object-oriented?

  : Yes. SkookumScript uses a pure [object-oriented programming](http://en.wikipedia.org/wiki/Object-oriented_programming) model like Smalltalk, Eiffel or Ruby. All class types have <code>Object</code> as a common (root) super class.

<span id="qst-code-reuse"/>What does SkookumScript do to maximize code reuse?

  : SkookumScript has several features that encourage code reuse.
  
    **Code reuse language features:**
  
    - pure object-oriented system with the polymorphism you’d expect, such as the ability to use inherited routines or to override routines with custom behaviour
    - it is easy to package up common code into reusable routine calls. People often write code for a specific case in a mission, realize that it could be useful in other areas, and then quickly and easily clean it up and put the common code in its own routine
    - SkookumScript’s built-in concurrency commands (running a bunch of routines at the same time with commands such as `race`, `sync`, and `branch`) make writing durational routines (commands that take a while to complete called coroutines) easy to write and reuse. For example, it is easy to cancel a complicated durational routine when it is midway through without needing to add extra parameters, loops, polling, or special tracking variables.
    - SkookumScript has built-in [closures] (similar to anonymous functions, lambdas or delegates) which make it really easy to treat code as data and plug-in and swap out code that does not require the hassle of creating whole new subclasses.
  
    **Code reuse practices:**
  
    Many game engines (such as Unreal Engine 4) use an entity and component model to describe game objects, where you can add or remove components that give various capabilities. For example, you could make a call to return the "interface" to a game entity’s physics component that you could use for any physics-related commands or queries. This works really effectively—we highly recommend this technique. It is more of a coding *practice* than a specific *feature*, though it is easy to adopt such a practice with SkookumScript.
  
    **Code reuse runtime features:**
  
    - SkookumScript sits on top of the host engine C++ environment and can reuse C++ calls, engine features and other common C++ libraries.
    - \[[Unreal 4 plugin][UE4plugin] specific\] You can interact with UE4 Blueprints, and have Blueprints call SkookumScript commands.
  
    **Code reuse IDE and compiler features:**
  
    - SkookumScript’s *overlay* mechanism is similar to modules or libraries in other languages. Overlays make it easy to share scripts and functionality across projects.  A video game project is comprised of a stack of overlays, each with a specific scope, such as company-wide (e.g. `AwesomeIncCore`), engine-specific (e.g.`Engine`), or project-specific (e.g. `CoolSpaceGame`). The `Core` overlay contains all of SkookumScript’s standard classes and commands.
    - Code snippets that you run on the SkookumIDE console are heavily reused across a team. They are an easy way to type in simple commands and snippets of logic that you can run on the game or editor in real-time—also known as the [read-eval-print-loop (REPL)][REPL]. For example there could be code snippet that says, "create five bad guys in front of the player, make it dark and raining and reset the player’s health."

    Most importantly, SkookumScript is easy to understand. It is a pleasure to use because its conciseness, and the fact that annoying setup and bookkeeping tasks are done for you, allows everything to fit in your head without your brain melting.
    {:.aside}
    
<span id="qst-common-class-func"/>Does SkookumScript provide a mechanism to describe common functionality between classes such as multiple inheritance, interfaces and protocols, traits or mixins?

  : SkookumScript is a pure object-oriented language with single inheritance.

    We are leaning towards adding something like [traits], or perhaps some sort of [mixin] capability, rather than [multiple inheritance] or [interfaces and protocols]. We haven’t done this yet for three reasons:
    
    - We tend to focus on features that have the most compelling justification to improve development of in-production games of the moment. This is definitely on our list, though there has so far always been other features we think would give better “bang for the buck”. \(That being said we will happily add it in an intelligent way if it becomes a priority.\)
    - One of the goals of SkookumScript is to reduce complexity where possible. Adding capabilities for multiple inheritance, traits, mixins, etc. is more complex than just sticking to single inheritance.
    - All the other [reuse mechanisms above](#qst-code-reuse) can get you a long way—certainly sufficient to produce already existing AAA games.
        
<span id="qst-txt-vs-vis"/>Are there advantages of text over visual "node"-based languages?

  : There are clear advantages to scripting with text-based code such as SkookumScript rather than a visual node-based language.

    - an easy way to type in simple commands and snippets of logic in a console to run on the game or editor in real-time—also known as the [read-eval-print-loop (REPL)][REPL]; These code snippets are easy to swap, trade, modify and reuse as well
    - simpler version control, allowing you to track changes and note differences using common professional tools
    - easier to work on and scale in a team environment, especially when more than one person is working on the same area
    - search and replace: over files, regular expressions, etc.
    - able to use Your Favourite Editor&trade;
    - easy to extend: adding new statements or modifying existing
    - easier to debug with print statements and step-wise debugging (if your language -- like SkookumScript -- has it)
    - more sophisticated logic allows an "escape hatch" when needed to get you past the 90% completion point
    - easier to document
    - good editors and IDEs with sophisticated auto-complete and syntax highlighting *can* be just as visually informative and error correcting as visual languages
    - and many more

    Of course the point is that some tools, workflows, etc. are better or easier to *get things done*. Any existing visual logic can be used along-side any SkookumScript code, so SkookumScript can readily co-exist with a visual scripting system, such as UE4 Blueprints. 

    Use whatever logic tool seems the best for a given gameplay scenario or workflow.
    

## Technical details

{: .faq}
<span id="qst-compiled"/>Is SkookumScript compiled or interpreted?

  : SkookumScript code is compiled to its own platform-independent, intermediate binary (called a "runtime structures binary") when stored (saved or serialized). It is loaded into memory as optimized runtime structures when needed, with all platform considerations such as endian-ness handled automatically.

    SkookumScript’s runtime structures are faster than byte-code (it does not use a *virtual machine*) and a little less speedy than native machine code—though more flexible.

    __Speed__: slower __&lt;__ faster<br>
    <br>
    interpreted<br>
    &nbsp;&nbsp;&nbsp;&nbsp;__&lt;__ byte-code with Virtual Machine (VM)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;__&lt;__ SkookumScript runtime-structures<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;__&lt;__ native code
    {:.aside}
    
    It is possible for SkookumScript to parse (evaluate) strings of text and run them as commands, though this is generally only done during debugging. A shipped project will usually run only compiled SkookumScript code, since it is faster and uses less memory.

<span id="qst-vm"/>Does SkookumScript use a virtual machine (VM)?

  : No. The SkookumScript runtime uses a faster mechanism where the previously-compiled, platform-independent "runtime structures binary" is loaded and converted once into data-driven optimized C++ data-structures that give near-native C++ performance. Unlike a typical VM, this mechanism uses direct pointers and offsets into tables rather than looking up byte op-codes.
  
    So SkookumScript has most of the speed of native code, while retaining most of the runtime flexibility of interpreted code.
 
<span id="qst-modular"/>Can I choose which components of the SkookumScript API I'd like to use, or is it all-or-nothing?

  : SkookumScript's modular design allows you to use only the components you need. SkookumScript can include or exclude libraries and tech based on needs, including:
    
    - parser (ability to read in text code)
    - compiler (ability to write out code binary)
    - disassembler (ability to write out text code from compiled code in memory)
    - remote workbench command console (a sophisticated [read-eval-print loop or REPL][REPL])
    - debugging (including step-wise debugging, breakpoints, profiling, runtime checks and more)
    - runtime (the environment that manages and runs SkookumScript commands and events)
  
    Generally the most common configurations are for:
    
    <div class="table-wrap" markdown="block">
    | Configuration | Typical capabilities
    |:-|:-
    |SkookumScript IDE and compiler|Parser, compiler, binary loader, disassembler, console, debugging, runtime (local to the IDE)
    |Project and developer tools|Binary loader, connection to remote console and debugging, runtime
    |Final shipped product|Binary loader and runtime
    
    </div>
    
    There are also several mechanisms to connect systems to tech of your choosing, so that they better integrate with your project, existing tech or platform. For example: memory allocation, file system, online communications, error handling, etc.
    
    You can also choose to use the efficient C++ core libraries which are used as fundamental building blocks for SkookumScript. This can kick-start your own development and ensure that it is very easy for your engine to communicate with the SkookumScript runtime.
    {:.aside}

<span id="qst-integration"/>How long will it take to initially integrate SkookumScript into my project?

  : Integrating SkookumScript with its C++ API is fairly simple and fast—possibly just a couple of hours. Call a few functions (and optionally override some methods) with your project-specific preferences and tech.  Place `SkookumScript::init()` and `SkookumScript::deinit()` in appropriate locations. Add `SkookumScript::update()` to your update loop.
  
    Next, you must use the SkookumScript C++ API to bind (hook in) the game engine features that you want SkookumScript to access. Likewise it is fairly straightforward to have your game engine make SkookumScript calls for various script commands.
    {:.aside}
    

[Astro]: http://www.joelonsoftware.com/articles/fog0000000018.html "Joel On Software article on 'Architecture Astronauts'"
[Castle in the Sky]: http://www.imdb.com/title/tt0092067/ "IMDB listing for 'Castle in the Sky'"
[closures]: /docs/v3.0/lang/syntax/#closure "Closure - SkookumScript syntax"
[Conan Reis]: /about/team/#conan-reis "Conan Reis on Team page"
[dict-skookum]: http://dictionary.reference.com/browse/skookum "Dictionary.com entry for 'skookum'"
[DogFood]: http://en.wikipedia.org/wiki/Eat_your_own_dogfood "Wikipedia article on 'eat your own dogfood'"
[Duck Typing]: http://en.wikipedia.org/wiki/Duck_typing
[Dynamic]: http://en.wikipedia.org/wiki/Type_system#Dynamic_type-checking_and_runtime_type_information
[ergo]: /about/origin/#ergo "Ancestor language: Ergo"
[forum]: https://skookum.chat "The SkookumScript Community Run Forum"
[Inferred]: http://en.wikipedia.org/wiki/Type_inference
[interfaces and protocols]: http://en.wikipedia.org/wiki/Protocol_%28object-oriented_programming%29 "Wikipedia article on 'interfaces and protocols'"
[Latent Typing]: http://en.wikipedia.org/wiki/Latent_typing
[Manifest]: http://en.wikipedia.org/wiki/Manifest_typing
[mixin]: http://en.wikipedia.org/wiki/Mixin "Wikipedia article on 'mixins'"
[multiple inheritance]: http://en.wikipedia.org/wiki/Multiple_inheritance "Wikipedia article on 'multiple inheritance'"
[Nominal]: http://en.wikipedia.org/wiki/Nominative_type_system
[origin]: /about/origin/ "SkookumScript's Origins"
[REPL]: http://en.wikipedia.org/wiki/REPL "Wikipedia article on 'read-eval-print loop'"
[Sleeping Dogs]: /about/#sleeping-dogs "SkookumScript Showcase: Sleeping Dogs"
[skookum-wiki]: http://en.wikipedia.org/wiki/Skookum#Principal_meaning "Wikipedia article on meaning of the word 'skookum'"
[Static]: http://en.wikipedia.org/wiki/Type_system#Static_type-checking
[Strong vs. Weak]: http://en.wikipedia.org/wiki/Strong_and_weak_typing
[Structural]: http://en.wikipedia.org/wiki/Structural_type_system
[team]: /about/team/ "The SkookumScript Team"
[traits]: http://en.wikipedia.org/wiki/Trait_%28computer_programming%29 "Wikipedia article on 'traits'"
[Triad Wars]: http://www.unitedfrontgames.com/games/triad-wars/ "Triad Wars - massively multiplayer open-world action adventure"
[Twit]: https://twitter.com/SkookumScript "SkookumScript - Twitter Page"
[Type Conversion]: http://en.wikipedia.org/wiki/Type_conversion
[UE4plugin]: /unreal/ "SkookumScript plugin for Unreal Engine 4"
[Unified Type System]: http://en.wikipedia.org/wiki/Type_system#Unified_type_system
[Union Types]: http://en.wikipedia.org/wiki/Union_type
[United Front Games]: http://www.unitedfrontgames.com "United Front Games - Website"
