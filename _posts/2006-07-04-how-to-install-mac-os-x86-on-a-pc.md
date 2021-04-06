---
layout: post
title: "How to install Mac OS x86 on a PC"
date: "2006-07-04"
tags: 
  - "apple"
---

I have finally managed to install and boot into (these are two separate things in this context as will soon become clear) Mac OS x86 on my PC after struggling for more than two weeks. I used HotISO 10.4.6 install DVD. I don't know much about legal stuff but it is probably illegal to do this without owning apple hardware. I own an iBook G4 so maybe it is ok. I don't know. Please don't quote me on this.

**Before the install:**  
These are the things that you have to take care of before you start the install. 90% of people asking for help in the forums are there because they did not pay attention to this part. So before you start-

1. Make sure that your DVD drive is set up as primary slave. If it is not, you would still be able to install the OS but you won't be able to boot into it. It would say 'waiting for root device' or 'b0 error' and just hang there. Or the PC would keep on rebooting itself. Some of these problems can be fixed if you are able to boot from the DVD and go into terminal but you won't be able to boot from the DVD either (after the install).
2. Both your keyboard and mouse should either be PS/2 or both should be USB; you cannot mix and match. If you do, you won't be able to boot into the OS after the install. It would complain about keyboard being not present and just stop there.
3. Make a primary partition while you are in Windows. You can use Partition Magic or any other such tool to do non-destructive partitioning. Once created, mark this partition as 'Active' otherwise you won't be able to boot into Mac OS X. You don't have to format it at this point.  
    You might want to make the size of the new partition sufficiently different from the size of Windows partition so that they are easy to tell apart in the Mac OS installer. A minimum size of 6GB is needed though.
4. You don't need Linux, fdisk, Acronis OS selector or any other such tool. Whatever you need is right there on the DVD itself. Some people suggest sacrificing a goat but I doubt if that'll be of any help.

**Install process:**

Boot off the install DVD and keep clicking until it's time to choose the volume on which to install Mac OS X. The list would be blank as of now. Go to 'Utilities --> Disk Utility'. The left side of the panel would now show all the partitions. Select the one you want and click on 'erase' tab in the right-hand panel. Choose 'Journaled' as the file-system, name the volume, and click on the 'erase' button. Try to avoid naming this volume with spaces in the name like 'Mac OS X' etc. I named this volume as 'Tiger'. This kind of name would come in handy if you have to launch the terminal and copy files here and there.

The next important panel is 'Installation Type'. Choose 'Custom' and it would show you the list of packages to be installed. Pay attention to the last entry there which contains the patches and other drivers which make this whole exercise possible. Select only those patches here which match your system hardware. So if you have an intel CPU, do NOT select anything related to AMD. This is important. If you are not sure whether your CPU supports SSE2 or SSE3, download this [small standalone utility](http://www.cpuid.com/cpuz.php "CPU-Z"). Again, select SSE3 only if your processor supports it.

Sit back and relax.

Installer would reboot automatically when it's done and Mac OS X would start. Go through the simple setup process and enjoy.

**Post-install:  
**If only computers were so simple! [Post-installtion help forums](http://forum.osx86project.org/index.php?showforum=61) on OSx86 project are a good place to start if you are having any problems with your setup. Make sure to go through the [Technical FAQ](http://wiki.osx86project.org/wiki/index.php/Technical_FAQ) first.

**Credits:**

1. Niall Douglas's [page on installing](http://www.nedprod.com/Niall_stuff/MacOS%20X/index.html) Mac OS x86[](http://www.osx86project.org/)
2. [OSx86 project](http://www.osx86project.org/)
