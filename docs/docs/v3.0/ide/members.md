---
layout: page
section: docs
title: Members widget
numbered-headers: true
footer: false
sharing: false
date: 2017-06-21

---

The **Members** widget displays the members for the class currently selected in the [Classes](/docs/v3.0/ide/classes/) widget. The full set of members available to a class include the members added to a class directly and the members inherited from its superclass all the way up to the `Object` root class.

![SkookumIDE Members widget](/images/Docs/SkIDE-Members.png){: .img-center}

The Members widget with the `SkookumDemo` instance default constructor `!()` method selected in the [member list](#member-list). Also note the [**Filters** drop-down list](#filters-drop-down) at the top left, the [**Search Members** box](#search-members-box) in the top right, and the collapsed [New Class or Member](/docs/v3.0/ide/new/) sub-pane at the bottom.
{:.caption}


## Member list

Depending on the class selected in the [Classes](/docs/v3.0/ide/classes/) widget and the state of the [**Filters** drop-down list](#filters-drop-down) and the [**Search Members** box](#search-members-box), the member list will be filled with all the matching members.

The different kinds of class members listed include:

- [data members](/docs/v3.0/lang/identifiers/data-members/)
- [methods](/docs/v3.0/lang/invocations/routines/)
- [coroutines](/docs/v3.0/lang/invocations/routines/)

The member list has the following columns showing info for each member:

- **`c`/`i`** (column 1): indicates whether the member is applicable to a **<em>c</em>**lass or an **<em>i</em>**nstance of a class
- **Name** (column 2: indicates the name of the member
- **Scope** (column 3): indicates the class where the member is specified - either the current class or inherited from a super class
- **Type/Parameters** (column 4): the type or the interface parameters for the member

The bottom of the Members widget is home to the [**New Class or Member** pane](/docs/v3.0/ide/new/).


### Interacting with the Member list

The members in the member list can be interacted with in the following manner:

- **select** a member - loads up the associated script file that defines the member in an [**Editor** tab](/docs/v3.0/ide/editors/) and highlights the overlay where it originated in the [**Overlays** widget](/docs/v3.0/ide/overlays/). If the script file is not already shown in an existing **Editor** tab, it will be shown it in the reusable _preview_ **Editor** (![Eye]) tab.
- **double click** a member - changes the preview tab to a _pinned_ (![Pin]) tab that will remain open even when a new member is selected.
- **right click** a member - brings up a context menu with the following options:
  - **Delete** (shortcut key Del) - deletes the member. [Only enabled for routines.]<br class="mgn_br">
    *NOTE*{:.mark} There is no confirmation or undo so beware! However it uses version control which can be reverted.
  - **Show in Explorer** (shortcut key Ctrl+Shift+E) - opens up the folder that contains the member file using File Explorer and selects the file.

Members are sorted by **Name** (column 2) by default. If you toggle a column title, it will use that column to sort. Multiple toggles of the same column title will alternate the sorting order which is indicated by an upward or downward pointing triangle accordingly.


## "Filters" drop-down

The filters drop-down list specifies the kinds of members to display in the [member list](#member-list). There can be hundreds or even thousands of members listed in the **Members** widget so these filters can help to reduce the members listed to only the ones of interest.

![SkookumIDE Members widget](/images/Docs/SkIDE-Members-Filters.png){: .img-center}

The **Members** widget with the **Filters** drop-down list open and all filters enabled.
{:.caption}

The different filters include:

- **Method**: shows class and instance methods
- **Coroutine**: shows coroutines
- **Data**: shows class and instance data members
- **Inherited**: shows matching members inherited from superclasses

At least one of **Method**, **Coroutine**, or **Data** must be enabled or no member will match and the member list will be empty.


## "Search Members" box

The search members box does a sub-string search of all the members. It lists the matches for the class currently selected in the [**Classes** widget](/docs/v3.0/ide/classes/) first and then matches from all other classes in a slightly darker color so that matching members can be easily discovered even outside the current class.

![SkookumIDE Members widget](/images/Docs/SkIDE-Members-Search.png){: .img-center}

The **Members** widget with "class" entered in the **Search Members** box. Note that the darker matches after `superclass_of?` are from classes other than the currently selected class.
{:.caption}

The search is case insensitive and symbols (including underscores `_`) are ignored.

Note that in addition to the member identifier names being searched, all the `&aka` annotations are also searched. So searching for "GetLife" will match with the `Actor@life_span()` member since it has the annotation `&aka("GetLifeSpan")`.

The `&aka("AlternateName")` annotation is designed for development environments such as Unreal Engine 4 which uses a naming convention different than SkookumScript for Blueprints and the C++ engine identifiers and you may be used to the names in those other systems. It can also just be used for common alternative names so that searches get the results that you expect.
{: .aside}

To clear the **Search Members** box, click the **&#215;** on the right or replace the search text with something else.


[Eye]: /images/Docs/SkIDE-Editors-preview.png
[Pin]: /images/Docs/SkIDE-Editors-pinned.png