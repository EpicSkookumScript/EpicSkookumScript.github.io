---
layout: page
section: docs
title: Overlays
numbered-headers: true
footer: false
sharing: false
date: 2017-07-27

---

## Overlays are similar to libraries

Overlays serve a function similar to that of code libraries in other languages, namely collecting and encapsulating code in a particular category or domain and making it easy add and remove these collections of code as a group to projects.

However, all SkookumScript overlays are essentially _open_ and build successively on top of one another starting with the `Core` overlay. They are somewhat analogous to layers in a graphic image editing program where each layer has some new visible content and also covers some content of earlier layers. Similar to image layers, each overlay can add more content which can be entirely new or it may also supersede content from a previous overlay. All the overlays for a project are flattened together and the resulting _visibile_ content is the code base used for a SkookumScript project.

Related coding constructs include:

- [_overriding_](https://en.wikipedia.org/wiki/Method_overriding) which has routines inherited from a superclass superseded with same named alternate routines in a subclass. Overriding is also supported in SkookumScript.
- [_overloading_](https://en.wikipedia.org/wiki/Function_overloading) which has routines with the same name though with different parameters. Overloading is intentionally _not_ supported in SkookumScript.

SkookumScript overlays add the construct of _overlaying_ whole libraries to add and supersede collections of code over the earlier overlays.

Each overlay has a _rank_ and overlays are applied in rank order. So code in a rank 1 overlay is added first, then the rank 2 overlay goes over top of that, then the rank 3 overlay on top of that, and so on. The `Core` overlay is always rank 1 - it has all the standard SkookumScript classes and routines such as `Object`, `String`, `Integer`, `Boolean`, `List` and `Mind`.

The current overlays for a project can be viewed in the SkookumIDE in the [**Overlays** widget](/docs/v3.0/ide/overlays/).

![SkookumIDE Overlays widget](/images/Docs/SkIDE-Overlays.png){: .img-center}

The [**Overlays** widget](/docs/v3.0/ide/overlays/). Disabled overlays are in a darker font and the overlay of the currently selected member has its line highlighted.
{:.caption}

Whenever you use the [**New Class or Member** pane](/docs/v3.0/ide/new/) in the [**Members** widget](/docs/v3.0/ide/members/) you must specify the overlay that new classes and members belong to.

As you are looking at or editing script files, the **Overlays** widget will highlight the overlay location of the current member.


## Overlay files

Overlays are specified in the _`MyProject`_`\Scripts\Skookum-project.ini` project settings file. The default overlays are usually sufficient for most projects.

*TIP*{:.tip} The current SkookumIDE doesn't have a dialog to modify overlays _yet_ -- so overlay settings are currently modified by hand.

Example overlay section from the "SkookumDemo" project:

```ini
[Script Overlays]
Overlay1=*Core|Core\
Overlay2=-*Core-Sandbox|Core-Sandbox\
Overlay3=*VectorMath|VectorMath\
Overlay4=*Engine-Generated|Engine-Generated\|A
Overlay5=*Engine|Engine\
Overlay6=*Project-Generated|Project-Generated\|C
Overlay7=SkookumDemo|Project\
```

<div markdown="1" class="focus">

### Notes on the project file overlay format

- The overlays are applied in increasing order so `Overlay5` (the `Engine` overlay above) will replace matches in `Overlay4` (the `Engine-Generated` overlay above).
- There can be no gap in the overlay rank numbers.
- The first section (delimited with `|`) in an overlay entry is the name of the overlay. (Examples from above include: `Core`, `VectorMath`, `Engine`.)
- Overlays that start with a minus `-` (such as `Core-Sandbox` above) are disabled - i.e. they are essentially _commented out_.
- Overlays that start with an asterisk `*` (such as `Core` and `Engine` above) are set to be _read-only_. (This is done in the example above since those overlays are either generated or come from the SkookumScript team.) Overlays without an asterisk are editable using the SkookumIDE. You can of course remove the asterisk and edit layers such as `Core` if you want to modify them to contribute scripts back to other teams using SkookumScript. We recommend making your own custom overlays (such as `Core-Extras` just after `Core`) and just make changes in them and you can send such mini overlays that the SkookumScript team can then integrate into common overlays on request.
- The second section in an overlay entry is the file path where the script files for the overlay are located. If it is a relative path, it is relative _to this `.ini` file_.
- The third section in an overlay indicates either:
  - no special layout (default - such as `Core` and `VectorMath` above) -- has the folder layout mirror the class hierarchy with subclasses as subfolders of their superclass folder and there are separate files for class and instance data and each routine.
  - `|#` a particular folder depth (not shown) -- similar to the default layout, though some OSes _still_ limit the max number of characters in folders so this ensures that no folder will go over that limit.
  - `|C` generated and non-editable _per **class** archive_ files (such as `Project-Generated` above) -- all the details for each class are stored in files named akin to `SubClass.SuperClass.sk`.
  - `|A` generated and non-editable _per overlay **archive**_ files (such as `Engine-Generated` above) -- all the details for an entire overlay are stored in a single archive file named `!Overlay.sk`.
</div>

Any changes to the project overlays should be made while the game engine and SkookumIDE do not have the project loaded or they are not running at all. Then reload the project or rerun the engine and SkookumIDE to take up the changes.  
