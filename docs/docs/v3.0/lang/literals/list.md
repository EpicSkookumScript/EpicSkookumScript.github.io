---
layout: page
section: docs
title: List
numbered-headers: true
footer: false
sharing: false

---

## Quick reference

<div class="table-wrap" markdown="block">
| *list-literal*{:#list-literal}[^list]       | = | \[*[list-class]* *[constructor-name]* *[invocation-args]*\]<br>'<code>{</code>' *[ws]* \[*[expression]* {*[ws]* \['<code>,</code>' *[ws]*\] *[expression]*} *[ws]* '<code>}</code>'
| *list-class*{:#list-class}[^lclass]      | = | `List` '`{`' *[ws]* \[*[class-desc]* *[ws]*\] '`}`'
| *constructor-name*{:#constructor-name}                 | = | '`!`' \[*[instance-name]*\]
| *instance-name*{:#instance-name}                       | = | *[lowercase]* {*[alphanumeric]*}

</div>

[^list]: `List` type specified if the optional *[list-class]* and appropriate *[constructor-name]* is supplied (also see *[instantiation]*). If the type is not supplied, then a type is inferred using the initial items -- if there are no initial items then `Object` used as default item type).
[^lclass]: `List` can be any class derived from `List`. If *[class-desc] in item class descriptor is omitted, `Object` is inferred when used as a type or the item type is deduced when used with a *[list-literal]*. A *[list-class]* of any item type can be passed to a simple untyped `List` class.

Lists are a simple though incredibly powerful construct in SkookumScript to group together objects so they can be treated as a single `List` object. List objects (also sometimes called _collections_ or _arrays_ in other languages depending on their implementation) store zero or more objects referred to as _items_ in an ordered, indexable group that can dynamically change in length. The same item can be in several positions in the same list.

Lists have two class types associated with them:

- *class of the list itself* This is `List` or a subclass. If the list class is not specified then `List` is inferred.
- *class of the list item(s)* If it is not specified and there are no initial items then `Object` is used since it is a match for any type of an item. If initial items are present then the parser uses their types to infer the overall item type for a list. Though a list can have many items and each can have a different class type, the parser only tracks one item type for all of a list's items. If the items in a list need to be more than one class type then either the item type needs to be a superclass of all the item types or it needs to be a union type of all the item classes that are possible for the list - for example: `<ItemType1|ItemType2|ItemType3>`.


## List initialization

A _list literal_ makes a `List` object with a series of [expressions][expression] with curly brackets `{` `}` (also known as _braces_) marking the beginning and the ending of the list. Items are separated by [whitespace][ws]. You can alternatively separate items with a comma `,` though they are optional (just as they are with routine arguments) and should only be used if they aid readability.

Each item expression is executed in order, the resulting object has its reference count incremented and then the object is added to the list as an item.

The syntax of list literals can be simple or tricky depending on the type of the list, the type(s) of the items in the list and whether any initial items are present.


### Simple lists - `{}`

Simple list literals have the parser automatically infer all class types being used. The list class is inferred to be `List`. The item class is inferred by examining the items and unioning their types or `Object` if the list is empty.

{% highlight js %}
{}        // List{Object} - empty list
{1 2}     // List(Integer) - 2 items: Integer items inferred
{1 "hi"}  // List{<Integer|String>} - 2 items: union type inferred
{% endhighlight %}


### Item typed list - `ItemType{}`

Item typed list literals specify the item class to use. The item type must not be a `List` or a subclass of a `List`. The list class is inferred to be `List`.

{% highlight js %}
Integer{}     // List{Integer} - empty list
Integer{1 2}  // List{Integer} - 2 items: Integer items
{% endhighlight %}


### List typed list - `ListType!ctor{}`

List typed list literals specify the list class to use. The list class must be a `List` or a subclass of a `List`. The item class is inferred by examining the items and unioning their types or `Object` if the list is empty.

{% highlight js %}
// It isn't that useful to specify the `List` type with the default
// constructor since that is default without specifying it.
List!           // List{Object} - same as {} or List!{}
List!{}         // List{Object} - same as List! or {}
List!{1 2}      // List(Integer)
List!{1 "hi"}   // List{<Integer|String>}

// Create using a named constructor
List!ctor       // List{Object} - empty with special constructor
List!ctor{}     // List{Object} - same as List!ctor{}
List!ctor{1 2}  // List{<Integer|String>} - 2 items w/ special ctor

// The list type can be a custom subclass of List
ListStates!                         // ListStates{Object}
ListStates!{}                       // ListStates{Object}
ListStates!{'state1' 'state2'}      // ListStates{Symbol}
ListStates!ctor{'state1' 'state2'}  // ListStates{Symbol}
{% endhighlight %}

List typed list literals can also use an empty item type specifier to indicate that the item type will be inferred. However it gives the same results as just omitting the item type specifier all together as above which has less typing.

{% highlight js %}
// It isn't that useful to specify the `List` type with the default
// constructor since that is default without specifying it.
List{}!           // List{Object}
List{}!{}         // List{Object}
List{}!{1 2}      // List(Integer)
List{}!{1 "hi"}   // List{<Integer|String>}

// Create using a named constructor
List{}!ctor       // List{Object}
List{}!ctor{}     // List{Object}
List{}!ctor{1 2}  // List{<Integer|String>}

// The list type can be a custom subclass of List
ListStates{}!                         // ListStates{Object}
ListStates{}!{}                       // ListStates{Object}
ListStates{}!{'state1' 'state2'}      // ListStates{Symbol}
ListStates{}!ctor{'state1' 'state2'}  // ListStates{Symbol}
{% endhighlight %}


### Qualified list - `ListType{ItemType}!ctor{}`

Qualified typed list literals specify both the list class and the item class to use. The list class must be a `List` or a subclass of a `List`.

{% highlight js %}
// Create list with Integer item type specified
List{Integer}!                   // Integer{} is easier
List{Integer}!{}                 // Integer{} is easier
List{Integer}!{1 2}              // {1 2} is easier
List{<Integer|String>}!          // List{<Integer|String>} - empty
List{<Integer|String>}!{1 2}     // 2 items, can add String
List{<Integer|String>}!{1 "hi"}  // {1 "hi"} is easier

// List type using custom subclass of List
ListStates{Symbol}!
ListStates{Symbol}!{}  // Same as above

// ListStates!{'state1' 'state2'} is easier than below:
ListStates{Symbol}!{'state1' 'state2'}
{% endhighlight %}


## Using lists

Also make sure to check out the `List!fill()` constructor which, while not a literal, is used in much the same way to programmatically populate a list.

Some `!fill()` examples:

{% highlight js %}
// List with 10 random numbers from 0-99
!nums: List{Integer}!fill 10 [@@random.uniform_int(100)]

// List of squares {0 1 4 9 16 ... 81}
!squares: List{Integer}!fill 10 [idx * idx]
{% endhighlight %}

Look at the `List` class in the SkookumIDE to see all the routines that are available for list objects. The methods that use [closures](/docs/v3.0/lang/literals/closure/) such as `do()` are especially useful and interesting. Most list routines have examples on how to use them in their comments.

Here are some quick examples of using lists:

## List examples
```js
// Reverse the order of the items
{1 2 3 4 5}.reverse

// Applies the method 'negate()' to all items of the list
// and returns the list.
{1 -2 3 -4}%negate

// List is empty so do nothing
{}%negate

// Runs some code - a 'closure' - on each item of the list.
// Same as %negate but can run more than just one method.
{1 -2 3 -4}.do[item.negate]

// `unless` is short for 'if not'
// (Again the closure is the code in the square brackets)
{1 2 3}.do[item++ unless item = 2]

// Keep only items where closure returns true
{3 4 5 8}.select[item.pow2?]

// Keep only items where closure returns false
{3 4 5 8}.reject[item.pow2?]

// Make new list and keep only items where closure returns false
// The ! indicates to make a new copy of the list first.
{3 4 5 8}!reject[item.pow2?]

// Select random item from list
{"A" "B" "C" "D"}.any

// Test if any item from list satisfies a condition.
// - i.e. loop through list until true
{3 4 5}.any?[item.pow2?]

// Test if all items from list satisfy a condition, false here
// - i.e. loop through list until false
{3 4 5}.all?[item.pow2?]

// Same, true in this case
{2 4 8}.all?[item.pow2?]
```

Also note this forum entry on [List item types and `ItemClass_`](https://skookum.chat/t/itemclass-of-list/162).


<div class="footline" id="footline"></div>


[constructor-name]: #constructor-name
[instance-name]: #instance-name
[list-class]: #list-class
[list-literal]: #list-literal

[alphanumeric]: /docs/v3.0/lang/syntax/#alphanumeric
[class-desc]: /docs/v3.0/lang/syntax/#class-desc
[expression]: /docs/v3.0/lang/expressions/
[instantiation]: /docs/v3.0/lang/syntax/#instantiation
[invocation-args]: /docs/v3.0/lang/syntax/#invocation-args
[lowercase]: /docs/v3.0/lang/syntax/#lowercase
[ws]: /docs/v3.0/lang/whitespace/
