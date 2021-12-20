---
layout: post
title: Things I learned clearing disk space
categories:
    - Productivity
published: true
links:
    - Hacker News: https://news.ycombinator.com/item?id=10823783
---

{% include image.html url="/static/learned-clearing-disk-space/screenshot.png" caption="Ushering one of computing's most mundane tasks" %}

This morning my Macbook Air produced the dreaded "your startup disk is almost full" dialog box. I proceeded to delete applications I no longer used, clear the `~/Downloads` folder, and empty the trash. To my surprise, though, I hardly cleared a gigabyte!

Disk scanners always struck me as scammy, but I finally gave in to [OmniDiskSweeper](https://www.omnigroup.com/more), a free utility that presents the filesystem as an exploratory tree of folders of descending size.

{% include image.html url="/static/learned-clearing-disk-space/omni.png" caption="OmniDiskSweeper presents folder and file sizes." %}

The exercise revealed stale folders I had completely overlooked:

1. `~/Library/` This is a hidden folder containing all sorts of system and application support files. I deleted `~/Library/Android/` (1.86 GB) and `~/Library/Application Support/Namecoin` (1.98 GB) because I no longer use the Android SDK and Namecoin client.
2. `~/Virtualbox VMs/` Before running OmniDiskSweeper, I had already purged this folder of the Virtualbox images I no longer used, leaving only the boot2docker VM. Little did I realize that `~/Virtualbox VMs/boot2docker-vm/` took up 15.76 GB! It's been a while since I used Docker for any projects, so I deleted that folder too.
3. `~/.*` I didn't realize how many utilities store data within hidden folders in the home directory. Here, I gained space by deleting `~/.meteor` (1.1 GB) and `~/.android` (4.0 GB).

All files tallied, I freed a whopping 24.7 GB. The experience revealed folders containing data I no longer needed for applications I no longer used. Dragging "Foo.app" to the Trash is rarely a comprehensive uninstallation.
