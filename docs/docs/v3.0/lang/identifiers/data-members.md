---
layout: page
section: docs
title: Data Members
numbered-headers: true
footer: false
sharing: false
date: 2017-07-25

---

## Quick reference

<div class="table-wrap" markdown="block">
| *data-member*{:#data-member}[^var-id]                  | = | \[*[expression]* *[ws]* '`.`' *[ws]*\] *[data-name]*
| *data-name*{:#data-name}[^data-name]                   | = | '`@`' \| '`@@`' *[variable-name]*
| *variable-name*{:#variable-name}                       | = | *[name-predicate]*
| *name-predicate*{:#name-predicate}[^name-predicate]    | = | *[instance-name]* \['`?`'\]
| *instance-name*{:#instance-name}                       | = | *[lowercase]* {*[alphanumeric]*}

</div>

[^var-id]: Optional *[expression]* can be used to access data member from an object -- if omitted, `this` is inferred.
[^data-name]: '`@`' indicates instance data member and '`@@`' indicates class instance data member.
[^name-predicate]: Optional '`?`' used as convention to indicate predicate variable or method of return type `Boolean` (`true` or `false`).


Both class _instances_ (particular instantiations of classes or simply "objects") and _classes_ (object types) can have members that store data.

Instance data members start with `@` and class data members start with `@@`.

Here is a mental aid to differentiate them:

- [temporary variables](#variable-name) are all at the current scope and do not need any `@`:<br/>`param1`, `obj`, `list`
- [instance data](#instance-data) is one level deep, so use one `@`:<br/>`vector.@x`, `guy.@hit_points`, `@member_data`
- [class data](#class-data) is two levels deep, so use two `@@`:<br/>`BadGuy.@@hit_points_max`, `@@random`, `@@class_data`

For some background history on the naming convention for data members see [Why `@` and `@@` for data?](/docs/v3.0/lang/identifiers/why-at-for-data/).
{:.aside}


## Instance Data

All data members for a class instance ("class instance data members" or just "data members" or "instance data") must start with a single "at" symbol `@`. For example, particular `Enemy` objects (such as `bad_bart` and `mean_mimi`) could store the current hit points in a data member called `@hit_points` or more fully `bad_bart.@hit_points`, `mean_mimi.@hit_points`

Any instance data members are [declared](#data-member-declaration) in a `!Data.sk` file and need to be bound to an object in any object _instance constructor_. Constructors start with an `!` and their files are named `!().sk` or `!`_`ctor_name`_`().sk`. After the instance data is [initialized in a constructor](#initialization-in-constructors) you can access them in other SkookumScript code as needed. The files and their names are managed automatically for you by the SkookumIDE.

- [Declared](#data-member-declaration) in `!Data.sk`:<br class="mgn_br">
  ```Real !@hit_points
  ```
- [Initialized in a constructor](#initialization-in-constructors) such as `!()`:<br class="mgn_br">
  ```@hit_points: 100
  ```
- [Used in code](#using-data-members-in-code):<br class="mgn_br">
  ```@hit_points--
  if @hit_points <= 0
    [die_horrible_death]
  ```

  
## Class data

All data members for a class ("class data members" or just "class data") must start with two "at" symbols `@@`. For example, a maximum amount of hit points for any `Enemy` class could be called `@@hit_point_max` or more fully `Enemy.@@hit_point_max`.

*NOTE*{: .mark} Class instance objects may also access class data members so `mean_mimi.@@hit_point_max` is also valid.

Any class data members are [declared](#data-member-declaration) in a `!DataC.sk` file and need to be bound to an object in the _class constructor_. Class constructors are named `!` and their files are named `!()C.sk`. The `C` in the file indicates that it is for a whole _class_ and not an _instance_ of a class. After the class data is [initialized in a class constructor](#initialization-in-constructors) you can access them in other SkookumScript code as needed. Again, the files and their names are managed automatically for you by the SkookumIDE.

- [Declared](#data-member-declaration) in `!DataC.sk`:<br class="mgn_br">
  ```Real !@@hit_point_max
  ```
- [initialized in class a constructor](#initialization-in-constructors) such as `!()`:<br class="mgn_br">
  ```@@hit_point_max: 100.0
  ```
- [Used in code](#using-data-members-in-code):<br class="mgn_br">
  ```@hit_points : @@random.uniform_range(
    @@hit_point_min @@hit_point_max)
  ```


## Adding new data members

To create new data members [they must be declared](#data-member-declaration) and [initialized in a constructor](#initialization-in-constructors).

The best way to add a new data member is to use the [**New Class or Member**](/docs/v3.0/ide/new/) pane of the [**Members** widget](/docs/v3.0/ide/members/) in the SkookumIDE.

<div markdown="1" class="aside">
### Comparision: C++ Data members
Instance data members starting with `@` in SkookumScript are similar to C++ non-static members. C++ non-static data members often have a naming convention such as start with `m_` for `m`ember. Though again these are just conventions and not enforced by the compiler.<br/>
<br/>
Class data members starting with `@@` in SkookumScript are similar to C++ `static` data members. C++ static data members often have a naming convention such as start with `ms_` for `m`ember `s`tatic. Though these are also just conventions and not enforced by the compiler.
</div>


### Data member declaration

<div class="table-wrap" markdown="block">
| *data-filename*{:#data-filename}[^d-file]              | = | '`!Data`' \['`C`'\] '`.sk`'
| *data-file*{:#data-file}                               | = | *[ws]* \[*[data-definition]* {*[wsr]* *[data-definition]*} *[ws]*\]
| *data-definition*{:#data-definition}[^d-defn]          | = | {*[annotation]* *[ws]*} \[*[class-desc]* *[wsr]*\] '`!`' *[data-name]*
| *annotation*{:#annotation}[^annotation]                | = | '`&`' *[instance-name]*

</div>

[^d-file]: A file name appended with '`C`' indicates that the file describes class members rather than instance members.
[^d-defn]: Optional *[class-desc]* is compiler hint for expected type of member variable. If class omitted, `Object` inferred or `Boolean` if *[data-name]* ends with '`?`'. If *[data-name]* ends with '`?`' and *[class-desc]* is specified it must be `Boolean`.
[^annotation]: The context / file where an *[annotation]* is placed limits which values are valid.

Data members must be declared for a whole class which includes specifying their class type. Multiple data members are declared in the same `!Data.sk` (for _instance_ data) or `!DataC.sk` (for _class_ data).

You can see the [data member file definition](/docs/v3.0/lang/syntax/#data-filename) for both class and instance data members in the SkookumScript syntax.

<!--
- _[expand these out]_
- setting type in data file
- predicates ending with `?`. Predicate data members do not need to specify the `Boolean` type (since `Boolean` is inferred) though if they _do_ specify a type it _must_ be `Boolean`.
- unlike temporary variables can only switch to types that are same or subclass of type specified in data file
- `raw` annotations
- access and data hiding
- additive across overlays
-->


### Initialization in constructors

After data members have been declared they need to bind `:` to an initial object in the appropriate constructor -- an _instance_ constructor for _instance_ data members and the _class_ constructor for _class_ data members. This is called _data member initialization_. All data members must be bound by the end of a constructor or it is considered to be an error. As a safety measure, if an object is not bound to a data member in its appropriate constructor then it is automatically bound to the `nil` object so at least it is bound to _something_ -- though the `nil` object may not match the expected class type of the data member.

<!--
For example, the body of the class constructor `!()C.sk`
-->


## Using data members in code

<!--
_Give examples of using data members..._
-->

### Binding objects and type inference

Since data members can be used in different routines, it is not possible for the SkookumScript parser to infer their class type if it changes just by looking at a particular routine. Data members could be bound `:` to one object type in one routine and a different routine could concurrently change the object type without the parser knowing.

This means that as far as the Parser is concerned the only class type that a data member can be is the type that is specified when it is declared (in its `!Data.sk` or `!DataC.sk` file). The parser restricts rebinding of a data member to object types that are of the same type or a subclass of the type in its declaration.

*NOTE*{: .mark} Temporary variables and parameter variables within a routine or an arbitrary code snippet _can_ have their types inferred by the SkookumScript parser -- all the context is within the one file for the parser to see where and when variables are bound to particular types of objects.
{:.aside}


### Special considerations for `raw` data members

Data members that have the `raw` annotation in their declaration allow non-SkookumScript values created by the runtime (such as Unreal Engine 4 Blueprint variables) to be treated as if they were SkookumScript data members. This is for convenience and aesthetics -- they are more like accessor method calls behind the scenes.

See more detail on [raw data members](https://skookum.chat/t/raw-data-members-how-do-they-work/786/1)


<div class="footline" id="footline"></div>


[alphanumeric]: /docs/v3.0/lang/syntax/#alphanumeric
[annotation]: #annotation
[class-desc]: /docs/v3.0/lang/syntax/#class-desc
[data-definition]: #data-definition
[data-filename]: #data-filename
[data-name]: #data-name
[expression]: /docs/v3.0/lang/expressions/
[instance-name]: #instance-name
[lowercase]: /docs/v3.0/lang/syntax/#lowercase
[name-predicate]: #name-predicate
[var-id]: #var-id
[variable-name]: #variable-name
[ws]: /docs/v3.0/lang/whitespace/
[wsr]: /docs/v3.0/lang/whitespace/
