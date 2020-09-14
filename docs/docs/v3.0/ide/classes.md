---
layout: page
section: docs
title: Classes widget
footer: false
sharing: false
date: 2017-06-30

---

The **Classes** widget lists the class hierarchy of all the SkookumScript classes, starting with the root `Object` class, then its subclasses, their subclasses and so on.

![SkookumIDE Classes widget](/images/Docs/SkIDE-Classes.png){: .img-center}

The **Classes** widget with the `SkookumDemo` class selected. Note that `SkookumDemo` is indented below `Master` -- this indicates that it is a subclass of `Master`.
{:.caption}

To create new classes or add members to classes use the [**New Class or Member** pane](/docs/v3.0/ide/new/).


### Interacting with classes

When you select a class, the [**Members** widget](/docs/v3.0/ide/members/) lists the class's data members, methods and coroutines. It also sets the working class for the [**New Class or Member** pane](/docs/v3.0/ide/new/).

If you **right click** on a class it brings up a context menu with options **Show in Explorer** or **Copy Path to Clipboard**. Since a class can be in more than one [overlay](/docs/v3.0/lang/layout/overlays/), both options will list each overlay the class is in. It will also show a mouse hover hint with the folder location on the file system. These are handy as an _escape hatch_ so you can manipulate SkookumScript files directly with other software.

![SkookumIDE Classes widget](/images/Docs/SkIDE-Classes-context-menu.png){: .img-center}

Context menu on `Mind` class.
{:.caption}


### Searching and Filtering

To selectively filter classes that match a particular sub-string, enter a sub-string to search for in the **Search Classes** box at the top of the widget.

![SkookumIDE Classes widget](/images/Docs/SkIDE-Classes-search.png){: .img-center}

When "Pawn" is entered into the **Search Classes** box, only classes including the sub-string "Pawn" (and their superclasses) are displayed.
{:.caption}

To clear the **Search Classes** box, click the **&#215;** on the right.

