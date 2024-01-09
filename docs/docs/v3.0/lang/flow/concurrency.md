---
layout: page
section: docs
title: Concurrency
footer: false
sharing: false

---

Much of the docs on coroutines and structured concurrency was lost when the SkookumScript Forum server was shut down (including its backups). Concurrency in the Verse language is copied from SkookumScript so take a look at the [Verse Concurrency docs][vconcurrency].
{:.focus}

In the meantime, see these concurrency-related posts on the remaining archives of the [SkookumScript Forum][forum]:

### Concurrent syntax
See the concurrency [flow control expressions][flow]: `sync`, `race`, `branch`, `change` plus the [concurrent apply operators](/docs/v3.0/lang/syntax/#apply-operator).

### Concurrent details
- [Coroutines in the SkookumScript Primer][coro]
- [Apply operators `%` (serial) and especially `%>` (concurrent race) in the SkookumScript Primer][applyops]
- [`branch` command explained](https://web.archive.org/web/https://skookum.chat/t/branch-command-explained/118?source_topic_id=784)
- [Order of coroutine updating](https://web.archive.org/web/https://skookum.chat/t/order-of-coroutine/1196/2)


### `Mind` objects and the `Master` `Mind`

Minds are used to manage and update coroutines, and encapsulate logical components of gameplay such levels, missions, minigames, squad AI, and group behaviors. Mind objects also often act as a starting or entry point for code.

Additional information on `Mind` objects can be found in these forum posts:

- [The `Mind`, the `Master` and who pulls the strings](https://web.archive.org/web/https://skookum.chat/t/the-mind-the-master-and-who-pulls-the-strings-in-skookumscript/110)
- [**change** command explained](https://web.archive.org/web/https://skookum.chat/t/change-command-explained/117)
- [How to use `BerzerkRobot` class](https://web.archive.org/web/https://skookum.chat/t/how-to-use-berzerkrobot-class/573)
- *Controlling which Mind a coroutine uses for its updating:* [Assigning a coroutine to a `Mind`](https://web.archive.org/web/https://skookum.chat/t/assigning-a-coroutine-to-a-mind/1101/3)


### Advanced coroutine control
- [Coroutine to Play Matinee - and `InvokedBase`](https://web.archive.org/web/https://skookum.chat/t/coroutine-to-play-matinee/664/2)


[applyops]: /docs/v3.0/#apply-operator "Apply operators"
[coro]: /docs/v3.0/#coroutines "Coroutines"
[flow]: /docs/v3.0/lang/syntax/#Flow-Control "Flow control syntax"
[forum]: /community/ "Discuss SkookumScript with the community"
[vconcurrency]: https://dev.epicgames.com/documentation/en-us/uefn/concurrency-overview-in-verse