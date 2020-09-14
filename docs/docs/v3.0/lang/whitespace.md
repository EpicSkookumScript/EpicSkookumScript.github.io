---
layout: page
section: docs
title: Whitespace
footer: false
sharing: false
date: 2016-02-03

---

<div class="table-wrap" markdown="block">
| *wsr*{:#wsr}[^wsr]                    | = | {*[whitespace]*}<sup>1+</sup>
| *ws*{:#ws}                            | = | {*[whitespace]*}
| *whitespace*{:#whitespace}            | = | *[whitespace-char]* \| *[comment]*
| *whitespace-char*{:#whitespace-char}  | = | '&nbsp;' \| `formfeed` \| `newline` \| `carriage-return` \| `horiz-tab` \| `vert-tab`
| *end-of-line*{:#end-of-line}          | = | `newline` \| `carriage-return` \| `end-of-file`

</div>

[^wsr]: *[wsr]* is an abbreviation for (w)hite (s)pace (r)equired.

Whitespace (non-printing or invisible characters) and [comments][comment] are used liberally throughout SkookumScript code to separate coding elements, increase readability and to give additional explanation and description.

<div class="footline" id="footline"></div>


[wsr]: #wsr
[ws]: #ws
[whitespace]: #whitespace
[whitespace-char]: #whitespace-char
[end-of-line]: #end-of-line
[comment]: /docs/v3.0/lang/comments/
