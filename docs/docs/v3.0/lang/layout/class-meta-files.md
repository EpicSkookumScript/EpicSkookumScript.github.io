---
layout: page
section: docs
title: Class meta files
sidebar-page: none
footer: false
sharing: false
date: 2014-04-03

---

<div class="table-wrap" markdown="block">
| Meta&nbsp;Files<span class="pad_r2"></span>
|:-|-:|:-
| *class-meta-filename*{:#class-meta-filename} | = | !Class.sk-meta
| *class-meta-file*{:#class-meta-file}         | = | *[ws]* {*meta-name* ':' *[ws]* *value* *[ws]*}
| *meta-name*{:#meta-name}                     | = | `demand_load`<!-- \| `object_id_lookup` \| `object_id_validate`-->

</div>

Each SkookumScript class can have a `!Class.sk-meta` file that specifies various settings and properties for the class. A class meta file is located in the same directory (folder) that represents the class.

<div class="table-wrap" markdown="block">
| Meta&nbsp;Name      |   | Possible Values
|:-|-:|:-
| demand_load         | = | `true` \| `false`

</div>

<!--
| object_id_lookup    | = | `true` \| `false`
| object_id_validate  | = | `none` \| `any` \| `parse` \| `exist` \| `defer`
-->

Here is a further detailing of the values and what they mean for the class:

{: .list-brkt}
- `demand_load:`{:#demand_load}
  - `true` -- This class is "demand loaded" and any subclasses are saved in a separate compiled runtime structures binary that can be loaded and unloaded as needed. By default the class is not loaded at SkookumScript initialization. This is generally to ensure that info for a class and its subclasses do not take up memory when they are not needed. This can also be used for code that you want to compile though you aren't using it yet, etc.<br/>For more information see [Demand Script Loading].
  - `false` -- This class is "static loaded" so it is loaded at SkookumScript initialization and always available.

  
[alphanumeric]: /docs/v3.0/lang/syntax/#alphanumeric
[character]: /docs/v3.0/lang/syntax/#character
[class-name]: #class-name
[Demand Script Loading]: /docs/v3.0/rt/demand-loading/ "More info on Demand Script Loading"
[end-of-line]: /docs/v3.0/lang/syntax/#end-of-line
[Object Id Files]: /docs/v3.0/lang/layout/object-id-files/
[Object Id Identifiers]: /docs/v3.0/lang/identifiers/object-ids/
[symbol-literal]: #symbol-literal
[raw-object-id]: #raw-object-id
[uppercase]: /docs/v3.0/lang/syntax/#uppercase
[ws]: /docs/v3.0/lang/whitespace/

