---
layout: page
section: docs
title: Comments
footer: false
sharing: false
date: 2016-02-03

---

<div class="table-wrap" markdown="block">
| *comment*{:#comment}                  | = | *[single-comment]* \| *[multi-comment]*
| *single-comment*{:#single-comment}    | = | '`//`' {`printable`} *[end-of-line]*
| *multi-comment*{:#multi-comment}      | = | '`/*`' {`printable`} \[*[multi-comment]* {`printable`}\] '`*/`'
| *end-of-line*{:#end-of-line}          | = | `newline` \| `carriage-return` \| `end-of-file`

</div>

Comments are blocks of text that are used as code documentation and are ignored by the SkookumScript parser which considers them to be no more than [whitespace][ws]. While the computer ignores them, comments are essential for us humans to make notes in code to other users or as an aid to memory to your future self. You can also use comments to have the parser skip over code that you don't want to be present in the runtime though you want to keep it around for reference.

Comments are ignored by the compiler and written to help programmers to better understand the code. Comments in SkookumScript are very similar to those in [C++] except that multi-line comments in SkookumScript can be *nested* inside one another.

<figure class="code"><figcaption><span>Comment Examples</span></figcaption><div class="highlight"><table><tr><td class="gutter"><pre class="line-numbers"><span class="line-number">1</span>
<span class="line-number">2</span>
<span class="line-number">3</span>
<span class="line-number">4</span>
<span class="line-number">5</span>
<span class="line-number">6</span>
<span class="line-number">7</span>
<span class="line-number">8</span>
<span class="line-number">9</span>
<span class="line-number">10</span>
<span class="line-number">11</span>
<span class="line-number">12</span>
<span class="line-number">13</span>
<span class="line-number">14</span>
<span class="line-number">15</span>
<span class="line-number">16</span>
<span class="line-number">17</span>
<span class="line-number">18</span>
<span class="line-number">19</span>
<span class="line-number">20</span>
<span class="line-number">21</span>
<span class="line-number">22</span>
<span class="line-number">23</span>
<span class="line-number">24</span>
<span class="line-number">25</span>
<span class="line-number">26</span>
<span class="line-number">27</span>
<span class="line-number">28</span>
<span class="line-number">29</span>
<span class="line-number">30</span>
<span class="line-number">31</span>
</pre></td><td class="code"><pre><code class="cpp"><span class="line"><span class="c1">// This is an example of a single line comment.</span>
</span><span class="line"><span class="c1">// It continues from its start until the end of the line -&gt;</span>
</span><span class="line"><span class="n">do_this</span>
</span><span class="line">
</span><span class="line"><span class="c1">// It can be on its own line</span>
</span><span class="line"><span class="n">do_that</span>  <span class="c1">// or at the end of other code</span>
</span><span class="line">
</span><span class="line"><span class="n">some_code</span>
</span><span class="line">
</span><span class="line"><span class="cm">/* This is an example of a multi-line comment.</span>
</span><span class="line"><span class="cm">   It can be a single line, multiple lines or used</span>
</span><span class="line"><span class="cm">   in the middle of code just like other whitespace. */</span>
</span><span class="line">
</span><span class="line"><span class="k">if</span> <span class="cm">/*like this*/</span> <span class="n">test</span>
</span><span class="line">  <span class="p">[</span>
</span><span class="line">  <span class="n">do_this</span>
</span><span class="line">  <span class="n">do_that</span>
</span><span class="line">  <span class="p">]</span>
</span><span class="line">
</span><span class="line"><span class="cm">/* [B1] Multi-line comments</span>
</span><span class="line"><span class="cm">do_this</span>
</span><span class="line">
</span><span class="line"><span class="cm">  /* [B2] can nest other comment blocks</span>
</span><span class="line"><span class="cm">  do_that</span>
</span><span class="line"><span class="cm">  do_stuff // Including single line comments</span>
</span><span class="line"><span class="cm">  */  // end of [B2]</span>
</span><span class="line">
</span><span class="line"><span class="cm">do_other</span>
</span><span class="line"><span class="cm">*/  // end of [B1]</span>
</span><span class="line">
</span><span class="line"><span class="n">do_end</span>
</span></code></pre></td></tr></table></div></figure>


[C++]: https://en.wikipedia.org/wiki/C%2B%2B "C++ - Wikipedia"
[comment]: #comment
[end-of-line]: #end-of-line
[multi-comment]: #multi-comment
[single-comment]: #single-comment
[ws]: /docs/v3.0/lang/whitespace/
