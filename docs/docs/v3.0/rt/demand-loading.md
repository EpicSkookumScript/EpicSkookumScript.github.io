---
layout: page
section: docs
title: Demand Script Loading
numbered-headers: true
footer: false
sharing: false
date: 2015-06-24

---

_Demand Script Loading_ is a SkookumScript runtime feature that enables the ability to tag a class (and any subclasses) as "demand loaded" so that the runtime can load and unload class groups in the form of pre-compiled script binaries based on game progression or other criteria.

This is great (and possibly a necessity!) when you need to fit a huge open-world game or sprawling massively-multiplayer world into memory. It may also be the case that your platform is a small mobile device and you must squeeze out every byte possible. In all of these cases, Demand Script Loading is a good solution.

## Load one or more classes as needed

Demand Script Loading loads in or out an entire class (including any subclasses) quickly and easily, so scripts are only in memory when they are needed. Game missions that take place at the end of the game won't be loaded at the start of the game. Mission scripts that only take place if the player has a certain vehicle or special inventory won't be loaded until the player has those items. Ambient behaviors that are relative to areas of the world that are far from the player's current location won't be loaded until the player is nearby.

This can also be used for code that you want to compile, though you only use it in special cases such as smoke tests and you don't want it taking up space.

<div markdown="1" class="aside">

### Example demand load statistics: _**Sleeping Dogs**_

To give an idea of demand load classes in action on an actual project, [<em>Sleeping Dogs: Definitive Edition</em>][SDogs] had a limit of 10MB for all 64-bit SkookumScript code and runtime data. The runtime data was approximately 2.5MB in preallocated pools of reusable data structures. This left around 7.5MB for SkookumScript code. However, the entire <em>Sleeping Dogs</em> SkookumScript class hierarchy was 23.5MB!<br/>
<br/>
Due to extensive use of demand loaded classes, only 5MB was permanently loaded and the remaining 2.5MB was available for demand loaded classes to be loaded and unloaded as needed based on game progression, game geography, and other criteria.<br/>
<br/>
This meant that the 35-40 member scripting team could pound out scripts, and they essentially only had to watch memory on a per-mission basis rather than for the entire game at once.
</div>


## Working with _demand loaded_ classes

To specify that a class (and any subclasses) should be saved as a separate demand-loadable binary, in the `!Class.sk-meta` file for a class, set the **demand_load** setting to **true**. For more info, see [Class Meta File][dl_set].

Classes that are set to demand load are saved out as binary files separate from the main SkookumScript class hierarchy binary. Demand load classes are not loaded at SkookumScript initialization by default.

The logic to determine when to load and unload demand load classes is entirely up to your game. There are simple calls to the C++ API to load and unload classes based on the progression of your game, or any other criteria you specify.

You can also pre-emptively stream in script binaries once you know they will soon to be needed, allowing players to seamlessly travel through your world.


[dl_set]: /docs/v3.0/lang/layout/class-meta-files/#demand_load "'demand_load' setting in the class meta file"
[SDogs]: /about/#sleeping-dogs "SkookumScript Showcase: Sleeping Dogs"
