---
layout: page
section: docs
title: Type system
footer: false
sharing: false
date: 2016-08-24

---

SkookumScript's [type system](http://en.wikipedia.org/wiki/Type_system) (type model) is powerful, flexible, safe, and *gets out of the way as much as possible*. Unlike many other scripting languages, SkookumScript is fully type-checked at compile-time, which catches many bugs before the game runs.

<div class="table-wrap" markdown="block">
| Typing | SkookumScript methodology
|:-|:-
|[Inferred] vs. [Manifest]|When context is available, types are inferred; otherwise, types must be manifest (specified) when needed.
|[Static] vs. [Dynamic]|Uses static type-checking during compile-time though has full dynamic type info during runtime and several dynamic syntax features.
|[Strong vs. Weak]|Strongly typed.
|[Nominal] vs. [Structural]|Uses nominal with nominal subtyping -- types are known via inference or being explicitly specified rather than determining type by examining an object's structure.
|[Union Types]|Uses union types. These can be specified explicitly `<Class1|Class2>` and also be auto-inferred based on alternate code paths.
|[Duck Typing]|Uses a limited form of duck typing: reduction of 'nil' and object(s) unions to just object(s).
|[Latent Typing]|Uses latent typing—types are associated with objects (values) rather than variables.
|[Unified Type System]|All class types have `Object` as a common (root) super class.
|[Type Conversion]|Explicit type casting `expression<>SomeClass` and type conversion `expression>>SomeClass` (type can be inferred if context available: `expression<>` or `expression>>`). Implicit coercion is intentionally omitted to reduce unintentional conversion bugs.
    
</div>

[Astro]: http://www.joelonsoftware.com/articles/fog0000000018.html "Joel On Software article on 'Architecture Astronauts'"
[Castle in the Sky]: http://www.imdb.com/title/tt0092067/ "IMDB listing for 'Castle in the Sky'"
[closures]: /docs/v3.0/lang/syntax/#closure "Closure - SkookumScript syntax"
[Conan Reis]: /about/team/#conan-reis "Conan Reis on Team page"
[dict-skookum]: http://dictionary.reference.com/browse/skookum "Dictionary.com entry for 'skookum'"
[DogFood]: http://en.wikipedia.org/wiki/Eat_your_own_dogfood "Wikipedia article on 'eat your own dogfood'"
[Duck Typing]: http://en.wikipedia.org/wiki/Duck_typing
[Dynamic]: http://en.wikipedia.org/wiki/Type_system#Dynamic_type-checking_and_runtime_type_information
[ergo]: /about/origin/#ergo "Ancestor language: Ergo"
[forum]: https://skookum.chat "The Official SkookumScript Community Forum"
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
[testimonials]: /about/testimonials/ "SkookumScript Testimonials"
[traits]: http://en.wikipedia.org/wiki/Trait_%28computer_programming%29 "Wikipedia article on 'traits'"
[Triad Wars]: http://www.unitedfrontgames.com/games/triad-wars/ "Triad Wars - massively multiplayer open-world action adventure"
[Twit]: https://twitter.com/SkookumScript "SkookumScript - Twitter Page"
[Type Conversion]: http://en.wikipedia.org/wiki/Type_conversion
[UE4blog]: /blog/categories/unreal/ "SkookumScript Unreal Engine 4 plugin blog posts"
[Unified Type System]: http://en.wikipedia.org/wiki/Type_system#Unified_type_system
[Union Types]: http://en.wikipedia.org/wiki/Union_type
[United Front Games]: http://www.unitedfrontgames.com "United Front Games - Website"
