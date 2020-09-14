---
layout: page
section: docs
title: Code block
numbered-headers: true
footer: false
sharing: false
date: 2015-06-17

---

## Quick reference

<div class="table-wrap" markdown="block">
| *code-block*{:#code-block} | = | '`[`' *[ws]* \[*[expression]* {*[wsr]* *[expression]*} *[ws]*] '`]`'

</div>


Code blocks are used to group together a series of [expressions]. They can be used on their own, as the body of methods, coroutines and closures, or sub-parts of some flow control expressions such as `loop`, `if` and `case` clauses, `sync` and `race`. For now let's examine using code blocks on their own.

Like [Smalltalk], SkookumScript uses square brackets `[]` to indicate the beginning and ending of a code block.

{% highlight js %}
[expr1 expr2 expr3]
{% endhighlight %}

Simple [whitespace][ws] (which includes [comments]) is used to separate / delimit between expressions---or even no whitespace if the separation is obvious to the compiler. Expressions do not need an [end of expression / statement delimiter symbol][statement_delim] (such as `;`, `.` or newline)---the SkookumScript compiler knows what is and is not a valid expression, and figures it out for you.

## Identical code blocks with different spacing
```js
[expr1 expr2 expr3]

[
expr1
expr2
expr3
]

[expr1
 expr2
 expr3]
 
[
  expr1
    expr2
      expr3
        ] 
```

<div markdown="1" class="aside">
### Why use square brackets rather than curly braces `{}`, `begin`/`end`, etc.?

SkookumScript was initially inspired from [Smalltalk] which uses square brackets `[]` for code blocks so that is its heritage. There are many [different ways to group expressions][block_delims] including `do`/`end` like Lua and indention (known as the [off-side rule](https://en.wikipedia.org/wiki/Off-side_rule) <!-- _ --> like Python, though using curly braces `{}` like [C++], C# and JavaScript is probably the most widespread. C++ is the most common runtime/game engine language and the language that SkookumScript is written and embedded in so a common question is:

> Why not use curly braces `{}` for code blocks?

It turns out that visual code differences can actually be an *asset*.  It is common to switch back and forth from SkookumScript and the C++ used in a game engine. If the two languages have something that visually sets them apart at a glance, it makes it easier for coders' brains to switch to "SkookumScript" mode or "C++" mode as needed.  When the code gets too similar, coders start writing SkookumScript specific code in C++ files and C++ specific code in SkookumScript files.  We've tried SkookumScript with both `[]` and `{}` and having the code look a *little* different with square brackets `[]` leads to less mistakes.

Also square brackets `[]` on many keyboards do not need the `Shift` key pressed to type them so they are *clearly* superior.
</div>


## Code block result

The *result* of a code block is the result of the last expression in the series.

{% highlight js %}
[
// Results not used
expr1
expr2
// Result used as result for whole code block
expr3 
]
{% endhighlight %}

So you can do some work with earlier expressions in a code block and then return a result at the end of the code block.

{% highlight js %}
[
!result: do_something(get_some_info)
println("Here is the result: " result)
result // object/value returned by the code block 
]
{% endhighlight %}

Since the result of a code block is always the last expression, SkookumScript has no `return` command. Always ensure that the value you want to return from a code block is the last expression.


## Code blocks to specify order

A code block allows several expressions to be used in the place of a single expression. Wherever a single expression can be used, a code block with several expressions can be used instead. 

SkookumScript code is always evaluated in left to right order, with each expression grabbing as much text in a given set of script code as it can. This is particularly important to remember with operators since they have no precedence rules.

{% highlight js %}
// Evaluated as 2 * (3 + 4) = 14
// not as (2 * 3) + 4 = 10
2 * 3 + 4

// Evaluated as test1? or (test2? and test3?)
test1? or test2? and test3?
{% endhighlight %}

However you can use code blocks and their square brackets `[]` to group expressions to specify a different order. Many other languages and standard mathematical notation achieves the same effect with parentheses / brackets `()`.  

{% highlight js %}
// Evaluated as (2 * 3) + 4 = 10
[2 * 3] + 4

// Evaluated as (test1? or test2?) and test3?
[test1? or test2?] and test3?
{% endhighlight %}

<div markdown="1" class="aside">
### No special operator precedence order

Many languages have [precedence rules for their operators][op_precedence] such as multiplication `*` should be grouped together before addition `+`. However many languages have slight differences that can be a gotcha and source of errors and many programmers -- even really experienced ones -- cannot remember *all* the precedence rules correctly.

Due to this, it is generally considered to be good coding practice to explicitly specify the intended evaluation order using brackets `()` etc. even if a given expression evaluates in the order that you want due to precedence rules. Since SkookumScript has *no* precedence rules -- similar to Smalltalk -- specifying intended order other than simple left to right grouping is *mandatory* and you never need to worry if you are correctly remembering all the precedence order rules. 
</div>

<!-- div markdown="1" class="note">
**Pro tip: Use "Disassembly" in IDE to show evaluation order**{: .hdr}

As you are writing method and coroutine scripts in the Browser of the SkookumScript IDE you can view the how the parser is actually ordering expressions by toggling *Disassembly* \[`Ctrl`+`F11`\]. This converts the parsed data structures that are in memory back into text source code so that you can see how the parser actually sees the code without any *syntactic sugar*.
</div -->


[block_delims]: https://en.wikipedia.org/wiki/Comparison_of_programming_languages_%28syntax%29#Blocks "Block syntax in other languages - Wikipedia"
[C++]: http://en.wikipedia.org/wiki/C%2B%2B "C++ - Wikipedia"
[comments]: /docs/v3.0/lang/comments/
[expression]: /docs/v3.0/lang/expressions/
[expressions]: /docs/v3.0/lang/expressions/
[op_precedence]: https://en.wikipedia.org/wiki/Order_of_operations#Programming_languages "Operator precedence - Wikipedia"
[Smalltalk]: http://en.wikipedia.org/wiki/Smalltalk "Smalltalk - Wikipedia"
[statement_delim]: http://en.wikipedia.org/wiki/Comparison_of_programming_languages_(syntax)#Statements "Statement comparison - Wikipedia"
[ws]: /docs/v3.0/lang/whitespace/
[wsr]: /docs/v3.0/lang/whitespace/

