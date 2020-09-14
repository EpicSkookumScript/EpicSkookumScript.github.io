---
layout: page
section: docs
title: SkookumScript UE4 Plugin installation and setup
numbered-headers: true
footer: false
sharing: false

---

You must have the [Unreal Engine](https://www.unrealengine.com/what-is-unreal-engine-4) installed on your system (either pre-built or build it yourself) before you can install the SkookumScript Unreal Engine 4 Plugin. ([Install Unreal Engine][UE4Install])
{:.note}

## Before installing the SkookumScript plugin, ensure UE4 is installed

[![SkookumDemo](/images/Download/SkookumDemo-editor.jpg){:.pic-full}][UE4Install]

After it is installed, choose your path to continue:
- [Pre-built Unreal Engine from Epic Games Launcher](#epic)
- [Custom built Unreal Engine using Visual Studio (or platform appropriate build tool)](#vs)

## Epic Games Launcher users (pre-built)
{:#epic}

[![](/images/Download/Workflow_Butterfly.jpg){:.pic-full}][SkMarketplace]

### First-time install
{:#epic-first-time}

1. Open Epic Games Launcher.
2. Under the **Unreal Engine** tab, click **Marketplace**. In the search box, type `SkookumScript`. [[SookumScript plugin on Unreal Marketplace web]][SkMarketplace]
3. The SkookumScript logo should appear; click it to go to SkookumScript Content Detail page. 
4. Scroll down and click **Install to Engine**.
5. An **Install to Engine** dialog box will appear; select the version(s) of Unreal Engine 4 to which you want to add the SkookumScript UE4 Plugin. Click **Install**.
6. [Get the SkookumDemo project (and any other sample projects you want)](https://github.com/EpicSkookumScript/SkookumScript-Demos) from GitHub. Try to get the files for the same version or less than and closest version to UE4 version you are using. Lower version projects _should_ be converted to newer versions of UE4.
7. Extract the zip archive(s) to **My Documents\Unreal Projects**. (If a different location is used for your project files, that's fine.) 
8. To launch the Unreal Editor, run the Epic Games Launcher, click the **Unreal Engine** tab, click **Library**, and then under **My Projects**, double-click any example project such as **SkInvaders**, **SkookumDemo** or any other Unreal project. Two windows will load: the SkookumIDE and the Unreal Editor. _Depending on your system, the SkookumIDE and Unreal Editor may take a few minutes to load._
9. If you have any issues, see if the [Resolving installation issues](/docs/ue4/setup/#resolving-installation-issues) section can help you out and then return back.
12. Ensure [UE4 settings are optimized](#ue4-settings) for SkookumScript development.

Have fun with your lovely new SkookumScript UE4 Plugin! Check out our [Docs](/docs/) for more info, and if you have any questions, comments or suggestions, please share them on the [SkookumScript Forum](https://skookum.chat/).


### Update an existing install to the latest version
{:#epic-update}

The UE4 Marketplace will alert you when an update of the SkookumScript UE4 Plugin is available. When that occurs, click on the **SkookumScript** badge and follow the instructions. _Voilà!_

Enjoy your updated SkookumScript UE4 Plugin! Check out our [Docs](/docs/) for more info, and if you have any questions, comments or suggestions, please share them on the [SkookumScript Forum](https://skookum.chat/).


### Uninstall
{:#epic-uninstall}

1. Run the Epic Games Launcher.
2. Under the **Unreal Engine** tab, click **Library**.
3. Under **Engine Versions**, click **Installed Plugins** under the relevant version of Unreal Engine. 
4. In the list of installed plugins, locate **SkookumScript** and click **Remove**.  


## Microsoft Visual Studio users (full source build)
{:#vs}

[![](/images/Download/SkCode.jpg){:.pic-full}][SkGit]

### First-time install
{:#vs-first-time}

The SkookumScript Unreal Engine 4 Plugin source code is provided via [GitHub][SkGit]. Be sure to check for updates and bug fixes and you can send us pull requests with your own nifty additions and improvements.

Our plugin resides within the **Engine/Plugins** folder, so it is a GitHub repository within a GitHub repository. This is a supported configuration in Git, and Git handles it by automatically excluding anything in the subfolder from the parent repository. We recommend using Git from the command line for the initial cloning, as GUI tools such as SourceTree can get confused by this configuration. The following instructions assume your Unreal Engine version is **4.23**. 

1. Open a command prompt.
2. Ensure you have [Git Large File Storage (Git LFS)](https://git-lfs.github.com/) enabled. (See extra info on [installing Git LFS](https://github.com/github/git-lfs/wiki/Installation).)
3. Follow the instructions on the [SkookumScript plugin on GitHub](https://github.com/EpicSkookumScript/SkookumScript-Plugin)
  It will be along the lines of:
  `cd` to your **Engine/Plugins** folder, and run this command:<br />`git clone https://github.com/EpicSkookumScript/SkookumScript-Plugin.git SkookumScript -b 4.23`
4. [Get the SkookumDemo project (and any other sample projects you want)](https://github.com/EpicSkookumScript/SkookumScript-Demos) from GitHub. Try to get the files for the same version or less than and closest version to UE4 version you are using. Lower version projects _should_ be converted to newer versions of UE4.
5. Extract the zip archive(s) to **My Documents\Unreal Projects**. (If a different location is used for your project files, that's fine.) 
6. Run `GenerateProjectFiles.bat`.
7. Open the generated Visual Studio solution file.
8. If your engine version is 4.15 or below, right-click the **UnrealHeaderTool** project in the VS Solution Explorer, then click **Clean**. _(It is very important to do this before you build the engine or your project!)_
9.  Build the engine or your project. As it builds, `Module.SkookumScriptGenerator.cpp` should fly past in the Output window to indicate that SkookumScriptGenerator has been properly recognized as a plugin.
10. To launch the Unreal Editor, run the Epic Games Launcher, click the **Unreal Engine** tab, click **Library**, and then under **My Projects**, double-click any example projects such as **SkInvaders**, **SkookumDemo** or any other Unreal project. Two windows will load: the SkookumIDE and the Unreal Editor. _Depending on your system, the SkookumIDE and Unreal Editor may take a few minutes to load._
11. If you have any issues, see if the [Resolving installation issues](/docs/ue4/setup/#resolving-installation-issues) section can help you out and then return back.
12. Ensure [UE4 settings are optimized](#ue4-settings) for SkookumScript development.

The IDE will create a user settings file on its first run. It's located at `Plugins/SkookumScript/SkookumIDE/SkookumIDE-user.ini`. Take a look as not all settings are exposed in the IDE user interface.

Have fun with your lovely new SkookumScript UE4 Plugin! Check out our [Docs](/docs/) for more info, and if you have any questions, comments or suggestions, please share them on the [SkookumScript Forum](https://skookum.chat/).


### Update an existing install to the latest version
{:#vs-update}

_Important:_ If you want to preserve settings from your current install, save a copy of the file **Engine/Plugins/SkookumIDE/SkookumIDE-user.ini** in another location before updating, and restore it after updating.

1. Open a command prompt, `cd` to your **Engine/Plugins/SkookumScript** folder and run `git pull`.
2. Get any updated SkookumScript demo projects desired as described in #4 above and replace your existing version(s) of the demo project(s) with the contents of the zip archive(s). 
4. Run `GenerateProjectFiles.bat` 
5. Open the generated Visual Studio solution file.
6. If your engine version is 4.15 or below, right-click the **UnrealHeaderTool** project in the VS Solution Explorer, then click **Clean**. _(It is very important to do this before you build the engine or your project!)_
7. Build the engine or your project. 
8. Delete the **SkookumScript** folders in both your **Engine/Content** and **SkookumDemo/Content** folders.

Enjoy your updated SkookumScript UE4 Plugin! Check out our [Docs](/docs/) for more info, and if you have any questions, comments or suggestions, please share them on the [SkookumScript Forum](https://skookum.chat/).


### Uninstall
{:#vs-uninstall}

1. Delete the **Engine/Plugins/SkookumScript** folder.
2. Build the engine or your project.


## Modify UE4 settings for SkookumScript
{:#ue4-settings}
In order to get the best development experience with the SkookumIDE and Unreal Engine 4 you should modify a few UE4 Editor settings:

1. In the Unreal Editor, click the **Edit** tab, then click **Editor Preferences...**
2. In the **Editor Preferences...** dialog box, click **General**, then click **Miscellaneous**, then click **Performance**, and ensure that **Use Less CPU When In Background** is unchecked. Click **Set as Default** (If you receive the "The default configuration file for these settings is not currently writable. Would you like to make it writable?" message, click Yes.)
3. Also in the **Editor Preferences...** dialog box, click **Level Editor**, then click **Miscellaneous**, then click **Sound**, and ensure that **Allow Background Audio** is checked. Click **Set as Default** (If you receive the "The default configuration file for these settings is not currently writable. Would you like to make it writable?" message, click Yes.)


## SkookumScript for other engines

If you aren't an Unreal Engine user, fear not! The SkookumScript Unreal Engine 4 Plugin contains source code examples, the SkookumScript C++ API and libraries necessary to integrate SkookumScript into just about anything -- game engines, embedded systems, robots, real-time applications, and more. With medium-to-advanced C++ skills, you can use the SkookumScript API to integrate into just about any code base on almost any platform in just a few hours.

Download the SkookumScript UE4 Plugin C++ source code and precompiled SkookumScript API from GitHub using the same first three steps described for the Microsoft Visual Studio setup instructions. Requires C++ compiler.

[**Get the SkookumScript C++ API from GitHub!**][SkGit]
{:.bubble-link}


## Resolving installation issues

Both SkookumScript and Unreal Engine 4 are complex software and they can sometimes run into issues when they are being installed on your unique and also complex computer system. Some of these issues may need to be revisited with updates and new versions.

Here are a few tips that might help:

### Anti-virus software (AVS)

You may need to whitelist the SkookumIDE or the UE4 Editor in any anti-virus software (AVS) that you may be running.
  
The default anti-virus pre-installed on MS Windows is called _Windows Defender_. It may use its _SmartScreen_ to block `SkookumIDE.exe`. It is especially likely to be blocked if you downloaded the SkookumScript UE4 Plugin yourself. If you see a pop-up similar to this (it may be a different color based on your settings):
  
![Windows Defender SmartScreen Initial](/images/Docs/SmartScreen1.png){:.img-center}
  
Select the **More info** under the text and it will change to look something like this, adding a **Run anyway** button:
  
![Windows Defender SmartScreen Initial](/images/Docs/SmartScreen2.png){:.img-center}
  
Obviously this is the software that you just installed and you want to run it. Select the **Run Anyway** button and it should start. _[You may have to do this whenever the SkookumIDE starts for the next few sessions until SmartScreen accepts that it isn't a threat.]_


### Connection: Firewalls and VPNs

The SkookumIDE and the UE4 Editor need to communicate with each other in order to work properly. If needed, see [Communication issues](/docs/v3.0/ide/ip-addresses/#communication-issues) to resolve network issues related to areas such as firewalls, virtual private networks (VPNs), etc.


### Timing issues

If you receive a "SkookumScript UE4 Plugin cannot connect to the SkookumIDE!" message, wait a few seconds and select **Try Again** -- the connection should be successful. This is likely if you got held up on other issues that slowed down the start of things.

If the SkookumIDE is up and not connected or if the UE4 Editor is up and running with a project loaded and the SkookumIDE is not up, you can press the ![Sk]{:.emoji} button on the UE4 editor toolbar to connect them. [See more about it](/docs/ue4/quickstart/#sk-button).

If the SkookumIDE does not start automatically when you run the UE4 Editor or when you press the ![Sk]{:.emoji} button on the UE4 editor toolbar, then you can try to run `SkookumIDE.exe` manually. Find it in your engine plugins folder, which is in a location similar to `\\Program Files\\Epic Games\\UE_4.18\\Engine\\Plugins` and in that is where you can find the SkookumScript plugin and `\\Marketplace\\SkookumScript\\SkookumIDE\\Engine\\Binaries\\Win64`. Try to run it and if it seems to load up, then try running the UE4 Editor and load up your project.


### Still having issues?

If you have any additional issues or questions, please head over to the [SkookumScript forum](https://skookum.chat/) and see if other users have had a similar issue resolved or create a post describing your issue and we will help walk you through it.

---
[**Next >>**{:.tip} **SkookumScript Primer**](/docs/v3.0/)<br/>
[**<< Previous**{:.tip} **Documentation Intro**](/docs/)
{:.bubble-link}


[Sk]: /images/Sk-icon-40.png
[SkGit]: https://github.com/EpicSkookumScript/SkookumScript-Plugin
[SkMarketplace]: https://www.unrealengine.com/marketplace/en-US/slug/skookumscript
[UE4Install]: https://docs.unrealengine.com/en-US/GettingStarted/Installation/index.html
