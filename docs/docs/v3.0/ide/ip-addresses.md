---
layout: page
section: docs
title: Communicating with remote (and local) runtimes
numbered-headers: true
footer: false
sharing: false
date: 2017-10-27

---

In order for the SkookumIDE and the SkookumRuntime (such as the UE4 editor or a game running on the desktop, console, mobile or VR device) to communicate between each other they must use the same IPv4 IP addresses.

## Communicating locally

When both the SkookumIDE and the SkookumRuntime are on the same system, such as on the MS Windows desktop with the SkookumIDE and the UE4 editor, then the [virtual loopback interface](https://en.wikipedia.org/wiki/Loopback#Virtual_loopback_interface) [`localhost` (127.0.0.1)](https://en.wikipedia.org/wiki/Localhost) is used by default. The virtual loopback interface is part of the networking driver software and not an actual physical adapter so it usually just works -- though some systems can have issues with it as with any communication.

The SkookumIDE also sends an anonymized ping to Google Analytics so we have an idea of who is using the SkookumIDE. You can ignore this -- the SkookumIDE will still work without the ping to Google Analytics.
{:.aside}


## Specifying the SkookumIDE IP address

The SkookumIDE is actually a server that listens for SkookumRuntimes trying to connect to it.

In addition to `localhost`, you can also have the SkookumIDE listen to an additional specific IP address. This is generally used to connect to a SkookumRuntime on a different system (such as consoles, mobile, or multi-player) -- though it can also be used with specific adapters on the same system. This address is stored in the `SkookumIDE-user.ini` configuration file. If it is present, it looks something like this:

```ini
[Remote IDE Hosts]
MyPCName=192.168.1.116
```

Where `MyPCName` is the name of your computer system in the OS. Your "PC name" can be found in the system settings. _[One simple way to get there is to type "computer name" in the Cortana "Type here to search" area in the Start bar of Windows 10.]_
{:.caption}

The IP address is associated with the name of the host PC so that you can use the same `.ini` file on a portable drive or shared network drive on multiple computers with different IP addresses.

You can bring up this file from the SkookumIDE by going to the "Edit"→"Preferences File..." menu option and it will load up that file in the editor you have associated with `.ini` files. It is a generated file, so you must run the SkookumIDE at least once. If you are using our Unreal Engine 4 plugin, you can also find `SkookumIDE-user.ini` and `SkookumIDE.exe` yourself in something similar to the `\Program Files\Epic Games\UE_4.17\Engine\Plugins\Marketplace\SkookumScript\SkookumIDE\` folder.

If it is not using the adapter address that you want - you can add or change it.

You will have to close and restart the SkookumIDE once you have changed the IP address.
{:.focus}

You can leave the IP address in the settings file and just have the SkookumIDE ignore it by adding a minus sign `-` before the IP address:

```ini
[Remote IDE Hosts]
MyPCName=-192.168.1.116
```

Still in the settings file though it is ignored.
{:.caption}


## Specifying the SkookumRuntime IP address

By default, the SkookumRuntime will connect to a local host IP address. It might not be the address that you want, so here is how you can set it manually.

Note that this same mechanism is used to specify a remote SkookumIDE IP address for any SkookumRuntime that is not on the same machine as the SkookumIDE such as consoles, mobile or multi-player.
{:.focus}

The SkookumRuntime will check if there is a file named `ide-ip.txt` in the compiled binary folder. In our Unreal Engine 4 plugin, this folder is located inside your project folder at  `Content/SkookumScript` which will get added to your pak file during packaging. If the runtime on your remote device finds the file `ide-ip.txt`, it uses the IP address stored in that file to connect to the SkookumIDE.

Note that `Shipping` builds of the runtime cannot connect to the SkookumIDE and do not read this file.
{:.focus}


## Communication issues

Even if it is two applications on the same system, some security software is over protective. You may have to 'whitelist' `SkookumIDE.exe` and possibly the Unreal Editor or any runtime using SkookumScript that you want to connect to the SkookumIDE on various Internet firewalls or anti-virus software in order for the IDE and the runtime to communicate properly. If you need to open a TCP/IP port, the one used by the SkookumIDE is `12357` (the first five prime numbers).

Some Virtual Private Network (VPN) software can have issues. The SkookumRuntime or SkookumIDE might latch on to a hardware or software adapter that isn't the best choice. In this case you may need to specify a particular IP to use to get around the problem. Some users reported that they would disable VPN while the SkookumIDE and the UE4 editor initially connected and then they would turn it back on again.

If you get a "Connection timed out" error, you should be able to safely select **Try Again** and skip past. This is more likely to occur if you ran into other issues or if it is the first run through and the start of the SkookumIDE was slow or delayed.

You may also want to look at [Resolving installation issues](/docs/ue4/setup/#resolving-installation-issues) for other ideas on getting things to work.

If you have additional communication issues please head over to the [SkookumScript forum](https://skookum.chat/) and see if other users have had a similar issue resolved or create a post describing your issue and we will help walk you through it.
{:.focus}
