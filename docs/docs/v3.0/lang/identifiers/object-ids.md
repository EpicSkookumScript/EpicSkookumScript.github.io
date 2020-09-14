---
layout: page
section: docs
title: Object IDs
numbered-headers: true
footer: false
sharing: false
date: 2017-07-01

---

<div class="table-wrap" markdown="block">
| *object-id*{:#object-id}[^object-id]        | = | \[*[class-name]*\] '`@`' \['`?`' \| '`#`'\] *[symbol-literal]*
| *class-name*{:#class-name}                  | = | *[uppercase]* {*[alphanumeric]*}
| *symbol-literal*{:#symbol-literal}          | = | '`'`' {*[character]*}<sup>0-255</sup> '`'`'

</div>

[^object-id]: If *[class-name]* absent `Actor` inferred. Optional '`?`' indicates result may be `nil` -- if question mark not used and object not found at runtime then assertion error occurs. Optional hash sign '`#`' indicates it is a symbol literal validated by class type.

Object IDs are a feature unique to SkookumScript -- they allow game / simulation objects, concepts and assets to be referred to by class type and name in code.

Object IDs can be used for game characters, trigger regions, sound effects, user interface elements, mission names, cars, cutscenes, props, doors, geographical locations, art assets, game events, AI / behaviour types, animations or *anything* that you can associate a name to.

Classes that use object IDs  must have the appropriate settings in their [class meta file](/docs/v3.0/lang/layout/class-meta-files/) and a `object_id_find()` method that can be called to do object lookup.

All `Actor` objects have object IDs enabled and by default look them up by name using the `Actor@object_id_find()` method.


## Using Object IDs in Code 
{:#using}

Every object ID is associated with a SkookumScript class type. If the class type is not specified then the `Actor` class is inferred.

Object IDs have several forms:

- **[Reference @](#reference)**: refers to the named object
- **[Potential reference @?](#potential-reference)**: refers to the named object or `nil` if not found
- **[Identifier @#](#identifier)**: identifier name of the object in the type most appropriate for the runtime
 
<div markdown="1" class="focus">
#### Object IDs Cache References to Objects

If a reference or potential reference form of an object ID is evaluated, it caches the reference of the object (using a memory smart pointer) and will quickly return the same object on successive calls if the object is still valid. It will only look up the object by name again if the previous object goes stale and is removed for some reason.

This means that they can be more speed efficient than a routine call that does a look-up each time it is evaluated.
</div>


### Reference @
{:#reference}

The reference form of an object ID uses an "at" symbol `@`. It returns a reference to the named object and will assert if the named object is not present when the object ID is evaluated. Its result class type is the same as the class doing the named object lookup. So `Mission@'crazy_space_chase'` will have a result class type of `Mission`.

{% highlight js %}
// Actor is inferred
@'SomeGuy'.do_stuff

// Same as above
Actor@'SomeGuy'.do_stuff

// Similar to above though in method
// form and result not cached
Actor.named("SomeGuy".Name).do_stuff
{% endhighlight %} <!-- _ --> 


### Potential Reference @?
{:#potential-reference}

The potential reference form of an object ID uses an "at" symbol `@` followed by a question mark `?`. It returns a reference to the named object or `nil` if the object is not present when the object ID is evaluated. Its result class type is a union between the object ID class and `None` (the class type for `nil`). So `Trigger@'trap_door'` will have a result class type of `<Trigger|None>`.

{% highlight js %}
// Actor is inferred so <Actor|None> is result type
@?'SomeGuy'

// Same as above
Actor@?'SomeGuy'

// Similar to above though in method
// form and result not cached
Actor.named("SomeGuy".Name)


// Generally need to account for possibility of nil
!guy: @?'SomeGuy'
guy.do_stuff unless guy.nil?

// [or] Use apply operator % to ignore call if receiver is nil
@?'SomeGuy'%do_stuff
{% endhighlight %}


### Identifier @#
{:#identifier}

The identifier form of an object ID is essentially the same as a common identifier type of the engine being used (`Name` in UE4 or `FName` in UE4 C++). It uses an "at" symbol `@` followed by a hash sign `#`. It returns a `Symbol`. It is useful to use in code that need to reference the name of an object and do not need the object itself.

{% highlight js %}
// Actor is inferred and engine identifier type is result
@#'SomeGuy'

// Same as above
Actor@#'SomeGuy'

// Similar to above
"SomeGuy".Name

// Can be used with methods that need the name of an object
my_mission.set_smart_mouth(Robot@#'Marvin')
{% endhighlight %} <!-- _ -->


<div class="footline" id="footline"></div>


[alphanumeric]: /docs/v3.0/lang/syntax/#alphanumeric
[class-name]: #class-name
[character]: /docs/v3.0/lang/syntax/#character
[meta file]: /docs/v3.0/lang/layout/class-meta-files/
[object-id]: #object-id
[object id validation files]: /docs/v3.0/lang/layout/object-id-files/
[symbol]: /docs/v3.0/lang/syntax/#symbol-literal
[symbol-literal]: #symbol-literal
[SkUE4]: /docs/integrations/ue4plugin/ "SkookumScript Unreal Engine 4 plugin"
[uppercase]: /docs/v3.0/lang/syntax/#uppercase
