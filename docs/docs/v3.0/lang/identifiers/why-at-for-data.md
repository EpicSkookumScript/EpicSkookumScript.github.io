---
layout: page
section: docs
title: Why @ and @@ for data?
sidebar-page: none
footer: false
sharing: false
date: 2017-07-24

---

_**(Backgrounder from [Conan Reis](/about/team/#conan-reis))**_

SkookumScript prefixes its data members with `@` and `@@`, though why is this so?

Being able to visually differentiate data members, class data members and temporary variables (including parameter names from routines) can be really useful. IDEs and other coding editors that know a language _could_ be sophisticated enough to highlight these different categories of variables with different colors, fonts, etc. though we often cut and paste code outside the IDE which would not have this highlighting. Lexically differentiating variables also helps reduce name collisions.

For many years I worked on projects that simply used naming conventions for data members. Since the naming was never _enforced_ by the compiler, people broke the conventions _all the time_. Even worse, naming conventions were frequently used in the _wrong_ circumstances such as making it seem that a class data member was actually an instance data member or vice versa.

The solution is to have the compiler enforce a naming convention.

In my experience, people dislike parser enforced naming conventions if they are standard identifier characters (such as `m_`) whereas non-identifier symbol characters are more readily accepted.

I also did not want to enforce a full word in their declaration like `static` as is used in C++ to denote class data members. The creator of C++, Bjarne Stroustrup, used `static` because he didn't want to introduce another reserved word. He later regretted it since it muddied the usage of `static` in other areas and it was an arbitrary word for the concept and not using conventional object-oriented terminology.

So which symbols?

SkookumScript already used `@` for its scope resolution operator for routines.

A scope resolution operator is generally only used when you want to call an overridden version of a superclass routine from a subclass. So if you are in the `do_stuff` method in `ClassB` and you want to call the `do_stuff` method from `ClassA` you call it with `ClassA@do_stuff`. Otherwise calling `do_stuff()` without the scope resolution operator with the `do_stuff()` method will recursively call itself. _(The scope operator in C\+\+ is `::`.)_
{:.aside}

The `@` symbol also has the nice connotation that it is called "at". So `ClassA@do_stuff()` is read as "Class A _at_ do stuff". This fits in a _location_ or _address_ kind of way.

The "at" aspect of `@` makes a lot of sense so I thought about using `@` for data members plus a member accessor dot to differentiate from methods. So `object.@data` is read as "object _at_ data".

I don't like to arbitrarily choose syntax when there is pre-existing language history and convention to choose from - even if it may not seem like it at times in SkookumScript. Of course it occurred to me that [the Ruby programming langauge](http://ruby-doc.com/docs/ProgrammingRuby/html/tut_classes.html) also used `@` and `@@` for its data member naming. So I went with that since there is some history to draw on and people in the Ruby community seem to like it.

So that is how SkookumScript ended up using `@` and `@@` for data members.


---
**← Return to [Data members](/docs/v3.0/lang/identifiers/data-members)**
{:.bubble-link}



