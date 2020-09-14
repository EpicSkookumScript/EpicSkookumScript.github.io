---
layout: page
section: docs
title: Expressions
footer: false
sharing: false
date: 2014-04-03 00:23

---

<div class="table-wrap" markdown="block">
| *expression*{:#expression} | = | *[literal]* \| *[identifier]* \| *[flow-control]* \| *[primitive]* \| *[invocation]* <span class="mgn_r15"></span>

</div>

An _expression_ is a combination of one or more specific commands, queries, values or names that is computed sometimes with [side-effects](https://en.wikipedia.org/wiki/Side_effect_(computer_science)) <!-- _ --> to produce a result value. Expressions are the smallest elements that describe an action in SkookumScript.

Performing the action and doing whatever computation is necessary is called code _evaluation_ or often code _execution_. In SkookumScript, everything is an expression and all expressions return a result when evaluated.

<div markdown="1" class="focus">
### Even nothing is a still a result

When an expression does not have an obvious result it returns `nil` which is an object that essentially represents _nothing_ or the absence of a value. This is a similar concept to a `void` result in C++. `nil`, or something like it, is common in many languages (Smalltalk, Lisp, Objective-C, Ruby). It goes by several different names, such as `NULL` (C), `nullptr` (C++), and `null` (JavaScript).
</div>

In addition to expressions, some languages (such as C++ and JavaScript) also have *[statements]*, which are contrasted from expressions in that they have no result and are executed primarily for their side-effect behavior.
{:.aside}

Simple [whitespace] (which includes [comments]) is used to separate / delimit between expressions---or even no whitespace if the separation is obvious to the parser. Expressions do not need an [end of expression / statement delimiter symbol][statement_delim] (such as `;`, `.` or newline)---the SkookumScript parser knows what is and is not a valid expression, and figures it out for you.

### Same expressions with different spacing
```js
println("expr1") println("expr2") println("expr3")

println("expr1")
println("expr2")
println("expr3")

println("expr1")
  println("expr2")
    println("expr3")
```

*TIP*{:.tip} Multiple expressions can be grouped together and treated as a single expression using a [code block][code-block].

There several kinds of expressions:

- [Literals][literal] create simple, handy building-block values such as numbers, strings of text, Booleans (`true` and `false`), and lists, as well as more sophisticated objects known as *closures* (which represent a hunk of code as an object).
- [Identifiers][identifier] reference objects in the language and include variables, data members, and classes. Another form of identifier unique to SkookumScript is an ​*object id*​, which references named objects often specified from outside the language (such as items placed in a game editor). Also related are the [variable primitives] for creating and setting variables.
- [Invocations][invocation] are the mechanisms for calling commands and actions called *routines* (methods and coroutines), which include special operator symbols for math, comparison and logic.
- [Type Primitives] includes expressions to manage type-checking and convert objects from one class type to another.
- [Flow-control][flow-control] specifies expression groupings, alternate code paths, iterations for code to execute, timings and concurrency.


[code-block]: /docs/v3.0/lang/flow/code-block/
[comments]: /docs/v3.0/lang/comments/
[identifier]: /docs/v3.0/lang/syntax/#identifier
[invocation]: /docs/v3.0/lang/syntax/#invocation
[flow-control]: /docs/v3.0/lang/syntax/#flow-control
[literal]: /docs/v3.0/lang/syntax/#literal
[primitive]: /docs/v3.0/lang/syntax/#primitive
[statements]: https://en.wikipedia.org/wiki/Statement_(programming) "Wikipedia article on 'Statements'"
[statement_delim]: http://en.wikipedia.org/wiki/Comparison_of_programming_languages_(syntax)#Statements "Statement comparison - Wikipedia"
[Type Primitives]: /docs/v3.0/lang/syntax/#type-primitives
[variable primitives]: /docs/v3.0/lang/syntax/#var-primitives
[whitespace]: /docs/v3.0/lang/whitespace/
