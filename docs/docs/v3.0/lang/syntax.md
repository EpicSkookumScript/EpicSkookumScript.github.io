---
layout: page
section: docs
title: Syntax
sidebar-page: none
footer: false
sharing: false
date: 2015-08-29

---

[Here](#skookumscript-language-specification) are the combined syntactical and lexical rules for the SkookumScript grammar in modified [Extended Backus-Naur Form (EBNF)][EBNF] -- essentially a [cheat sheet](#download_syntax) <!-- _ --> for the language.

EBNF is [by no means a manual][XKCD-manual] - though it is nice to have and some language geeks (such as the [SkookumScript Team](/about/team/)) will appreciate it.

<div markdown="1" class="focus">

## Grammar Key

- Production rules: *in-italics*
- Terminals: `inset-border`
- Literal strings: '`quoted with inset border`'
- Optional groups: \[ \]
- Repeating groups of zero or more: { }
- Repeating groups of n or more: { }<sup>n+</sup>
- Mandatory groups: ( )
- Alternatives: \|
</div>

<div markdown="1" class="aside">
Many programming languages try to keep their grammar __*context free*__ as much as possible so that later code does not need to depend on earlier code -- this makes it easier to write a compiler. SkookumScript is the opposite -- its grammar is __*context rich*__ and tries to have the compiler figure out things as you would sensibly expect.

This means that many production rules cannot be simply described with standard EBNF -- and in those cases a footnote[^example] is used after the name of a *production-rule* to describe additional details for how the grammar works depending on the context.
</div>

[^example]: Here is an example footnote.


## SkookumScript Language Specification

<div class="table-wrap" markdown="block">
| [Expressions](#Expressions){:#Expressions}
|:-|-:|:-
| *[expression][man_expression]*{:#expression}  | = | *[literal]* \| *[identifier]* \| *[variable-primitive]* \| *[invocation]* \| *[type-primitive]* \| *[flow-control]*

</div>


<div class="table-wrap" markdown="block">
| [Literals](#Literals){:#Literals .pad_r3}
|:-|-:|:-
| *literal*{:#literal}                        | = | *[boolean-literal]* \| *[integer-literal]* \| *[real-literal]* \| *[string-literal]* \| *[symbol-literal]* \| *[char-literal]* \| *[list-literal]* \| *[closure]*
| *boolean-literal*{:#boolean-literal}        | = | '`true`' \| '`false`'
| *integer-literal*{:#integer-literal}[^int]  | = | *[simple-integer]* \['`r`' {*[big-digit]*}<sup>1+</sup>
| *simple-integer*{:#simple-integer}[^s-int]  | = | ['`-`'] *[digits]*
| *real-literal*{:#real-literal}[^real]       | = | *[simple-integer]* \['`.`' {*[digit]*}<sup>1+</sup>\] \[*[real-exponent]*\]
| *real-exponent*{:#real-exponent}            | = | '`E`' \| '`e`' *[simple-integer]*
| *string-literal*{:#string-literal}          | = | *[simple-string]* {*[ws]* '`+`' *[ws]* *[simple-string]*}
| *simple-string*{:#simple-string}            | = | '`"`' {*[character]*} '`"`'
| *symbol-literal*{:#symbol-literal}          | = | '`'`' {*[character]*}<sup>0-255</sup> '`'`'
| *character-literal*{:#character-literal}    | = | '<code>\`</code>' *[character]*
| *list-literal*{:#list-literal}[^list]       | = | \[*[list-class]* *[constructor-name]* *[invocation-args]*\]<br>'<code>{</code>' *[ws]* \[*[expression]* {*[ws]* \['<code>,</code>' *[ws]*\] *[expression]*} *[ws]* '<code>}</code>'
| *[closure][man_closure]*{:#closure}[^closure]  | = | \['`^`' {*[annotation]* *[ws]*} \['`_`' *[ws]*\] \[*[expression]* *[ws]*\]\] \[*[parameters]* *[ws]*\] *[code-block]*

</div>

<!--| *range-literal*{:#range-literal}            | = | \[*[expression]*\] '`..`' \[*[expression]*\] \| ('`#`' *[expression]*) -->

[^int]: '`r`' indicates (r)adix / base -- default 10 (decimal) if omitted. Ex: `2r` binary & `16r` hex. *[big-digit]*(s) vary by the radix used.
[^s-int]: Negative *[simple-integer]* can be confused with subtract *[math-operator]*.
[^real]: Decimal part of *[real-literal]* is optional if `Real` type can be inferred from context or if the exponent part is present.
[^list]: `List` type specified if the optional *[list-class]* and appropriate *[constructor-name]* is supplied (also see *[instantiation]*). If the type is not supplied, then a type is inferred using the initial items -- if there are no initial items then `Object` used as default item type).
[^closure]: \[Also known as: code block, anonymous function or lambda expression.\]  Optional '`^`' or *[parameters]* or both must be provided (unless used in *[closure-tail-args]* where both are optional). Optional *[expression]* (which may not be *[code-block]* or *[closure]*) will be captured and used as receiver/this for the *[code-block]* -- if not provided `this` is inferred. Optional '`_`' indicates it is durational (like a coroutine) -- if not present durational/immediate inferred via *[code-block]*. Parameter types, return type, scope, whether surrounding `this` or temporary/parameter variables are used and captured may all be inferred if omitted.


<div class="table-wrap" markdown="block">
| [Identifiers](#Identifiers){:#Identifiers .pad_r2}
|:-|-:|:-
| *identifier*{:#identifier}[^identifier]                | = | *[variable-identifier]* \| *[reserved-identifier]* \| *[class-name]* \| *[object-id]*
| *variable-identifier*{:#variable-identifier}[^var-id]  | = | *[variable-name]* \| (\[*[expression]* *[ws]* '`.`' *[ws]*\] *[data-name]*)
| *instance-name*{:#instance-name}                       | = | *[lowercase]* {*[alphanumeric]*}
| *variable-name*{:#variable-name}                       | = | *[name-predicate]*
| *data-name*{:#data-name}[^data-name]                   | = | '`@`' \| '`@@`' *[variable-name]*
| *reserved-identifier*{:#reserved-identifier}           | = | '`nil`' \| '`this`' \| '`this_class`' \| '`this_code`' \| '`this_mind`'
| *object-id*{:#object-id}[^object-id]                   | = | \[*[class-name]*\] '`@`' \['`?`' \| '`#`'\] *[symbol-literal]*
| *class-name*{:#class-name}                             | = | *[uppercase]* {*[alphanumeric]*}
| *routine-name*{:#routine-name}                         | = | *[method-name]* \| *[coroutine-name]*
| *method-name*{:#method-name}[^method-name]             | = | *[name-predicate]* \| *[constructor-name]* \| *[destructor-name]* \| *[class-name]*
| *name-predicate*{:#name-predicate}[^name-predicate]    | = | *[instance-name]* \['`?`'\]
| *constructor-name*{:#constructor-name}                 | = | '`!`' \[*[instance-name]*\]
| *destructor-name*{:#destructor-name}[^dtor-name]       | = | '`!!`'
| *coroutine-name*{:#coroutine-name}                     | = | '`_`' *[instance-name]*

</div>

[^identifier]: Note that scoping is not necessary -- instance names may not be overridden and classes and implicit identifiers effectively have global scope.
[^var-id]: Optional *[expression]* can be used to access data member from an object -- if omitted, `this` is inferred.
[^data-name]: '`@`' indicates instance data member and '`@@`' indicates class instance data member.
[^object-id]: If *[class-name]* absent `Actor` inferred or desired type if known. If optional '`?`' is present and object not found at runtime then result is `nil` else assertion error occurs. Optional hash mark '`#`' indicates no lookup - just return name identifier validated by class type.
[^method-name]: A method using *[class-name]* allows explicit conversion similar to *[class-conversion]* except that the method is always called.
[^name-predicate]: Optional '`?`' used as convention to indicate predicate variable or method of return type `Boolean` (`true` or `false`).
[^dtor-name]: Destructor calls are only valid in the scope of another destructor's *[code-block]*.


<div class="table-wrap" markdown="block">
| [Variable Primitives](#var-primitives){:#var-primitives .pad_r2}
|:-|-:|:-
| *variable-primitive*{:#variable-primitive}           | = | *[create-temporary]* \| *[bind]*
| *create-temporary*{:#create-temporary}[^temp]        | = | *[define-temporary]* \[*[ws]* *[binding]*\]
| *define-temporary*{:#define-temporary}               | = | '`!`' *[ws]* *[variable-name]*
| *bind*{:#bind}[^bind]                                | = | *[variable-identifier]* *[ws]*  *[binding]*
| *binding*{:#binding}                                 | = | '`:`' *[ws]* *[expression]*

</div>

[^temp]: Only valid in the scope of a *[code-block]*.
[^bind]: May not be used as an argument. Only a *[named-spec]* is valid as an argument which looks similar.


<div class="table-wrap" markdown="block">
| [Invocations](#Invocations){:#Invocations .pad_r2}
|:-|-:|:-
| *invocation*{:#invocation}                           | = | *[invoke-call]* \| *[instantiation]* \| *[invoke-cascade]* \| *[invoke-operator]* \| *[index-operator]* \| *[apply-operator]*
| *invoke-call*{:#invoke-call}[^call]                  | = | (\[*[expression]* *[ws]* '`.`' *[ws]*\] *[invoke-selector]*) \| *[operator-call]*
| *instantiation*{:#instantiation}[^instant]           | = | \[*[class-instance]*\] \| *[expression]* '`!`' \[*[instance-name]*\] *[invocation-args]*
| *invoke-cascade*{:#invoke-cascade}                   | = | *[expression]* *[ws]* '`.`' *[ws]* '`[`' {*[ws]* *[invoke-selector]* \| *[operator-selector]*}<sup>2+</sup> *[ws]* '`]`'
| *invoke-operator*{:#invoke-operator}[^i-op]          | = | *[expression]* *[bracketed-args]*
| *index-operator*{:#index-operator}[^idx-op]          | = | *[expression]* '`{`' *[ws]* *[expression]* *[ws]* '`}`' \[*[ws]* *[binding]*]
| *apply-operator*{:#apply-operator}[^apply]           | = | *[expression]* *[ws]* '`%`' \| '`%>`' *[invoke-selector]*
| *invoke-selector*{:#invoke-selector}                 | = | \[*[scope]*\] *[routine-name]* *[invocation-args]*
| *scope*{:#scope}                                     | = | *[class-name]* '`@`'  
| *operator-call*{:#operator-call}[^op-call]           | = | (*[prefix-operator]* *[ws]* *[expression]*) \| (*[expression]* *[ws]* *[operator-selector]*)
| *operator-selector*{:#operator-selector}             | = | *[postfix-operator]* \| (*[binary-operator]* *[ws]* *[expression]*)
| *binary-operator*{:#binary-operator}                 | = | *[math-operator]* \| *[compare-op]* \| *[logical-operator]* \| '`:=`'
| *math-operator*{:#math-operator}[^math-op]           | = | '`+`' \| '`+=`' \| '`-`' \| '`-=`' \| '`*`' \| '`*=`' \| '`/`' \| '`/=`'
| *compare-op*{:#compare-op}                           | = | '`=`' \| '`~=`' \| '`>`' \| '`>=`' \| '`<`' \| '`<=`'
| *logical-operator*{:#logical-operator}               | = | '`and`' \| '`or`' \| '`xor`' \| '`nand`' \| '`nor`' \| '`nxor`'
| *prefix-operator*{:#prefix-operator}[^prefix-op]     | = | '`not`' \| '`-`'
| *postfix-operator*{:#postfix-operator}               | = | '`++`' \| '`--`'
| *invocation-args*{:#invocation-args}[^args]          | = | \[*[bracketed-args]*\] \| *[closure-tail-args]*
| *bracketed-args*{:#bracketed-args}                   | = | '`(`' *[ws]* \[*[send-args]* *[ws]*] \['`;`' *[ws]* *[return-args]* *[ws]*\] '`)`'
| *closure-tail-args*{:#closure-tail-args}[^cls-tail]  | = | *[ws]* *[send-args]* *[ws]* *[closure]* \[*[ws]* '`;`' *[ws]* *[return-args]*\]
| *send-args*{:#send-args}                             | = | \[*[argument]*\] {*[ws]* \['`,`' *[ws]*] \[*[argument]*\]}
| *return-args*{:#return-args}                         | = | \[*[return-arg]*\] {*[ws]* \['`,`' *[ws]*] \[*[return-arg]*\]}
| *argument*{:#argument}                               | = | \[*[named-spec]* *[ws]*\] *[expression]*
| *return-arg*{:#return-arg}[^rarg]                    | = | \[*[named-spec]* *[ws]*\] *[variable-identifier]* \| *[define-temporary]*
| *named-spec*{:#named-spec}[^named]                   | = | *[variable-name]* *[ws]* '`:`'

</div>

<!--| *slice-operator*{:#slice-operator}[^slice]           | = | *[expression]* '`{`' *[ws]* *[range-literal]* \[*[wsr]* *[expression]*\] *[ws]* '`}`'

[^slice]: Returns sub-range: {[first] (..[last]) \| (# count) [wsr step]}. Where: last is inclusive; last and first may be negative with -1 last item, -2 penultimate item, etc.;  step may be negative indicating sub-range in reverse order. -->

[^call]: If an *[invoke-call]*'s optional *[expression]* (the receiver) is omitted, '`this.`' is implicitly inferred.
[^apply]: If receiver 'List' type - each item sent call -- coroutines called using `%` -- `sync`,  `%>` -- `race` concurrency depending on delimiter. If receiver empty list or `nil` invocation is skipped. If not list or `nil` then executes like normal invoke call -- i.e. '`%`' is synonymous to '`.`'.
[^i-op]: Akin to `expr.invoke(...)` or `expr._invoke(...)` depending if *[expression]* immediate or durational -- *and* if enough context is available the arguments are compile-time type-checked plus adding any default arguments.
[^idx-op]: Gets item (or sets item if *[binding]* present) at specified index object. Syntactic sugar for `at()` or `at_set()`.
[^instant]: If *[class-instance]* can be inferred then it may be omitted. When *[expression]* used rather than *[class-instance]* lots of syntactic sugar is provided: `expr!ctor()` is alias for `ExprClass!ctor(expr)` -- ex: `num!copy` equals `Integer!copy(num)`; brackets are optional for *[invocation-args]* if it can have just the first argument; a *[constructor-name]* of `!` is an alias for `!copy` -- ex: `num!` equals `Integer!copy(num)`; and if `expr!ident` does not match a constructor it will try `ExprClass!copy(expr).ident` -- ex: `str!uppercase` equals `String!copy(str).uppercase`.
[^op-call]: Every operator has a named equivalent. For example `:=` and `assign()`. Operators do *\*not\** have a special order of precedence -- any order other than left to right must be indicated by using code block brackets ('`[`' and '`]`').
[^math-op]: In order to be recognized as single subtract '`-`' *[expression]* and not an *[expression]* followed by a second *[expression]* that starts with a minus sign, the minus symbol '`-`' must either have whitespace following it or no whitespace on either side.
[^args]: *[bracketed-args]* may be omitted if the invocation can have zero arguments.
[^prefix-op]: See *[math-operator]* footnote about subtract on how to differentiate from a negation '`-`' prefix operator.
[^cls-tail]: Routines with last send parameter as mandatory closure may omit brackets '`()`' and closure arguments may be simple *[code-block]* (omitting '`^`' and *[parameters]* and inferring from argument parameter context). Default arguments indicated via comma '`,`' separators.
[^rarg]: If a temporary is defined in the *[return-arg]*, it has scope for the entire surrounding code block.
[^named]: Named arguments may only be used at end of the argument list -- and once used may only be followed by other named arguments. Named arguments may also specify an argument for a *[group-param]*, but must be compatible `List` object. Named arguments evaluated in parameter index order regardless of order they appear since defaults may reference earlier parameters. Note that *[bind]* may not be used as an argument.


<div class="table-wrap" markdown="block">
| [Type Primitives](#type-primitives){:#type-primitives .pad_r2}
|:-|-:|:-
| *type-primitive*{:#type-primitive}                        | = | *[class-cast]* \| *[class-conversion]*
| *class-cast*{:#class-cast}[^cast]                    | = | *[expression]* *[ws]* '`<>`' \[*[class-desc]*\]
| *class-conversion*{:#class-conversion}[^conversion]  | = | *[expression]* *[ws]* '`>>`' \[*[class-name]*\]

</div>

[^cast]: Compiler \*hint\* that expression evaluates to specified class -- otherwise error. *[class-desc]* optional if desired type can be inferred. If *[expression]* is *[variable-identifier]* then parser updates type context. \[Debug: runtime ensures class specified is received.\]
[^conversion]: Explicit conversion to specified class. *[class-name]* optional if desired type inferable. Ex: `42>>String` calls conversion method `Integer@String()` i.e. `42.String()` - whereas `"hello">>String` generates no extra code and is equivalent to `"hello"`.


<div class="table-wrap" markdown="block">
| [Flow&nbsp;Control](#Flow-Control){:#Flow-Control}
|:-|-:|:-
| *flow-control*{:#flow-control}                | = | *[code-block]* \| *[if]* \| *[when]* \| *[unless]* \| *[case]* \| *[nil-coalescing]* \| *[loop]* \| *[loop-exit]* \| *[concurrent-block]*
| *[code-block][man_code-block]*{:#code-block}  | = | '`[`' *[ws]* \[*[expression]* {*[wsr]* *[expression]*} *[ws]*] '`]`'
| *[if][man_conditionals]*{:#if}                | = | '`if`' {*[ws]* *[expression]* *[ws]* *[code-block]*}<sup>1+</sup> \[*[ws]* *[else-block]*\]
| *[else-block][man_conditionals]*{:#else-block} | = | '`else`' *[ws]* *[code-block]*
| *[when][man_conditionals]*{:#when}            | = | *[expression]* *[ws]* '`when`' *[ws]* *[expression]*
| *[unless][man_conditionals]*{:#unless}        | = | *[expression]* *[ws]* '`unless`' *[ws]* *[expression]*
| *[case][man_conditionals]*{:#case}            | = | '`case`' *[ws]* *[expression]* {*[ws]* *[expression]* *[ws]* *[code-block]*}<sup>1+</sup> \[*[ws]* *[else-block]*\]
| *nil-coalescing*{:#nil-coalescing}[^nil-coalescing] | = | *[expression]* *[ws]* '`??`' *[ws]* *[expression]*
| *loop*{:#loop}[^loop]                         | = | '`loop`' \[*[ws]* *[instance-name]*\] *[ws]* *[code-block]*
| *loop-exit*{:#loop-exit}[^exit]               | = | '`exit`' \[*[ws]* *[instance-name]*\]
| *concurrent-block*{:#concurrent-block}        | = | *[sync]* \| *[race]* \| *[branch]* \| *[change-mind]*
| *sync*{:#sync}[^sync]                         | = | '`sync`' *[ws]* *[code-block]*
| *race*{:#race}[^race]                         | = | '`race`' *[ws]* *[code-block]*
| *branch*{:#branch}[^branch]                   | = | '`branch`' *[ws]* *[expression]*
| *change-mind*{:#change-mind}[^change-mind]              | = | '`change`' *[ws]* *[expression]* *[ws]* *[expression]*

</div>

[^nil-coalescing]: `expr1??expr2` is essentially equivalent to `if expr1.nil? [expr2] else [expr1<>TypeNoneRemoved]`.
[^loop]: The optional *[instance-name]* identifies the loop for specific reference by a *[loop-exit]* which is useful for nested loops.
[^exit]: Only valid in the code block scope of the loop that it references.
[^sync]: 2+ durational expressions run concurrently and next expression executed when *\*all\** expressions returned (result `nil`, return args bound in order of expression completion).
[^race]: 2+ durational expressions run concurrently and next expression executed when *\*fastest\** expression returns (result `nil`, return args of fastest expression bound) and other expressions are *\*aborted\**.
[^branch]: Durational expression run concurrently with surrounding context and the next expression executed immediately (result `InvokedCoroutine`). expression is essentially a closure with captured temporary variables to ensure temporal scope safety. Any return arguments will be bound to the captured variables.
[^change-mind]: Rather than inheriting the caller's updater `Mind` object, durational expressions in the second expression are updated by the mind object specified by the first expression.


<div class="table-wrap" markdown="block">
| [File Contents](#File-Contents){:#File-Contents}
|:-|-:|:-
| *method-filename*{:#method-filename}[^m-fname]         | = | *[method-name]* '`()`' \['`C`'\] '`.sk`'
| *method-file*{:#method-file}[^m-file]                  | = | *[ws]* {*[annotation]* *[ws]*} *[parameters]* \[*[ws]* *[code-block]*\] *[ws]*
| *coroutine-filename*{:#coroutine-filename}             | = | *[coroutine-name]* '`()`' '`.sk`'
| *coroutine-file*{:#coroutine-file}[^c-file]            | = | *[ws]* {*[annotation]* *[ws]*} *[parameter-list]* \[*[ws]* *[code-block]*\] *[ws]*
| *data-filename*{:#data-filename}[^d-file]              | = | '`!Data`' \['`C`'\] '`.sk`'
| *data-file*{:#data-file}                               | = | *[ws]* \[*[data-definition]* {*[wsr]* *[data-definition]*} *[ws]*\]
| *data-definition*{:#data-definition}[^d-defn]          | = | {*[annotation]* *[ws]*} \[*[class-desc]* *[wsr]*\] '`!`' *[data-name]*
| *annotation*{:#annotation}[^annotation]                | = | '`&`' *[instance-name]*

</div>

[^m-fname]: If optional '`?`' is used in query/predicate method name, use '`-Q`' as a substitute since question mark not valid in a file name.
[^m-file]: Only immediate calls are permissible in the code block. If *[code-block]* is absent, it is defined in C++.
[^c-file]: If *[code-block]* is absent, it is defined in C++.
[^d-file]: A file name appended with '`C`' indicates that the file describes class members rather than instance members.
[^d-defn]: Optional *[class-desc]* is compiler hint for expected type of member variable. If class omitted, `Object` inferred or `Boolean` if *[data-name]* ends with '`?`'. If *[data-name]* ends with '`?`' and *[class-desc]* is specified it must be `Boolean`.
[^annotation]: The context / file where an *[annotation]* is placed limits which values are valid.

<!--
| *[object-id-filename][man_obj_id_files]*{:#object-id-filename}[^id-fname]  | = | *[class-name]* \['`-`' {`printable`}\] '`.sk`' '`-`' \| '`~`' '`ids`'
| *[object-id-file][man_obj_id_files]*{:#object-id-file}[^id-file]           | = | {*[ws]* *[symbol-literal]* \| *[raw-object-id]*} *[ws]*
| *[raw-object-id][man_obj_id_files]*{:#raw-object-id}[^raw-id]              | = | {`printable`}<sup>1-255</sup> *[end-of-line]*
-->

<!--
[^id-fname]: Starts with the object id class name then optional source/origin tag (assuming a valid file title) -- for example: `Trigger-WorldEditor`, `Trigger-JoeDeveloper`, `Trigger-Extra`, `Trigger-Working`, etc. A dash '`-`' in the file extension indicates an id file that is a compiler dependency and a tilde '`~`' in the file extension indicates that is not a compiler dependency
[^id-file]: Note: if *[symbol-literal]* used for id then leading whitespace, escape characters and empty symbol can be used.
[^raw-id]: Must have at least 1 character and may not have leading whitespace (*[ws]*), single quote ('`'`') nor *[end-of-line]* character.
-->

<div class="table-wrap" markdown="block">
| [Parameters](#HdrParameters){:#HdrParameters}
|:-|-:|:-
| *parameters*{:#parameters}[^params]                | = | *[parameter-list]* \[*[ws]* *[class-desc]*\]
| *parameter-list*{:#parameter-list}                 | = | '`(`' *[ws]* \[*[send-params]* *[ws]*] \['`;`' *[ws]* *[return-params]* *[ws]*\] '`)`'
| *send-params*{:#send-params}                       | = | *[parameter]* {*[ws]* \['`,`' *[ws]*\] *[parameter]*}
| *return-params*{:#return-params}                   | = | *[param-specifier]* {*[ws]* \['`,`' *[ws]*\] *[param-specifier]*}
| *parameter*{:#parameter}                           | = | *[unary-param]* \| *[group-param]*
| *unary-param*{:#unary-param}[^uparam]              | = | *[param-specifier]* \[*[ws]* *[binding]*\]
| *param-specifier*{:#param-specifier}[^param_spec]  | = | \[*[class-desc]* *[wsr]*\] *[variable-name]*
| *group-param*{:#group-param}[^gparam]              | = | '`{`' *[ws]* \[*[class-desc]* {*[wsr]* *[class-desc]*} *[ws]*\] '`}`' *[ws]* *[instance-name]*

</div>

[^params]: Optional *[class-desc]* is return class -- if type not specified `Object` is inferred (or `Boolean` type for predicates or `Auto_` type for closures) for nested parameters / code blocks and `InvokedCoroutine` is inferred for coroutine parameters.
[^uparam]: The optional *[binding]* indicates the parameter has a default argument (i.e. supplied *[expression]*) when argument is omitted.
[^param_spec]: If optional *[class-desc]* is omitted `Object` is inferred or `Auto_` for closures or `Boolean` if *[variable-name]* is predicate and ends with '`?`'. If *[variable-name]* ends with '`?`' and *[class-desc]* is specified it must be `Boolean`.
[^gparam]: `Object` inferred if no classes specified. Class of resulting list bound to *[instance-name]* is class union of all classes specified.


<div class="table-wrap" markdown="block">
| [Class Descriptors](#Class-Descriptors){:#Class-Descriptors}
|:-|-:|:-
| *class-desc*{:#class-desc}               | = | *[class-unary]* \| *[class-union]*
| *class-unary*{:#class-unary}             | = | *[class-instance]* \| *[meta-class]*
| *class-instance*{:#class-instance}       | = | *[class-name]* \| *[list-class]* \| *[invoke-class]*
| *meta-class*{:#meta-class}               | = | '`<`' *[class-name]* '`>`'
| *class-union*{:#class-union}[^union]     | = | '`<`' *[class-unary]* {'`|`' *[class-unary]*}<sup>1+</sup> '`>`'
| *invoke-class*{:#invoke-class}[^iclass]  | = | \['`_`' \| '`+`'\] *[parameters]*
| *list-class*{:#list-class}[^lclass]      | = | `List` '`{`' *[ws]* \[*[class-desc]* *[ws]*\] '`}`'

</div>

[^union]: Indicates that the class is any one of the classes specified and which in particular is not known at compile time.
[^iclass]: '`_`' indicates durational (like coroutine), '`+`' indicates durational or immediate (coroutine or method) and lack of either indicates immediate (like method). Class '`Closure`' matches any closure interface. Identifiers and defaults used for closure arguments without parameters.
[^lclass]: `List` can be any class derived from `List`. If *[class-desc] in item class descriptor is omitted, `Object` is inferred when used as a type or the item type is deduced when used with a *[list-literal]*. A *[list-class]* of any item type can be passed to a simple untyped `List` class.


<div class="table-wrap" markdown="block">
| [Whitespace](#HdrWhitespace){:#HdrWhitespace .pad_r2}
|:-|-:|:-
| *[wsr][man_whitespace]*{:#wsr}[^wsr]                   | = | {*[whitespace]*}<sup>1+</sup>
| *[ws][man_whitespace]*{:#ws}                           | = | {*[whitespace]*}
| *[whitespace][man_whitespace]*{:#whitespace}           | = | *[whitespace-char]* \| *[comment]*
| *[whitespace-char]*{:#whitespace-char}                 | = | '` `' \| `formfeed` \| `newline` \| `carriage-return` \| `horiz-tab` \| `vert-tab`
| *[end-of-line]*{:#end-of-line}                         | = | `newline` \| `carriage-return` \| `end-of-file`
| *[comment][man_comments]*{:#comment}                   | = | *[single-comment]* \| *[multi-comment]*
| *[single-comment][man_comments]*{:#single-comment}     | = | '`//`' {`printable`} *[end-of-line]*
| *[multi-comment][man_comments]*{:#multi-comment}       | = | '`/*`' {`printable`} \[*[multi-comment]* {`printable`}\] '`*/`'

</div>

[^wsr]: *[wsr]* is an abbreviation for (w)hite (s)pace (r)equired.


<div class="table-wrap" markdown="block">
| [Characters & Digits](#CharsDigits){:#CharsDigits}
|:-|-:|:-
| *character*{:#character}                    | = | *[escape-sequence]* \| `printable`
| *escape-sequence*{:#escape-sequence}[^esc]  | = | '`\`' *[integer-literal]* \| `printable`
| *alphanumeric*{:#alphanumeric}              | = | *[alphabetic]* \| *[digit]* \| '`_`'
| *alphascore*{:#alphascore}                  | = | *[alphabetic]* \| '`_`'
| *alphabetic*{:#alphabetic}                  | = | *[uppercase]* \| *[lowercase]*
| *lowercase*{:#lowercase}                    | = | '`a`' \| ... \| '`z`'
| *uppercase*{:#uppercase}                    | = | '`A`' \| ... \| '`Z`'
| *digits*{:#digits}                          | = | (*[non-zero-digit]* {*[digit]*}) \| '`0`'
| *non-zero-digit*{:#non-zero-digit}          | = | '`1`' \| '`2`' \| '`3`' \| '`4`' \| '`5`' \| '`6`' \| '`7`' \| '`8`' \| '`9`'
| *digit*{:#digit}                            | = | '`0`' \| '`1`' \| '`2`' \| '`3`' \| '`4`' \| '`5`' \| '`6`' \| '`7`' \| '`8`' \| '`9`'
| *big-digit*{:#big-digit}                    | = | *[digit]* \| *[alphabetic]*

</div>

[^esc]: Special escape characters: '`n`' - newline, '`t`' - tab, '`v`' - vertical tab, '`b`' - backspace, '`r`' - carriage return, '`f`' - formfeed, and '`a`' - alert. All other characters resolve to the same character including '`\`', '`"`', and '`'`'.

<br>

__Download SkookumScript Syntax__{: .hdr #download_syntax}<br>
Display or print out the SkookumScript syntax as a quick reference / cheat sheet. Use it when programming with SkookumScript for your project that will be the envy of the interwebs and lead to eventual world domination.<br>
<br>
[Download the SkookumScript syntax (PDF)](SkookumScript-Syntax.pdf){:.link-down} for your very own.
{:.note}

__Planned and Future Syntax__{: .hdr #download_syntax}<br>
While SkookumScript is very state-of-the-art and the "best compared to other leading brands"&trade; -- it continues to evolve. If you care to take a peek behind the curtain you can see some of the new syntax planned for SkookumScript in the near future.<br>
<br>
[Download the planned SkookumScript syntax (PDF)](SkookumScript-SyntaxPlanned.pdf){:.link-down} for fun and profit.
{:.note .soon}


<div class="footline" id="footline"></div>


[alphabetic]: #alphabetic
[alphanumeric]: #alphanumeric
[annotation]: #annotation
[apply-operator]: #apply-operator
[argument]: #argument
[big-digit]: #big-digit
[binary-operator]: #binary-operator
[bind]: #bind
[binding]: #binding
[boolean-literal]: #boolean-literal
[bracketed-args]: #bracketed-args
[branch]: #branch
[case]: #case
[change-mind]: #change-mind
[char-literal]: #char-literal
[character]: #character
[class-cast]: #class-cast
[class-conversion]: #class-conversion
[class-desc]: #class-desc
[class-instance]: #class-instance
[class-name]: #class-name
[class-unary]: #class-unary
[class-union]: #class-union
[closure-tail-args]: #closure-tail-args
[closure]: #closure
[code-block]: #code-block
[comment]: #comment
[compare-op]: #compare-op
[concurrent-block]: #concurrent-block
[constructor-name]: #constructor-name
[coroutine-name]: #coroutine-name
[create-temporary]: #create-temporary
[data-definition]: #data-definition
[data-name]: #data-name
[define-temporary]: #define-temporary
[destructor-name]: #destructor-name
[digit]: #digit
[digits]: #digits
[else-block]: #else-block
[end-of-line]: #end-of-line
[escape-sequence]: #escape-sequence
[expression]: #expression
[flow-control]: #flow-control
[group-param]: #group-param
[identifier]: #identifier
[if]: #if
[index-operator]: #index-operator
[instance-name]: #instance-name
[instantiation]: #instantiation
[integer-literal]: #integer-literal
[invocation-args]: #invocation-args
[invocation]: #invocation
[invoke-call]: #invoke-call
[invoke-cascade]: #invoke-cascade
[invoke-class]: #invoke-class
[invoke-operator]: #invoke-operator
[invoke-selector]: #invoke-selector
[list-class]: #list-class
[list-literal]: #list-literal
[literal]: #literal
[logical-operator]: #logical-operator
[loop-exit]: #loop-exit
[loop]: #loop
[lowercase]: #lowercase
[man_closure]: /docs/v3.0/lang/literals/closure/ "Manual page for Closure"
[math-operator]: #math-operator
[meta-class]: #meta-class
[method-name]: #method-name
[multi-comment]: #multi-comment
[name-predicate]: #name-predicate
[named-spec]: #named-spec
[nil-coalescing]: #nil-coalescing
[non-zero-digit]: #non-zero-digit
[object-id]: #object-id
[operator-call]: #operator-call
[operator-selector]: #operator-selector
[param-specifier]: #param-specifier
[parameter-list]: #parameter-list
[parameter]: #parameter
[parameters]: #parameters
[postfix-operator]: #postfix-operator
[prefix-operator]: #prefix-operator
[race]: #race
[raw-object-id]: #raw-object-id
[real-exponent]: #real-exponent
[real-literal]: #real-literal
[reserved-identifier]: #reserved-identifier
[return-arg]: #return-arg
[return-args]: #return-args
[return-params]: #return-params
[routine-name]: #routine-name
[scope]: #scope
[send-args]: #send-args
[send-params]: #send-params
[simple-integer]: #simple-integer
[simple-string]: #simple-string
[single-comment]: #single-comment
[string-literal]: #string-literal
[symbol-literal]: #symbol-literal
[sync]: #sync
[type-primitive]: #type-primitive
[unary-param]: #unary-param
[unless]: #unless
[uppercase]: #uppercase
[variable-identifier]: #variable-identifier
[variable-name]: #variable-name
[variable-name]: #variable-name
[variable-primitive]: #variable-primitive
[when]: #when
[whitespace-char]: #whitespace-char
[whitespace]: #whitespace
[ws]: #ws
[wsr]: #wsr
[man_code-block]: /docs/v3.0/lang/flow/code-block/ "Manual page for Code Block"
[man_comments]: /docs/v3.0/lang/comments/ "Manual page for Comments"
[man_conditionals]: /docs/v3.0/lang/flow/conditionals/ "Manual page for Conditionals"
[man_expression]: /docs/v3.0/lang/expressions/ "Manual page for Expressions"
[man_obj_ids]: /docs/v3.0/lang/identifiers/object-ids/ "Manual page for Object Ids"
[man_obj_id_files]: /docs/v3.0/lang/layout/object-id-files/
[man_whitespace]: /docs/v3.0/lang/whitespace/ "Manual page for Whitespace"
[EBNF]: https://en.wikipedia.org/wiki/EBNF "Wikipedia article on 'Extended Backus-Naur Form'"
[XKCD-manual]: http://xkcd.com/1343/ "XKCD - Manuals"
