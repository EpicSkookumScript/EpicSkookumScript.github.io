---
layout: page
section: docs
title: Parser error checking
numbered-headers: true
footer: false
sharing: false
date: 2016-04-20

---

Warnings and errors are two of the hippest and coolest things about SkookumScript because it can notify you about many of them _even as you are typing_ rather than only when you are executing the code. Developers experience warnings and errors every day, and it pays to have a good workflow associated with them. Before attempting to run your code, the SkookumScript parser does as much up-front work as possible to detect errors.

SkookumScript can detect over 150 kinds of errors, and issue seven different warnings of varying sternness. (Don't worry, you'll experience them all eventually.)

*NOTE*{: .mark} These errors and warnings and their visualizations apply equally to [**Workbench** widgets](/docs/v3.0/ide/workbench/) and to code in [**Editor** widgets](/docs/v3.0/ide/editors/).


## Lexical (spelling) errors

Everybody makes typos (or as Computer Science PhDs prefer to call them, "booby-boo-boos"). But luckily for humanity, SkookumScript's sophisticated error-checking will prevent your typos from causing mayhem on a planetary scale. (Well, usually.)

{% highlight js %}
println("Hello, world!")
printl("I'll be your megalomaniacal overlord for today.")
{% endhighlight %}

If you select the above two lines and press `F4`, you will get the following rap on the knuckles:

{% highlight text %}
ERROR: The method 'printl()' does not exist for an instance
of the class 'SkookumDemo'.
vvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvv
println("Hello, world!")
printl("I'll be your megalomaniacal overlord for today.")
-----^ <<<< Line: 2, columns: 1-7
 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Script code index: [26-32]
{% endhighlight %} <!-- _ -->

As you can see, an `n` is missing in `println`. Just type in the fix (perhaps assisted by auto-complete, which, if anything, is usually over-eager to make suggestions) and try again.

*NOTE*{: .mark} No part of a code selection will be executed if the parser encounters an error in any part of the selection.

## Syntax (grammar) errors

This bit of code is missing an end bracket:

{% highlight js %}
42.max(33.min(11.max(9))
{% endhighlight %}

If you evaluate it, you will get the following sharp slap on the buttocks:

{% highlight text %}
ERROR: Expected the end of the invocation list ')', but did not
find it. [Too many arguments supplied?]
vvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvv
42.max(33.min(11.max(9))
>>>>>>>>>>>>>>>>>>>>>>> ^ <<<< Line: 1, column: 25
vvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvv
{% endhighlight %} <!-- _ -->

The compiler will heroically attempt to pinpoint the location where the fix should go. Yes, it's still a hero even it turns out to be incorrect.

## Semantic (meaning and logic) errors

Sometimes code might look error-free at first glance, yet still have errors in logic or meaning. The SkookumScript compiler will craftily catch these too.

{% highlight js %}
42.max("amok")
{% endhighlight %}

If you try to execute the above code, you will get the following slap across the face with a cold, wet fish:

{% highlight text %}
ERROR: The argument supplied to parameter named 'num' was
expected to be of type 'Integer' and it is type 'String' which
is not compatible.
vvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvv
42.max("amok") 
>>>>>>>>>>>> ^ <<<< Line: 1, column: 14
vvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvv
{% endhighlight %} <!-- _ -->

The `max()` method expects a number, not a string.

One of the reasons SkookumScript can detect this sort of error is that it is [strongly typed](http://en.wikipedia.org/wiki/Strong_and_weak_typing) <!-- _ --> and uses [static type checking](http://en.wikipedia.org/wiki/Type_system#Static_type-checking). This is often referred to as _compile-time type-checking_ -- though the SkookumIDE checks types even as you are typing and not just when compiling code binaries. The types can often be inferred (guessed by the parser by looking at the surrounding code) and types frequently do need to be explicitly specified. For more info check out the [SkookumScript type system](/docs/v3.0/lang/typesystem/).
{:.aside}


## Hints and visualizations from the SkookumIDE

The SkookumIDE has a few mechanisms to spot, visualize and prevent errors, even as you are typing code.


### Auto-parse

The SkookumScript parser will continuously and automatically parse code text to determine if it is valid as changes are made.

- [**Workbench** widgets](/docs/v3.0/ide/workbench/) will automatically parse any code that is selected or it will try to intelligently guess (sometimes if fails to determine your unfathomable human expectations) if code nearby the edit caret is correct
- [**Editor** widgets](/docs/v3.0/ide/editors/) will automatically parse a whole routine or script file

If it is not valid, the compiler adds a red wavy underline (or "squiggle") to the problem area. This is a valuable early-warning system that saves you the humiliation of pressing `F4` and being swiftly rejected.

_**And**_ as a huge time-saver, you can also mouse hover over an error wavy line to get the associated error description.

![SkookumIDE auto-parse](/images/Docs/SkIDE-Editor-autoparse-sel.png){: .img-center}

Same example from earlier showing red error squiggle and mouse hover with error description.
{:.caption}


### Bracket highlighting

The bracket grouping symbols—`[` `]` for blocks, `(` `)` for invocation arguments, and `{` `}` for lists—all have slight color shading between different group pairs, with three alternating shades representing levels of nesting. In the default color style, the first bracket for a group will be a bright light green, the next will be a medium green, and the next will be a dark green and then it repeats: bright, medium, dark, bright, medium, dark. Each matching closing bracket _should_ have a matching color, so you can tell at a glance which brackets match.

![SkookumIDE bracket group highlighting](/images/Docs/SkIDE-Editor-bracket-groups.png){: .img-center}

Group symbols with alternating shading helps determine matching symbols at a glance and there is still a red error squiggle pinpointing the first indication of an error.
{:.caption}


### Class highlighting

When you enter class names into a SkookumIDE **Workbench** or **Editor** widget, valid (known) classes will be colored  yellow, while invalid (unknown) classes will be colored orange. This catches class name typos as they are being written -- and more importantly, it adds a refreshing citrus ambiance to your code.

![SkookumIDE class highlighting](/images/Docs/SkIDE-Editor-class.png){: .img-center}

Guess which is a valid class and which is not.
{:.caption}


---
[**← Return to**{:.tip} **Workbench widgets**](/docs/v3.0/ide/workbench/#work-through-the-tutorial-workbench) (if you just came from there)
{:.bubble-link}
