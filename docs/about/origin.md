---
layout: page
section: about
title: SkookumScript's origin story and future
sharing: false
footer: false

---

###### By [Conan Reis](/about/team/#conan-reis), SkookumScript creator

<br>
_A bit of history covering the languages [Ergo](#ergo), [ChewieScript](#chewiescript), [SkookumScript](#skookumscript), [Verse](#verse) and the future..._

I first used a game-centric scripting language at Electronic Arts Canada (now known as [EA Vancouver](https://en.wikipedia.org/wiki/EA_Vancouver)) in the early 1990s, when EA Canada was still small enough to know most people by name. Although that language, _**Xyzzy**_ (pronounced "cheezy"), was fairly simple, using it was a great experience and I quickly realized that game oriented languages are the best way to create gameplay logic and make the game development process more satisfying and fun.

When I started developing my own video game projects, none of the existing programming languages available felt right for the needs of game development. Yes, you *can* make a game without a dedicated language – though any self-respecting craftsman knows you should use the right tools for the job. Making *fantastically great* games is my goal, so rather than use something sub-optimal, I embarked on a decades-long journey of game language creation.


## Ergo

![Ergo Logo](/images/about/Logo-Ergo_sm.png){:.right-margin .clear-all}
I started work on my first game scripting language, _**Ergo**_, in 1995. Ergo was funded in part through a $105K grant from the BC Science Council (now known as [Innovate BC](https://innovatebc.ca/)). It was a powerful and compact [distributed programming language](https://en.wikipedia.org/wiki/Distributed_computing) with a tiny syntax that fit on less than a page. It enabled you to write one program and have it run on several networked computers. When it required greater processing power, it would add additional computers to distribute the load and get faster results. This was just before the term [_cloud computing_](https://en.wikipedia.org/wiki/Cloud_computing) was popularized around 1996.

I have been building and evolving game scripting languages ever since. SkookumScript has some concepts from Ergo in its DNA -- particularly [closures](/docs/v3.0/lang/literals/closure/) and the ability to transfer hunks of code across networks.

## ChewieScript

![ChewieScript Logo](/images/about/Logo-ChewieScript_sm.png){:.left-margin .clear-all}
In 2001 I started a multi-year stint at [LucasArts Entertainment](http://en.wikipedia.org/wiki/LucasArts), where I was hired to create the successor to the venerable [***SCUMM***](http://en.wikipedia.org/wiki/SCUMM) scripting language. Initially called "Son of SCUMM", my new language _**ChewieScript**_ (named after the iconic _Star Wars_ engineer Chewbacca) was designed for practicality, performance and scalability. And whenever a compiler error in the code was encountered the ChewieScript IDE would make the iconic Chewbacca anger / distress call as a sound effect. [This could be toggled -- though it had Lucasfilm assent and was awesome!] 

Observing ChewieScript being used to develop _Star Wars: Bounty Hunter_ taught me a great deal about what works and what leads to bugs, especially in a large team setting. Several features I thought were _great_ in theory turned out to be, well, _not-so-great_ in practice. So, based on the team's feedback, I refined those features until they really were great – which is to say, conducive to both great gameplay for the player _and_ optimal workflow for the development team. 

This firmly instilled my ethos of "[eating your own dog food][DogFood]" while developing tools and tech – which is why reusability has long been one of my major priorities. Over the years as I worked at various video game companies, I licensed my language tech to each company, allowing me to keep ownership of (and build on) the tech rather than abandon it at the end of each game project. As a result, some of ChewieScript's DNA lives on in SkookumScript today.

## SkookumScript

![SkookumScript Logo](/images/about/Logo-SkookumScriptP_sm.png){:.right-margin .clear-all}
Work on SkookumScript officially began in July 2004. One of SkookumScript's key superpowers is that it evolved and continues to be enhanced during the development of actual shipping games for over a decade. I never cluttered things up by adding unnecessary features -- we were shipping a game and did not have time to be "[Architecture Astronauts][Astro]". However, SkookumScript _does_ have the critical bits that were not initially planned for though ended up being needed at the eleventh hour -- because in the end we did ship.

> It is my firm belief that all successful languages are grown and not merely designed from first principles.
_-- **Bjarne Stroustrup**<br>[The Design and Evolution of C++](http://www.stroustrup.com/dne.html)_{:.quoter}

SkookumScript was first used in 2008 during the development of [Sleeping Dogs][SDogs]. It had so many praises from the scripters and level designers using it that I decided to make the main purpose of Agog Labs to forward SkookumScript.

<div class='embed-container'>
  <iframe src="//player.vimeo.com/video/94688238" frameborder='0' webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>
</div>
> From the technical aspects I really liked how Skookum was robust. It basically never hit our profile in rendering performance, which is fantastic. Overall it was rock solid.
_-- **[Dave Roberts](http://linkedin.com/pub/david-roberts/2/a71/4b3)**<br>Technical Director on Sleeping Dogs &amp; Triad Wars<br>at United Front Games_{:.quoter}

<div class='embed-container'>
  <iframe src="//player.vimeo.com/video/94585251" frameborder='0' webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>
</div>
> SkookumScript is, without question, the most powerful and efficient scripting language I have used for creating quests in games.
_-- **[David Sitar](http://www.linkedin.com/profile/view?id=35528960)**<br>Mission Designer / Scripter at United Front Games_{:.quoter}

> I have not worked with a scripting language that gives as much power to scripters as SkookumScript does. I shudder to think of how difficult it would have been to get the same results with another scripting language.
_-- **[Mark Lewis](http://www.linkedin.com/in/fury2112)**<br>Mission Scripter at United Front Games_{:.quoter}

I personally believe that SkookumScript's greatest feature set is its [structured concurrency][concurrency]: `sync`, `race`, `branch`, `change` and the `Mind` class (used to organize groups of concurrent expressions at runtime), plus apply operators `%` (serial) and `%>` (concurrent race) and the supporting concurrency API. In particular I consider `race` to be one of my biggest gifts to computer science -- super simple and ridiculously powerful. These combine to make a whole [new stage-directed programming model][death-tick] ideal for simulations like games.

In addition to structured concurrency, honorable mentions also go to the SkookumScript features:
- The SkookumIDE and its [live execution of code](/docs/v3.0/ide/workbench/) and [live modification of existing code](/docs/tutorials/create-first-routine/#modify-a-method) -- all without needing to restart or lose any progression
- [Object IDs](/docs/v3.0/#object-ids)
- [Closure tail arguments](/docs/v3.0/#closure-tail-arguments) and [closures](/docs/v3.0/lang/literals/closure/) in general
- [Instantiation](/docs/v3.0/#instantiation) -- in particular [inferred instantiation](/docs/v3.0/#instantiation-with-inferred-class) and [expression instantiation](/docs/v3.0/#expression-instantiation)
- [Live integration with Unreal Engine Blueprints and Blueprint graphs](/docs/ue4/quickstart/#call-skookumscript-methods-and-coroutines-from-blueprint-event-graphs)
- [Super fast compilation](/blog/2016/10-04-faster-compile/) of large projects. While not really a feature -- still super cool.
- [Demand script loading](/docs/v3.0/rt/demand-loading/) (only used in _[Sleeping Dogs][SDogs]_)

After shiping Sleeping Dogs I sought out the viability of selling SkookumScript as a game development tool. I headed out to GDC 2014 to talk with game studio CEOs, CTOs and game developers of all sorts. They all agreed that a game oriented scripting language would be welcome in their development.

Though I wrote much of the Sleeping Dogs engine, I only had rights to SkookumScript. And a game language isn't too useful without an engine. I was in luck since this was the year that Epic changed their licensing model to $20 a month. I spoke with several Epic staff and they were excited at the prospect of hooking SkookumScript up to Unreal. So I decided to go for it.

I was doubly in luck in that my good friend and past coworker from LucasArts [Markus Breyer][Markus] had agreed to let me crash at his house in the nearby San Rafael (nearish to GDC and where I used to live when I worked at LucasArts). He also had a pass to GDC and heard me pitch SkookumScript to many a game dev at the conference. After a while Markus couldn't help himself and started jumping in and saying, "oh and it has this interesting feature too!". A bit after the conference Markus realized he couldn't shake SkookumScript from his system and he asked if he could join me as a cofounder. I was honored and agreed.

Next year at [GDC 2015](/blog/2015/03-12-GDC2015-results/) there were three of us in Agog Labs and Markus officially quit his day job at 2K Games to work on SkookumScript full time as Agog's CTO. Our booth was a bit hit.

[![GDC 2015 - the first SkookumScript booth](/images/blog/2015GDC-SkookumBooth-Muahahaha.jpg){:.pic-full}](/blog/2015/03-12-GDC2015-results/)

GDC 2015 - the first SkookumScript booth and public release
{:.caption}

During this GDC I met with Tim Sweeney in all my mad computer scientist splendor and let him know about what we were doing with SkookumScript and how we hooked it up to Unreal. I was concerned that he might object since Epic had removed _his_ baby of UnrealScript. He listened intently and said that it sounded like SkookumScript was really game oriented and impressively tied with Unreal - it even had live support of Blueprint graphs - and he gave SkookumScript his assent.

And we were off!

[SkookumScript](https://www.unrealengine.com/marketplace/en-US/product/skookumscript) ended up being the first code based plugin tested for the Unreal Marketplace. We worked with Epic extensively -- they ended up giving us direct Perforce access to the Unreal code base and we rewrote some major aspects of the Unreal build pipeline to be friendlier to plug-in scripting languages.

Being used in the workflow at all phases of a project has ensured that SkookumScript can painlessly scale to a project's size. It works well both in the starting phases of a project with few people and many unknowns, and during finaling when there are many people who require stability, performance and predictability. SkookumScript has had the time to evolve and become lean, efficient, practical, scalable, maintainable, and reliable -- the good parts have been made great, while any painful bits have been pruned out.

> Good software takes ten years.
_-- **Joel Spolsky**<br>[Joel on Software](http://www.joelonsoftware.com/articles/fog0000000017.html)_{:.quoter}

SkookumScript is, in a word, [skookum](/about/faq/#qst-skookum). Which is Canadian / Pacific Northwest for _"awesome"_.

## Verse
(and Epic Games)

![Verse Logo](/images/about/Verse_Logo.svg){:.height8em .left-margin .clear-all}
SkookumScript was being used in numerous Unreal projects and several AAA studios were starting to kick its tires and take it out for serious test drives. They were mightily impressed with the power and performance of the tech and the tooling -- though they were worried about making the backbone of their tens of millions and sometimes hundreds of millions of dollars projects depend on such a small studio as Agog Labs. Many recommended that we partner with a larger tool studio such as Epic Games -- so I set out to do just that.

First Agog did some contract work with Epic in 2018 -- I helped hook in [Python for Unreal editor automation][upython] and created a mechanism to auto generate the [Unreal Python API docs][upythonapi].

More and more Unreal teams were using SkookumScript. And so there came a time when:

> Is there anything we can do to help you and SkookumScript?
_-- **Epic Games**_{:.quoter}

> Yes, buy us.
_-- **Conan Reis**_{:.quoter}

And so they did.

[![Acquired by Epic](/images/about/Agog-Epic-Laptop.jpg){:.pic-full}](/blog/2019/01-23-epic-aquires-agog/)

Agog Labs and SkookumScript is acquired by Epic Games
{:.caption}

Working out the legalities took a long time (and _three_ separate teams of lawyers) though by December 2018, [Agog Labs and SkookumScript had been acquired by Epic Games][acquired] -- or more specifically _Epic Games Canada_ since Agog Labs was a Canadian company.

And so a team was assembled to start working on a new language for Epic Games. This was before the COVID-19 Pandemic when not many people worked remotely and _Zoom_ wasn't a verb yet. The SkookumScript team was seven strong (five engineers, a wordsmith/booth czar and an artist) though we didn't want to move from our established locales  to be closer to Epic offices. Only [Markus] and I were given the green light to work remotely due to our seniority -- so alas, the rest of the team was given both thanks and payouts and went off in search of new adventures. In addition to Markus and myself -- the initial Epic language team had four others for a grand total of six. Tim Sweeney was not officially on the language team at that time and was planning to act only in a light advisory capacity -- he had this company to run after all.

We had several debates about just using and reworking SkookumScript and its tech to be the new language. At first the main purpose was to have the language work with the Unreal Engine. SkookumScript was obviously already working in this capacity and had examples of running 140 times faster than Blueprints and even 40 times faster than nativized Blueprints on PlayStation 4. It had its own editor and debugger written in Unreal Slate UI. The SkookumScript language syntax could be relatively easily changed as needed but we could save time by keeping the language core. However, it was written _outside_ of Epic without full access to the internals of Unreal. So we would want to rewrite the language tech to use Unreal data structures and use Unreal C++ coding style etc. When asked how long this might take Markus and I gave an estimate -- about six months. _Six months!!!_ That was deemed _waaay_ too long and so the plan was to build the initial language on the Blueprint Virtual Machine (VM) and use Visual Studio Code as the editor. [Note that Verse was eventually released to the public about four and a half years later -- and hindsight is 20/20.]

[![Verse hello world in VS Code](/images/about/Verse_hello-world-device-vs-code.png){:.pic-full}](/images/about/Verse_hello-world-device-vs-code.png)

Verse "hello world" device in Visual Studio Code
{:.caption}

The name for the language evolved over time. The language was initially intended to have a simultaneous text and visual representation and the test language framework was called _tLang_ -- for "Temporary Language". That evolved into the working name _uLang_ -- which you might think stood for "Unreal Language", though it was actually _mu_ Lang (μ) by one of the early team members. All the while the language was being kept under wraps from the public and even a bit from the rest of Epic. The project's code name was [_Solaris_ (after the book)][solaris] so the language was often referred to as the _Solaris_ language. To limit unintentional leaks even further, some aspects of the language's links to other code in Unreal was called _ProtoLem_ (the author of Solaris being _Stanisław Lem_). So it basically had _four_ initial names! We later had a competition in the team for a real and trademarked name. We came up with many names, including sticking with uLang (or μLang) which some people wanted to keep. In the end my suggested name of _Verse_ was chosen -- since it is simple, related to Epic as in "epic verse" or poetry and of course the meta*verse* -- its intended use. [Note that Facebook had not yet rebranded itself as _Meta_.] Not _ideal_ for unique searches, though nine months after the public release of Verse, searching for "Epic Verse", "Verse language" and "Verse lang" all get the [Epic Games Verse language reference documentation][verseref] as its first match.

I also championed Verse having a logo and its particular "V" design. [Though the design itself was due to a talented UX designer and a talented artist. I'll see if they mind if they are mentioned by name...] So Verse feels very personal to me.

> If you want to get software engineers to have strong opinions, a good technique is to ask them about their programming language preferences.
<br>{:.quoter}

The early days of designing Verse were challenging -- though we eventually came to a consensus and got it up and running on test projects and fully integrated into the Epic build pipeline. It still had both a text and visual version that you could go back and forth between. Then around September 2019 the idea of using the creator base of Fortnite as the starting point of Epic's idea of the metaverse began taking shape and some early prototypes of what would eventually become the [Unreal Editor for Fortnite (UEFN)][UEFN] were experimented with -- and then became its own team. We put the visual representation of the language on the backburner. It turns out that making a visual language is quite tricky. [_Joke_: we all knew this would be a _monumental_ hurdle.] Verse was no longer being initially targeted for the Unreal Engine. Tim Sweeney became a regular presence to direct the language design using the syntax and parser from a concept language he had been tweaking in the background for years -- with a renewed focus on UEFN and the future metaverse.

Here are some of the contributions I made to Verse:
- Designed and wrote much of the Verse concurrency system borrowing from SkookumScript though Verse has a number of novel concepts. This is my main contribution from SkookumScript and the aspect of Verse that I am most proud of. See my [2023 Unreal Fest talk on Verse Concurrency][vconcurrencyufest] and the [Verse Reference Documentation on Concurrency][vconcurrency].
- Designed and/or wrote initial implementations of 10 of the 13 Verse flow control expressions including `sync`, `race`, `rush`, `branch`, `block`, `spawn`, `loop`/`break`, `defer` and even `if` (with its failure semantics designed by Tim). [Guess what the other 3 flow control expressions are...]
- The name for the Verse type `logic` was my suggestion when Tim didn't want to go with bool -- so you can thank/blame me
- Added Verse tuples, named and optional arguments, local using, early parser, type and semantic analysis systems
- Hunks of the Verse API especially async/suspends related aspects including the `Simulation` module, `Sleep()`, `task` and `event` classes
- Worked on many of the lower level Verse systems such as the integration with C++ engine, async function calling from C++ (which allows the `OnBegin()` device Verse entry points), changes with the Unreal build system to better suite Verse, making the Blueprint VM easier to work in
- And much more. Most if not all of these aspects of Verse have been worked on collaboratively with the rest of the amazing Verse team -- extending, rewriting, optimizing, etc., etc.

<div class='embed-container'>
  <iframe src="https://www.youtube.com/embed/B3WiSgKXsrg" frameborder="0" allowfullscreen></iframe>
</div>

My 2023 Unreal Fest talk on Verse Concurrency -- some of the key aspects of SkookumScript DNA passed on to Verse
{:.caption}

Over this time, the Verse team both gained and lost members. We added more language experts and luminaries and the push to have Verse working with UEFN began in earnest. Everything now had to [work _within_ Fortnite][UEFNdev] -- which meant no user added C++, inability to use Unreal Blueprints and its existing huge API. It also meant getting Verse integrated with VS Code using a Verse extension and integrating everything into UEFN. This included having Verse used in Fortnite AI internally and doing many Verse examples, code jams and tests to get things ready. We worked like mad and just barely got over the finish line to release the UEFN Beta and the first public release of Verse at the Game Developers Conference in March 2023.

[![Ask me about Verse sign at GDC booth](/images/about/Verse_2023-03_GDC.jpg){:.pic-full}](/images/about/Verse_2023-03_GDC.jpg)

GDC 2023 March -- Launch of UEFN Beta and booth with "Ask me about Verse" sign
{:.caption}

We braced ourselves for any missed issues though it was a success! UEFN creators were publishing experiences that could run on all the platforms of Fortnite on the same day that we released the UEFN Beta during the Game Developer Conference.

[![Unreal Fest UEFN Creators](/images/about/Verse_2023-UnrealFest-creators.jpg){:.pic-full}](/images/about/Verse_2023-UnrealFest-creators.jpg)

Unreal Fest 2023 New Orleans October -- with the UEFN Creators
{:.caption}

The first few months of Verse and UEFN use has been amazing and it has been gratifying to see all the UEFN projects leveraging Verse. Unreal Fest in October 2023 in New Orleans was updated to include talks on UEFN and Verse. Meeting the UEFN creators and actual Verse coders was an honor and especially made it feel like we had made it.

[![Unreal Fest T-shirt with Verse concurrency](/images/about/Verse_2023-UnrealFest-shirt.jpg){:.pic-full}](/images/about/Verse_2023-UnrealFest-shirt.jpg)

Unreal Fest 2023 New Orleans October -- Amazing to see Verse concurrency constructs on the back of a t-shirt! [Maybe caught a potential bug...](https://x.com/ConanReis/status/1709054653315313892?s=20)
{:.caption}


## The future

Verse continues to be evolved and optimized with a new custom virtual machine. Its API will be growing tremendously to specifically take advantage of Fortnite and metaverse implications. The Verse tooling is only in its first phases. Verse will eventually be made available for the Unreal Engine and even farther still is planned to be made open source.

SkookumScript is still used on some Unreal Engine projects while anyone is waiting for Verse to be Unreal ready.


[acquired]: /blog/2019/01-23-epic-aquires-agog/
[Astro]: http://www.joelonsoftware.com/articles/fog0000000018.html "Joel On Software article on 'Architecture Astronauts'"
[death-tick]: https://error454.com/2017/03/09/the-death-of-tick-ue4-the-future-of-programming/ "The death of tick"
[concurrency]: /docs/v3.0/lang/flow/concurrency/
[DogFood]: http://en.wikipedia.org/wiki/Eat_your_own_dogfood "Wikipedia article on 'eat your own dogfood'"
[flow]: /docs/v3.0/lang/syntax/#Flow-Control "Flow control syntax"
[Markus]: /about/team/#markus-breyer
[SDogs]: /about/#sleeping-dogs "More detail on Sleeping Dogs"
[skookum]: http://en.wikipedia.org/wiki/Skookum#Principal_meaning "Wikipedia article on meaning of the word 'skookum'"
[solaris]: https://en.wikipedia.org/wiki/Solaris_(novel) "Solaris (novel) on Wikipedia"
[team]: /about/team/ "The SkookumScript Team"
[UEFN]: https://www.unrealengine.com/en-US/free-download/uefn-unreal-editor-for-fortnite "Unreal Editor for Fortnite"
[UEFNdev]: https://forums.unrealengine.com/t/uefn-development-considerations-authors-epic-alike/1201558
[upython]: https://docs.unrealengine.com/scripting-the-unreal-editor-using-python/
[upythonapi]: https://docs.unrealengine.com/PythonAPI/
[vconcurrency]: https://dev.epicgames.com/documentation/en-us/uefn/concurrency-in-verse
[vconcurrencyufest]: https://dev.epicgames.com/documentation/en-us/uefn/concurrency-in-verse
[verseref]: https://dev.epicgames.com/documentation/en-us/uefn/verse-language-reference
