---
layout: page
section: docs
title: Log widget
sidebar-page: none
footer: false
sharing: false
date: 2017-05-24

---

The **Log** widget displays output from various SkookumScript systems, including results from [command-line arguments](/docs/v3.0/ide/command-line/).

![SkookumIDE Log widget](/images/Docs/SkIDE-Log.png){: .img-center}

The **Log** widget displaying SkookumIDE system messages (blue) and a result string from the SkookumScript runtime (yellow).
{:.caption}

You can select, select-all, and copy Log text with the usual Windows actions. **Right click** to display a context menu that offers these functions, plus an option to clear the Log.

To differentiate SkookumIDE output and SkookumScript runtime output,

- _<span class="mono">SkookumIDE output is in italics.</span>_
- <span class="mono">SkookumScript runtime output is not in italics.</span>

Also, different kinds of output are differentiated by text color:

- <span class="mono clr-log-standard">Print commands (white)</span>
- <span class="mono clr-log-title">Titles and links (yellow)</span>
- <span class="mono clr-log-note">Notable events (green)</span>
- <span class="mono clr-log-system">System or C++ messages (blue)</span>
- <span class="mono clr-log-error">Error messages (red)</span>
- <span class="mono clr-log-warning">Warning messages (orange)</span>
- <span class="mono clr-log-result">Result strings from evaluating code snippets (light yellow)</span>
- <span class="mono clr-log-trace">Trace info (lavender)</span>

_<span class="mono clr-log-warning">So warnings from the SkookumIDE look like this.</span>_

<span class="mono clr-log-warning">Warnings from the SkookumScript runtime look like this.</span>

_<span class="mono clr-log-result">Result strings from the SkookumIDE look like this.</span>_

<span class="mono clr-log-result">And result strings from the SkookumScript runtime look like this.</span>

*TIP*{:.tip} Also see the ["Printing to the Log" section](/docs/v3.0/ide/workbench/#printing-to-the-log) on the [**Workbench** widget page](/docs/v3.0/ide/workbench/).
