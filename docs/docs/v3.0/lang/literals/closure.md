---
layout: page
section: docs
title: Closure
footer: false
sharing: false
date: 2015-07-02

---

<div class="table-wrap" markdown="block">
| *closure*{:#closure}[^closure] | = | \['`^`' \['`_`' *[ws]*\] \[*[expression]* *[ws]*\]\] \[*[parameters]* *[ws]*\] *[code-block]*
| *closure-tail-args*{:#closure-tail-args}[^cls-tail]  | = | *[ws]* *[send-args]* *[ws]* *[closure]* \[*[ws]* '`;`' *[ws]* *[return-args]*\]
| *invoke-class*{:#invoke-class}[^iclass]  | = | \['`_`' \| '`+`'\] *[parameters]*

</div>

[^closure]: Optional `^` or *[parameters]* or both must be provided (unless used in *[closure-tail-args]* where both are optional). Optional *[expression]* (which may not be *[code-block]* or *[closure]*) will be captured and used as receiver/this for the *[code-block]* -- if not provided `this` is inferred. Optional `_` indicates it is durational (like a coroutine) -- if not present durational/immediate inferred via *[code-block]*. Parameter types, return type, scope, whether surrounding `this` or temporary/parameter variables are used and captured may all be inferred if omitted.
[^cls-tail]: Routines with last send parameter as mandatory closure may omit brackets `()` and closure arguments may be simple *[code-block]* (omitting `^` and *[parameters]* and inferring from argument parameter context). Default arguments indicated via comma `,` separators.
[^iclass]: `_` indicates durational (like coroutine), `+` indicates durational or immediate (coroutine or method) and lack of either indicates immediate (like method). Class `Closure` matches any closure interface. Identifiers and defaults used for closure arguments without parameters.

A [_closure_][closure-wiki] (also called closures in [Swift](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/Closures.html) and known as [_lambda expressions_ in C++](http://en.cppreference.com/w/cpp/language/lambda) or _blocks_ in [Ruby](http://ruby-doc.com/docs/ProgrammingRuby/html/tut_containers.html) and [Smalltalk](https://en.wikipedia.org/wiki/Smalltalk#Code_blocks)) is a series of expressions grouped together like an anonymous (without a name) routine together with parameters, that also includes (closes around) a referencing environment for the receiver (`this`) and non-local variables of that code.  This referencing environment creates and stores variables with the same name of any captured variables (including `this`) outside its immediate lexical scope by binding a *reference* to the objects the captured variables refer to at the time of the evaluation of the closure expression (and not the *value* of the captured variables at the time of the closure's invocation).

To get something similar to SkookumScript closures, a C++ lambda expression would use a _lambda-introducer_ of `[&, this]` if the this is captured or `[&]` if a receiver expression is supplied using `^`.
{:.aside}

Closures allow treating code as an object so it can be passed to and returned from routines and delay its evaluation until needed. This allows callbacks, custom control flow, and all manner of powerful constructs.

Most of the time the syntax for closures can be fairly straightforward, though on occasion they can have some of the most tricky syntax in the language. 

```js
!triple: (Integer x)[3 * x]
triple(4) // returns 12
```

The return class type of a closure can often be inferred so you don't need to explicitly specify it.

The above `triple` closure infers the `Integer` return class, and it is the same as:

```js
!triple:
  (Integer x) Integer
    [
    3 * x
    ]
```

See some closure-related info including [closure sample code on the SkookumScript forum](https://skookum.chat/t/closure-sample-code/149/2).


### Inferring type from context

The parameters for a closure can be inferred from surrounding context so they can be much more concise---see ["Closures as arguments" in the Primer](/docs/v3.0/#closures-as-arguments).


### Closure tail arguments

Whenever the _last_ parameter of a routine is a closure, the routine parentheses `( )` are not needed---the closure is used as a terminator for the arguments. This allows you to make routines that look similar to built-in language flow control commands. See ["Closure tail arguments" in the Primer](/docs/v3.0/#closure-tail-arguments).


### Calling closures

Learn about invoking closures at ["Closure invoke operator" in the Primer](/docs/v3.0/#closure-invoke-operator).


<div class="footline" id="footline"></div>


[closure]: #closure
[closure-tail-args]: #closure-tail-args
[closure-wiki]: https://en.wikipedia.org/wiki/Closure_(computer_programming)
[code-block]: /docs/v3.0/lang/flow/code-block/
[expression]: /docs/v3.0/lang/expressions/
[parameters]: /docs/v3.0/lang/syntax/#parameters
[return-args]: /docs/v3.0/lang/syntax/#return-args
[send-args]: /docs/v3.0/lang/syntax/#send-args
[ws]: /docs/v3.0/lang/whitespace/

