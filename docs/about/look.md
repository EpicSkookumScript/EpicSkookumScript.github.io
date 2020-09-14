---
layout: page
section: about
title: Show me some code!
numbered-headers: true
sharing: false
footer: false

---

Since its creation in 2004, SkookumScript's syntax has evolved based on inspiration, necessity, user feedback, influences from many other languages, and the occasional computer lab mishap. 

SkookumScript looks different from other languages in a few key ways, such as its use of square brackets `[]` for code blocks (rather than `{}`, `begin`/`end`, etc.), and its use of whitespace between expressions, arguments, list elements, and other statements instead of special characters (such as `;`) or the end of the line. The following easy-to-grasp examples demonstrate that SkookumScript is a distinctly distinct language with many uniquely unique features.

## Hello, world! Goodbye, clutter!

In keeping with the [ancient computer nerd tradition][HelloWorld] of demonstrating the ease of getting the simplest programs up and running, here is SkookumScript's "Hello world":

```js
println("Hello, world!")
```

This is the output:

```text
Hello, world!
```

Pretty simple, eh?

The above example shows that SkookumScript programs are not cluttered with “bookkeeping cruft” such as carefully-ordered includes, notes to the compiler, and class wrappers. SkookumScript uses a [multi-pass compiler][Mult-pass] to determine what files and components are needed, and automatically manages them in the memory of the parser and runtime, so aspects such as dependencies are always up-to-date.

## Time-flow logic

Let's jump right in with some examples of commands that do not complete immediately, where you can specify your desired time-flow logic, such as sequential (one after the other) or concurrent (simultaneous).

### Sequential commands

In the following examples there is a `guy` object that walks and a `car` object that drives. Let's start with two sequential commands – when the first command is completed, the second command will execute.

```js
// Two consecutive commands
// Each executes one after the other.
guy._walk  // Guy completes walk.
car._drive // Then car drives.
println("Completed")
```

`guy` will print "Walking..." when the `_walk` command starts, and "Walked" when the walk is completed. Likewise, `car` will print "Driving..." when the `_drive` command starts, and "Drove" when completed. This is the output:

```text
Walking...
Walked
Driving...
Drove
Completed
```

**Coroutines and methods**{: .hdr}<br/>
Commands that may take time (multiple frames) to complete are called _coroutines_ and have identfier names that must start with an underscore `_`.  Commands that start without an underscore such as `println()` complete immediately (within the same frame) and are called _methods_.
{:.note .info}

**Optional parentheses**{: .hdr}<br/>
If a command does not need any arguments to be passed when it is called, parentheses `()` are not necessary, so `_walk` above is the same as `_walk()`. [The Ruby language is similar in this way.]
{:.note .info}

### Concurrent commands: `sync`

Now let's have `guy` and `car` execute their commands concurrently (at the same time) with `sync`. 

```js
// Guy and car both start at same time.
// Next line runs after both guy and car have completed.
sync
  [
  guy._walk
  car._drive
  ]
println("Completed")
```

If `guy` takes longer to finish walking than `car` takes to finish driving, this is the output:

```text
Walking...
Driving...
Drove
Walked
Completed
```

**Square brackets and code blocks**{: .hdr}<br/>
Like Smalltalk programming language, SkookumScript uses square brackets `[]` to indicate the beginning and end of a [code block] rather than `{}`, `begin`/`end` or indentation using significant whitespace.<br/>
{: .note .info}

**Whitespace separates statements**{: .hdr}<br/>
Simple whitespace (rather than a semicolon `;`, the end of a line or other mechanisms) is used to delimit (separate) statements, expressions and arguments. And sometimes even whitespace is not needed in cases where the separation is obvious to the compiler.
{: .note .info}

### Concurrent commands: `race`

Let's say you don't know whether the walk or drive will be faster, and you want to run the next line as soon as either one completes.

```js
// Guy and car both start at same time.
// Next line is run after whichever one completes first
// and any remaining commands are cancelled.
race
  [
  guy._walk
  car._drive
  ]
println("Completed")
```

This is the output:

```text
Walking...
Driving...
Drove
Completed
```

Note that "Walked" is never printed, since the drive completes first and the walk is aborted before it completes.

### Concurrent commands with timeout: `wait`

Now let's add some additional complexity by adding a timeout with `wait`. If neither `car` nor `guy` reach their destination within 120 seconds, then both will be aborted.

```js
// Guy and car both start at same time.
// Next line is run after whichever completes first
// and any remaining commands are cancelled.
race
  [
  guy._walk
  car._drive
  _wait(120)
  ]
println("Completed")
```

Assuming neither `guy` nor `car` makes it in time, this is the output:

```text
Walking...
Driving...
Completed
```

### Concurrent commands: one from the trenches 

We'll end our concurrency examples with a more sophisticated command from <em>[Sleeping Dogs](/about/#sleeping-dogs)</em>:

```js
// All characters within 20 meters of the player will
// path to the player. Proceed to the next line after
// they have all reached the player.
// If no character is within 20 meters then do nothing.
@'Player'.list_near(20)%_path_to_actor(@'Player')
```

**Object IDs**{: .hdr}<br>
`@'Player'` is an example of a *validated object ID*—it retrieves the player character by name from the simulated world. Game objects can be referred to by name and checked at compile-time for correctness. Any class of object can be set up to use object IDs—for example `BadGuy@'EvilBob'`, `TriggerRegion@'trap_door'` or `Marker@'Destination42'` generally by communicating with the world editor such as the Unreal Engine Editor.
{: .note .info}

**Apply operators**{: .hdr}<br>
The percent sign `%` used after a list object is an *apply operator*—it applies the adjacent routine call simultaneously across all the items in the list.
{: .note .info}

There are many more concurrency commands built into SkookumScript, and it is easy to make your own custom concurrency-related commands.

> The advantage of conciseness is not just reducing finger typing, but reducing the amount of code you read.
_-- **Bill Venners**<br>(paraphrasing Guido van Rossum)_{:.quoter}

## Conditional flow control: `if`

Now let's see some more _traditional_ logical control flow with [conditionals] such as `if`.

### Single `then` clause
{% highlight js linenos %}
if test? [do_this]

if expr > 5 [do_this]

if test? [do_this1 do_this2]

if test?
  [
  do_this1
  do_this2
  ]

// Statement modifier version
do_this when test?

// Negated statement modifier version
do_that unless test?
{% endhighlight %}

### `then`–`else` clause
{% highlight js linenos %}
if test? [do_this] else [do_that]

if test? [do_this]
else     [do_that]

if test?
  [do_this]
else
  [do_that]

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
{% endhighlight %}

### Multiple clauses
{% highlight js linenos %}
if test1? [do_one]
  test2?  [do_two]
  else    [do_three]

if test1?
    [
    do_one1
    do_one2
    ]
  test2?
    [
    do_one1
    do_one2
    ]
  else
    [
    do_three1
    do_three2
    ]
{% endhighlight %}

### `case` statements with multiple clauses
{% highlight js linenos %}
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
{% endhighlight %}

## Iteration and looping

There are many mechanisms in SkookumScript to iterate (loop) through items. They should cover almost every scenario, and if not, it is easy to build your own custom iteration commands that look and work just like native language commands.  Here are some examples: 

### Bounded iteration
{% highlight js linenos %}
// Repeat 10 times
10.do[do_this do_that]

10.do
  [
  do_this
  do_that
  ]

// Iterate over a list of numbers  
!nums: {1 2 3 4}

nums.do[println(item)]
// Prints:
// 1
// 2
// 3
// 4

nums.do_reverse[println(item)]
// Prints:
// 4
// 3
// 2
// 1
{% endhighlight %}

**Local variables**{: .hdr}<br>
`!nums: {1 2 3 4}` above creates a variable called `num` that is bound to a `List` of `Integer` objects.<br>
<br>
The exclamation mark `!` indicates that something "new" is being created in SkookumScript -- in this case `!nums` creates a new variable called `num`.<br>
{: .note .info}

**Binding variables**{: .hdr}<br>
The colon `:` is used to <em>bind</em> a variable to a new object. The type of a variable is inferred automatically based on past context by the compiler whenever it is bound to an object.<br>
{: .note .info}

**Lists**{: .hdr}<br>
A <em>list literal</em> is a series of expressions surrounded by curly brackets / braces `{}`. The item type of the list is inferred by the compiler. Also note that any comma separators `,` are optional -- they are only used if they aid readability. So `{1 "two" 3.0}` is the same as `{1, "two", 3.0}`.
{: .note .info}

**Closures**{: .hdr}<br>
The `do` commands above use a simple form of a *[closure]* (also known as anonymous functions, lambda expressions and code blocks). If you aren't familiar with closures, they are supremely awesome—and SkookumScript closures are an order of magnitude more so!<br/>
<br/>
Essentially, closures allow you to group a chunk of code and its surrounding environment so you can treat it as data, just like any other object. You can do an infinite number of very splendid and worthwhile things with closures in SkookumScript, with very little typing or screen space.
{: .note .info}

### Simple loops
{% highlight js linenos %}
// 'while' loop
!count: 0
loop
  [
  if count >= 10 [exit]
  do_this
  do_that
  count++
  ]

// 'do while' loop
!count: 0
loop
  [
  do_this
  do_that
  count++
  if count >= 10 [exit]
  ]

// Middle exit
!count: 0
loop
  [
  do_this
  if count >= 10 [exit]
  do_that
  count++
  ]

// Named loops
loop outer
  [
  do_outer

  loop
    [
    do_inner
    if test1? [exit outer]
      test2?  [exit]
    ]
  ]
{% endhighlight %}

## This was just a taste...

...so head on over to the [SkookumScript Docs] and gorge yourself upon a veritable buffet of scrumptious SkookumScript syntax! Enjoy!

**Different code, different mode**{: .hdr}<br/>
SkookumScript looks distinctively different from its host language of C++ -- which is a good thing indeed.<br/>
<br/>
Consider, if you will, the noble gameplay developer, who is obliged to endlessly switch back and forth between SkookumScript and the C++ used in the game engine. If the two languages can be differentiated at a glance, it makes it easier for these developer' brains to toggle between "SkookumScript mode" and "C++ mode". On the other hand, if the SkookumScript and C++ code were too similar, these heroic coders could find themselves inadvertently writing SkookumScript code in C++ files and C++ code in SkookumScript files. Which would, needless to say, be bad.
{:.aside}

> A programming language that doesn't change the way you think is not worth learning.
_-- **Alan Perlis**<br>Epigrams on Programming_{:.quoter}


[closure]: /docs/v3.0/lang/literals/closure/ "Manual page for Closures"
[code block]: /docs/v3.0/lang/flow/code-block/ "Code block in Language Reference"
[conditionals]: /docs/v3.0/lang/flow/conditionals/ "Manual page for Conditionals"
[HelloWorld]: http://rosettacode.org/wiki/Hello_world/Text "Hello world examples - RosettaCode"
[Mult-pass]: http://en.wikipedia.org/wiki/Multi-pass_compiler "Multi-pass compiler - Wikipedia"
[Ruby]: http://en.wikipedia.org/wiki/Ruby_(programming_language) "Ruby - Wikipedia"
[SkookumScript Docs]: /docs/
[Smalltalk]: http://en.wikipedia.org/wiki/Smalltalk "Smalltalk - Wikipedia"
