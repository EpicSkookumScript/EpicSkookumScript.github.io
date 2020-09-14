---
layout: page
section: about
title: SkookumScript's origin story
sharing: false
footer: false

---

###### By [Conan Reis](/about/team/#conan-reis), SkookumScript creator

I first used a game-centric scripting language at [Electronic Arts Canada](http://en.wikipedia.org/wiki/Electronic_Arts_Canada) in the early 1990s, when EA Canada was still small enough to know most people by name. Although that language, _**Xyzzy**_ (pronounced "cheezy"), was fairly primitive, using it was a great experience and I quickly realized that scripting languages are the best way to create gameplay logic and make the game development process more satisfying and fun.

When I started developing my own video game projects, I found no programming language available that truly met many key needs of game development. Yes, you *can* make a game without a dedicated language – though any self-respecting craftsman knows you should use the right tools for the job. Making *fantastically great* games is my goal, so rather than use something sub-optimal, I embarked on a decades-long journey that would culminate in the creation of SkookumScript.


## Ergo

![Ergo Logo](/images/about/Logo-Ergo_sm.png){:.right-margin .clear-all} I started work on my first game scripting language, _**Ergo**_, in 1995. Ergo was funded in part through a $105K grant from the BC Science Council (now known as [Innovate BC](https://innovatebc.ca/)). It was a powerful and compact [distributed programming language](https://en.wikipedia.org/wiki/Distributed_computing) with a syntax that fit on a single page. It enabled you to write one program and have it run on several networked computers. When it required greater processing power, it would add additional computers to distribute the load and get faster results. This was over a decade before the term [_cloud computing_](https://en.wikipedia.org/wiki/Cloud_computing) was popularized around 2006.

I have been building and evolving game scripting languages ever since. SkookumScript has some concepts from Ergo in its DNA -- particularly [closures](/docs/v3.0/lang/literals/closure/) and the ability to transfer hunks of code across networks.

## ChewieScript

![ChewieScript Logo](/images/about/Logo-ChewieScript_sm.png){:.left-margin .clear-all} In 2001 I started a multi-year stint at [LucasArts Entertainment](http://en.wikipedia.org/wiki/LucasArts), where I was hired to create the successor to the venerable [***SCUMM***](http://en.wikipedia.org/wiki/SCUMM) scripting language. Initially called "Son of SCUMM", my new language _**ChewieScript**_ (named after the iconic _Star Wars_ engineer Chewbacca) was designed for practicality, performance and scalability. 

Observing ChewieScript being used to develop _Star Wars: Bounty Hunter_ taught me a great deal about what works and what leads to bugs, especially in a large team setting. Several features I thought were _great_ in theory turned out to be, well, _not-so-great_ in practice. So, based on the team's feedback, I refined those features until they really were great – which is to say, conducive to both great gameplay for the player _and_ optimal workflow for the development team. 

This firmly instilled my ethos of "[eating your own dog food][DogFood]" while developing tools and tech – which is why reusability has long been one of my major priorities. Over the years as I worked at various video game companies, I licensed my language tech to each company, allowing me to keep ownership of (and build on) the tech rather than abandon it at the end of each game project. As a result, some of ChewieScript's DNA lives on in SkookumScript today.

## SkookumScript

![SkookumScript Logo](/images/about/Logo-SkookumScriptP_sm.png){:.right-margin .clear-all}
Work on SkookumScript officially began in July 2004. SkookumScript is "right" and "real", in that it evolved and continues to be enhanced during the development of actual shipping games for over a decade. I never cluttered things up by adding unnecessary features -- we were shipping a game and did not have time to be "[Architecture Astronauts][Astro]". However, SkookumScript _does_ have the critical bits that were not initially planned for though ended up being needed at the eleventh hour -- because in the end we did ship.

> It is my firm belief that all successful languages are grown and not merely designed from first principles.
_-- **Bjarne Stroustrup**<br>[The Design and Evolution of C++](http://www.stroustrup.com/dne.html)_{:.quoter}

Gameplay tools are often developed while they are in active use developing a game title, and just when they are getting really good and useful, the game ships and the tools are discarded, and then they are rebuilt from scratch for the next title. SkookumScript was designed to render this wasteful practice obsolete.

Being used in the workflow at all phases of a project has ensured that SkookumScript can painlessly scale to a project's size. It works well both in the starting phases of a project with few people and many unknowns, and during finaling when there are many people who require stability, performance and predictability. SkookumScript has had the time to evolve and become lean, efficient, practical, scalable, maintainable, and reliable -- the good parts have been made great, while any painful bits have been pruned out.

> Good software takes ten years.
_-- **Joel Spolsky**<br>[Joel on Software](http://www.joelonsoftware.com/articles/fog0000000017.html)_{:.quoter}

SkookumScript will save you time, money and brain cells, and help you make your great games even greater. It is my gameplay tool of choice (big surprise there!), and many others who have used it think so too. 

SkookumScript is, in a word,  [skookum](/about/faq/#qst-skookum). Which is Canadian for "awesome".

## Epic Games and the future...

And now SkookumScript and the ideas and features behind it are [owned by Epic Games, Inc.][acquired] and we are busily using SkookumScript DNA to power up Epic's tools and products.


[acquired]: /blog/2019/01-23-epic-aquires-agog/
[DogFood]: http://en.wikipedia.org/wiki/Eat_your_own_dogfood "Wikipedia article on 'eat your own dogfood'"
[Astro]: http://www.joelonsoftware.com/articles/fog0000000018.html "Joel On Software article on 'Architecture Astronauts'"
[skookum]: http://en.wikipedia.org/wiki/Skookum#Principal_meaning "Wikipedia article on meaning of the word 'skookum'"
[team]: /about/team/ "The SkookumScript Team"
