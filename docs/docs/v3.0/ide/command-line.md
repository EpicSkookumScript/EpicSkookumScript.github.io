---
layout: page
section: docs
title: SkookumIDE command line
numbered-headers: true
footer: false
sharing: false

---

## Quick reference

Even though the SkookumIDE is a GUI program it can be run with [command-line arguments][cl_args]. In this way the command prompt and other applications such as Microsoft Visual Studio or *Your Favourite Editor<sup>TM</sup>* can communicate with the SkookumIDE. This can enable other applications to send script commands to a running game or world editor – giving the apps [scripting superpowers](#script-superpowers).

Arguments can be sent to the SkookumIDE on its start-up or when it is already running. If it is already running, any call to a second instance of the IDE will pass any command-line arguments to the already-running IDE, shut down and then the already-running IDE will run the arguments.


### Single argument: identifier or file/folder path

The IDE can be called with a single identifier or file/path argument, such as dragging a file to <strong>SkookumIDE.exe</strong> in Windows Explorer:

<div class="table-wrap clear-all" markdown="block">
| Argument[^arg_quoted]  | Action
|:-|:-
|Class<br/>class path | Browse to class in SkookumIDE Browser. See the [`-b` switch described below](#switch_b).
|Class@member<br/>Class.member<br/>\<Class\>.class_member<br/>member file path | Browse to member in SkookumIDE Browser. See the [`-b` switch described below](#switch_b).
|other text file | Execute file contents as a script on the startup Mind object. See the [`-xf` switch described below](#switch_xf).

</div>

``` bat Single Argument Examples
REM Browse to Master class
C:\Skookum>SkookumIDE Master 

REM Browse to _startup() coroutine in Master class
C:\Skookum>SkookumIDE Master._startup 

REM Browse to _startup() coroutine in Master class using folder
C:\Skookum>SkookumIDE Scripts\Core\Object\Mind\Master 

REM Browse to _startup() coroutine in Master class using file
C:\Skookum>SkookumIDE Scripts\Core\Object\Mind\Master\_startup().sk 

REM Parse and execute script code in scripts.sk file
C:\Skookum>SkookumIDE scripts.sk 
```
C:\Skookum is shorthand for your SkookumIDE plugin folder, such as D:\UnrealEngine\4.15\Engine\Plugins\SkookumScript\SkookumIDE.
{:.aside}

### Command-line switches

The SkookumIDE can also be called with the following switches (options):

<div class="table-wrap clear-all" markdown="block">
| <span style="white-space: nowrap;">Switch[^switch_dash_slash]</span> | Argument[^arg_quoted] | Action
|:-|:-|:-
`-b`{:#switch_b} | Class@member<br/>Class.member<br/>\<Class\>.class_member<br/>member file path<br/>Class<br/>class path | Browse to specified member (coroutine or method) or class using its qualified name or file/path.
`-x`[`i`] | {`expression`}<sup>1+</sup> | Execute specified expression(s) separated with whitespace on the startup `Mind` object. `-x` runs the script on the runtime and `-xi` runs it locally on the IDE. *(Must be used as last swtich.)*
`-xf`{:#switch_xf}[`i`] | file path | Execute specified file contents as a script on the startup `Mind` object. `-xf` runs the script on the runtime and `-xfi` runs it locally on the IDE.
`-f` | | Bring the SkookumIDE to foreground.<br/>*(Can be added prior to other switches.)*
`-m` | | Minimize the SkookumIDE on startup.<br/>*(Can be added prior to other switches.)*
`-?`<br/>`-h` | | Displays command-line help

</div>


### Command prompt

Here are some example commands to run on the command prompt. The SkookumIDE Log displays the results. 

``` bat Switch Argument Examples
REM Do some math
C:\Skookum>SkookumIDE -x 200.0 + [123.0 / 3.0]

REM Simulate a 6-sided die on the IDE
C:\Skookum>SkookumIDE -x 1 + @@random.uniform_int(6)


REM ==== Using the Unreal Engine 4 SkookumDemo ====

REM Get the location of the player
C:\Skookum>SkookumIDE -x payer_pawn.actor_location

REM Have all the Enemy robots explode simultaneously
C:\Skookum>SkookumIDE -x Enemy.instances%_boom 

REM You can send several expressions at once
REM Reset position of robots then path one after the other to the player
C:\Skookum>SkookumIDE -x robo_reset Enemy.instances._do[item._path_to_actor(player_pawn)] 
```

**SkookumIDE command-line prints to the SkookumIDE Log, not the command prompt**{: .hdr}<br>
Output from running SkookumIDE.exe with command-line arguments will print to the SkookumIDE Log rather than the command prompt. SkookumIDE.exe is a GUI application rather than a console application, so it cannot print to the [_standard output_](https://en.wikipedia.org/wiki/Standard_streams#Standard_output_.28stdout.29) and its results are not displayed by the command prompt.
{:.aside}


## Add 'scripting superpowers' to your other applications
{:#script-superpowers}

The fun part of SkookumIDE command-line arguments is hooking up *keyboard shortcuts* (sometimes called *hotkeys*) in your other development tools so that they can interact with the scripting system and the running game engine/editor.

Some of the commands that you might want to hook up will help streamline your workflow. For example: since pressing Ctrl+E while editing a file in the SkookumIDE loads up the file in the application associated with the file extension (such as .sk), one keyboard shortcut that is useful is assigning Ctrl+E on the same associated editor to in turn load the file being edited back into the SkookumIDE. This makes it easy to toggle back and forth.

Some examples of game script commands that you could run from a different tool:

- simple or even fairly sophisticated math: turn any text editor into a powerful calculator
- toggle game settings: make it night or day, disable damage, make all the bad guys have low health, toggle mission achievement and completion flags, enable or disable trigger regions
- change the game progression: restart the level, jump to the end of a level
- have the camera orient to or focus on an object of interest
- teleport the player to another location
- teleport an object or character to the player
- create objects: spawn a vehicle, ammo, powerup, etc. near the player
- change stats: give the player limitless health or special abilities
- get a game character to path to an object such as the player
- commands that loop, take time, or display periodic statistics -- basically anything you can think of! 

Many of these commands could be in the comments above code that you are working on in the game for quick reference or in a handy scratch pad text file of script snippets. Just select it and run it with a key shortcut.

Some of the keyboard shortcuts that we suggest might already be mapped to other commands, in which case feel free to use another keyboard shortcut or replace the current mapping. We suggest adopting a keyboard shortcut standard for your team so when members help each other or swap desks, everyone will have the handy shortcuts that they expect. 


### Visual Studio

Here are some interesting SkookumIDE commands that you can hook into Microsoft Visual Studio with our suggested keyboard shortcuts.

To add some handy script commands in Visual Studio, click the <strong>Tools</strong> tab, click <strong>External Tools...</strong>, and then click <strong>Add</strong> and enter the items in the table below. The <strong>Command</strong> field should be `\<your SkookumIDE dir>\SkookumIDE.exe`. 

You can find all the arguments/variables for External Tools [here][VS_args], or you can also click the triangle to the right of <strong>Arguments</strong>. <strong>Initial directory</strong> can be left empty. **Prompt for arguments** should be unchecked. When done, click **Apply**. You can then move the command up and down as you like -- the External Tool order is important when you reference it to give it a keyboard shortcut.

<div class="table-wrap clear-all font0_9em" markdown="block">
| Hotkey | Title | Argument[^arg_quoted] 
|:-|:-|:-
`Ctrl`+`E` | Skookum Browse File | `$(ItemPath)`
`Ctrl`+`Alt`+`E` | Skookum Browse Selected | `-b $(CurText)`
`Ctrl`+`~` | Skookum IDE | `-f`
`Alt`+`~` | Skookum Run Selected | `-f -x $(CurText)`
`Ctrl`+`Alt`+`~` | Skookum Run IDE Selected | `-f -xi $(CurText)`

</div>

Any new External Tool commands added in this way will automatically be added to the Tools group in the Main Menu of Visual Studio. To run them, have the file open or text selected as needed for the command you want to run, click **Tools** and select the command.

Here are instructions on how to [associate keyboard shortcuts][VS_keys]. To find the external tool commands you have added, in the **Show commands containing:** box type `ExternalCommand`. Note that each external command corresponds with its position in the list of external commands as described above.


### Other applications

If you have some favorite keyboard shortcuts for an application not yet listed, and you think that others would like to know about them, please [let us know][forum]] and we may add them to this page.

<div class="footline" id="footline"></div>


[^arg_quoted]: Arguments may optionally be enclosed in double quotes: `"arg"`. The quotes will be kept or removed automatically as needed.
[^switch_dash_slash]: Switches may use the forward slash `/` rather than the dash `-`, so `SkookumIDE -?` is the same as `SkookumIDE /?`. Note that a dash must be preceded by a space, (such as `SkookumIDE -?`), but a forward slash need not be preceded by a space (`SkookumIDE/?`).

[cl_args]: https://en.wikipedia.org/wiki/Command-line_interface#Arguments "Command-line argument Wikipedia entry"
[forum]: https://skookum.chat "The Official SkookumScript Community Forum"
[VS_args]: https://msdn.microsoft.com/en-us/library/ekbzk5f8.aspx "Microsoft Visual Studio: Arguments for External Tools"
[VS_keys]: https://msdn.microsoft.com/en-us/library/5zwses53.aspx#bkmk_assign ""Microsoft Visual Studio: Custom Keyboard Shortcut Assignment" 