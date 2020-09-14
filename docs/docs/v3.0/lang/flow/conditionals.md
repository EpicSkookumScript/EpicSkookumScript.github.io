---
layout: page
section: docs
title: Conditionals
numbered-headers: true
footer: false
sharing: false
date: 2015-09-04

---


## Quick reference

<div class="table-wrap" markdown="block">
| *[if](#if)*                | = | '`if`' {*[ws]* *[expression]* *[ws]* *[code-block]*}<sup>1+</sup> \[*[ws]* *[else-block]*\]
| *[when](#when)*            | = | *[expression]* *[ws]* '`when`' *[ws]* *[expression]*
| *[unless](#unless)*        | = | *[expression]* *[ws]* '`unless`' *[ws]* *[expression]*
| *[case](#case)*            | = | '`case`' *[ws]* *[expression]* {*[ws]* *[expression]* *[ws]* *[code-block]*}<sup>1+</sup> \[*[ws]* *[else-block]*\]
| *else-block*{:#else-block} | = | '`else`' *[ws]* *[code-block]*

</div>

It is useful to have the flow of your code run through alternative paths based on whether certain conditions are met. To do this _logical flow control_ you use _conditionals_ which include the commands: [`if`](#if), [`when`](#when), [`unless`](#unless), and [`case`](#case).

_If you think that you've heard this story before -- please read on -- SkookumScript may have some surprises for you_.

**Other mechanisms for alternate paths**{: .hdr}  
[Closures] -- especially routines that take closures as arguments -- [concurrent blocks], and the short-circuit `Boolean` operators `and`, `or`, `nand` and `nor` can also be used to create alternate code paths.
{:.note}

## '`if`' expression
{:#if}

An `if` expression has one or more _test expressions_ that evaluate to a `Boolean` (`true` or `false`) paired with associated _clause blocks_ (sometimes called _then_ clauses). Whichever test expression evaluates to `true` _first_ will run its associated clause block and then skip any remaining test/clause pairs and continue on to the next expression following the entire `if` expression.

The simplest form of an `if` expression is a single test expression with a single clause block.

### Single Test/Clause Pair
```js
// Test expressions and clauses can be simple
if expr > 5 [do_this]

// Method calls that return true/false usually end with '?'
// The fancy name for this is a 'predicate' method.
if test? [do_this]

if not test? [do_this]

// Test expressions can have multiple conditions
if test1? and test2? [do_this]

// Clauses can have multiple expressions
if test? [do_this1 do_this2]

if test?
  [
  do_this1
  do_this2
  ]
```

Simple conditionals with a single expression clause are often best represented with statement modifiers -- see [`when`](#when) and [`unless`](#unless).

Often you will want to have a test expression that always succeeds and ensures that at least one clause block is run. On these occasions you use an `else` clause.

An `else` is essentially the same as a test expression of `true` -- though it looks a little nicer and more explicitly gets your intent across.
{:.aside}

### 'else' Clause
```js
if test? [do_this] else [do_that]

// Essentially the same as:
if test? [do_this] true [do_that]

// The spacing and layout can be in many forms.
if test? [do_this]
  else [do_that]

if test?
  [do_this]
else
  [do_that]

if test?
  [
  do_this
  ]
else
  [
  do_that
  ]

// An else clause can have several expressions
// just like other clauses.
if test?
  [
  do_this1
  do_this2
  ]
else
  [
  do_that1
  do_that2
  ]
```

**Pro Tip: Two Random Alternate Paths**{: .hdr}  
If you want to randomly alternate between two possible code paths use the `Random.coin_toss()` method which randomly returns `true` or `false`.  
<br/>
`if @@random.coin_toss [path1] else [path2]`  
<br/>
`@@random` is the SkookumScript default psuedo-random number genenerator object which is always available.
{:.note}

Here is where things get a little interesting compared to many other languages. SkookumScript supports _multiple_ clauses in a single `if` expression. Just chain as many test/clause pairs together as you like and end it with an optional `else` clause.

The `if` expression is somewhat similar to the Lisp [`cond`](http://clhs.lisp.se/Body/m_cond.htm) expression though it has its own syntax. The other conditional expressions have similar usage and naming to [Lisp conditionals](https://www.cs.cmu.edu/Groups/AI/html/cltl/clm/node84.html) as well. This is cool -- though actually a total coincidence and an example of convergent evolution.
{:.aside}

### Multi-clause
```js
if test1? [do_one]
  test2?  [do_two]
  else    [do_else]

if test1?
  [do_one]
test2?
  [do_two]
else
  [do_else]

if test1?
  [
  do_one1
  do_one2
  ]
test2?
  [
  do_two1
  do_two2
  ]
else
  [
  do_else1
  do_else2
  ]

// If you are familiar with other languages that
// do not allow mulitple clauses it means that
// code like this below is a thing of the past:
if test1?
  [do_one]
else
  [
  if test2?
    [do_two]
  else
    [
    if test3?
      [do_three]
    else
      [do_else]
    ]
  ]

// Isn't this better?
if test1?
    [do_one]
  test2?
    [do_two]
  test3?
    [do_three]
  else
    [do_else]
```

## '`when`' expression modifier
{:#when}

Simple conditionals with a single clause can also be represented with the `when` _expression modifier_. `when` does not require a code block around its clause. It essentially makes an _optional_ expression.

```js
do_this when test?

// Same as code
if test? [do_this]

do_that when expr > 5

obj.do_stuff when obj.valid?
```

**Pro Tip: Random Expression**{: .hdr}  
You can easily make an expression run randomly with `Random.coin_toss()` and `when`.  
<br/>
`do_this when @@random.coin_toss`
{:.note}

You _\*can\*_ use a code block to group expressions in a `when` clause, though generally you should use an `if` in these cases instead and reserve `when` for simple single expressions.

```js
// Legal - but not recommended
[do_this do_that do_stuff] when test?

// Prefer `if` for clauses with multiple expressions
if test?
  [
  do_this
  do_that
  do_stuff
  ]
```

## '`unless`' expression modifier
{:#unless}

`unless` is an expression modifier similar to `when` that negates the test and only executes the earlier clause expression if the later test expression is `false`.

```js
do_this unless test?

// Same as code
if not test? [do_this]

do_that unless expr > 5

obj.do_stuff unless obj.invalid?
```
As with a `when` expression, you _\*can\*_ use a code block to group expressions in an `unless` clause, though generally you should use an `if` and `not` in these cases instead and reserve `unless` for simple single expressions.

## '`case`' expression
{:#case}

A `case` expression is similar to an `if` expression except that it does a logical `equal?()`/`=` comparison with an initial expression and a bunch of potential value expression and clause pairs. There can also be an optional `else` clause.

The initial expression is evaluated and then `equal?()`/`=` is called on it with each potential value in succession until one matches (returns `true`). If there are no matches then any optional `else` clause is run. Then the control flow continues on to the next expression following the entire `case` expression.

Several other languages use the key word `switch` rather than `case`. Also some languages use `default` rather than `else`. SkookumScript uses `else` like the `if` expression for consistency.
{:.aside}

### 'case' expression
```js
case expr
  val1 [do_one]
  val2 [do_two]
  else [do_three]

case expr
  val1
    [
    do_one1
    do_one2
    ]
  val2
    [
    do_one1
    do_one2
    ]
  else
    [
    do_three1
    do_three2
    ]
```

## Common conditional considerations

All conditionals are expressions that can [return a result](#results) and they all can [bind variables in their clauses](#binding-vars) which may change the types of the variables.


### Using the result of conditionals
{:#results}

The language geeks among you may have raised an eyebrow when I said conditional _expression_ rather than _statement_ -- this is not a mistake -- all conditionals are an [expression] and all expressions return a value.

Just like other [code blocks][code-block], the last expression in the successful clause will be the result. If there is no successful clause and there is no `else` clause then then result will be `nil`. Usually only conditionals where all paths have a result (and not `nil`) are used as a result -- though even conditionals that may return `nil` can be used.

Because the result of a conditional expression will be one of several alternative paths and the parser cannot know ahead of time which path will be successful, the class type of the result will be a union of _all_ the result types from each of the possible paths.

### Result of an 'if' expression
```js
// Single clause
!result: if test? ["first"]
// result will be "first" or nil
// and its class type will be <String|None>

// Single clause with else clause
!result: if test? ["first"] else ["else"]
// result will be "first" or "else"
// and its class type will be String
// All the conditional paths have the same result type
// so there is no need for a union class.

// Single clause with else clause and different types
!result: if test? ["first"] else [42]
// result will be "first" or 42
// and its class type will be <String|Integer>

// Multiple clauses - same type
!result: if test1? ["one"] test2? ["two"] else ["else"]
// result will be "one", "two" or "else"
// and its class type will be String

// Multiple clauses - different types
!result: if test1? [42] test2? [2.0] else ["else"]
// result will be 42, 2.0 or "else"
// and its class type will be <Integer|Real|String>

// The result of an if can also be used as an argument
println(if success? ["success"] else ["failure"])
```

`if` expressions are essentially the same as the [ternary operator](https://en.wikipedia.org/wiki/%3F:) used by many languages like `?:` in C++ -- though the SkookumScript `if` can have multiple clauses and has no statement (no result) version.
{:.aside}

### Result of modifier expressions
```js
!result: "first" when test?
// result will be "first" or nil
// and its class type will be <String|None>

// Can also be used as an argument
println(obj.name unless obj.invalid?)
```

### Result of a 'case' expression
```js
// Single clause
!result: case expr val1 ["first"]
// result will be "first" or nil
// and its class type will be <String|None>

// Single clause with else clause
!result: case expr val1 ["first"] else ["else"]
// result will be "first" or "else"
// and its class type will be String

// Single clause with else clause and different types
!result: case expr val1 ["first"] else [42]
// result will be "first" or 42
// and its class type will be <String|Integer>

// Multiple clauses - same type
!result: case expr val1 ["one"] val2 ["two"] else ["else"]
// result will be "one", "two" or "else"
// and its class type will be String

// Multiple clauses - different types
!result: case expr val1 [42] val2 [2.0] else ["else"]
// result will be 42, 2.0 or "else"
// and its class type will be <Integer|Real|String>

// The result of a case can also be used as an argument
println(
  case guy.name
    'Vader' ["bad guy"]
    'Yoda'  ["good guy"]
    else    ["don't know"]
  )
```


### Binding variables in clauses
{:#binding-vars}


Variables can be rebound (`:`) to different class types in clause code blocks. Since the parser cannot know which clause code path will be successful, the type of a varable after a conditional is a union of all the possible binding types.

#### Type Changing in Clauses
```js
!val: 42

// Type of val is Integer

if test? [val: 1234]

// Type of val is still Integer

if test? [val: "[Sk] can do fancy type-checking!"]

// Type of val is <Integer|String>

if test?
  [val: 2.0]
else
  [val: 3.14]

// Type of val is Real

if test1?
    [val: 888]
  test2?
    [val: "[Sk] tracks types for you"]

// Type of val is <Integer|Real|String>
```


[closures]: /docs/v3.0/lang/literals/closure/
[code-block]: /docs/v3.0/lang/flow/code-block/
[concurrent blocks]: /docs/v3.0/lang/syntax/#concurrent-block
[else-block]: #else-block
[expression]: /docs/v3.0/lang/expressions/
[ws]: /docs/v3.0/lang/whitespace/
[wsr]: /docs/v3.0/lang/whitespace/
