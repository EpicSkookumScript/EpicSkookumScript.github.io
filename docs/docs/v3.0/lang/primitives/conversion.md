---
layout: page
section: docs
title: Conversion
sidebar-page: none
footer: false
sharing: false

---

<div class="table-wrap" markdown="block">
| *class-conversion*{:#class-conversion}[^conversion]  | = | *[expression]* *[ws]* '`>>`' \[*[class-name]*\]
| *class-name*{:#class-name}                           | = | *[uppercase]* {*[alphanumeric]*}

</div>

[^conversion]: Explicit conversion to specified class. *[class-name]* optional if desired type inferable. Ex: `42>>String` calls conversion method `Integer@String()` i.e. `42.String()` - whereas `"hello">>String` generates no extra code and is equivalent to `"hello"`.

Learn about [class conversion `>>` in the Primer](/docs/v3.0/#class-conversion).


<div class="footline" id="footline"></div>


[alphanumeric]: /docs/v3.0/lang/syntax/#alphanumeric
[class-name]: #class-name
[class-conversion]: #class-conversion
[expression]: /docs/v3.0/lang/expressions/
[ws]: /docs/v3.0/lang/whitespace/
[uppercase]: /docs/v3.0/lang/syntax/#uppercase
