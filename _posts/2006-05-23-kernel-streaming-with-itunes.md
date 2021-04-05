---
layout: post
title: "Kernel Streaming with iTunes."
date: "2006-05-23"
categories: 
  - "apple"
  - "audio"
  - "software"
---

iTunes is considered to be the best music organizer and foobar to be the best music player. But what if you could have the interface of iTunes but guts of foobar in one application? Enter [Multi-plugin](http://www.aqua-soft.org/board/showthread.php?t=38334 "Multi-plugin").

Here is what you'll need:

1. [foobar](http://www.foobar2000.org/) (0.9.4) and [Kernel Streaming plugin](http://www.foobar2000.org/components/index.html) for foobar.
2. [iTunes](http://www.apple.com/itunes/) (for Windows, ver 7.0.1)
3. [Multi-plugin](http://www.aqua-soft.org/board/showthread.php?t=38334 "Multi-plugin") (latest version is 2.4.2 as of September 22, 2006)

Install iTunes, foobar, and Multi-plugin. To install Kernel Streaming plugin for foobar, just copy the file "foo\_out\_ks.dll" to foobar components directory.

Run foobar, go to file-> preferences -> playback -> output and choose Kernel Streaming as the output method.

Run iTunes, go to Edit -> preferences -> Multi-plugin and make the following changes:

1. Under "Appearance", choose the default skin.
2. Under "Other", choose "foobar2000 passthrough".

Now whenever you hit play on a song in iTunes, it would be played through foobar. This means that you get access to all the foobar DSP goodness too. Enjoy!

**Notes:**

1. You might get the message "foobar not installed" when you enable "foobar2000 passthrough". This happens because Multi-plugin looks for foobar information in the wrong place in the registry. It's pretty easy to fix though. Just transfer the keys from "HKEY\_LOCAL\_MACHINE\\Software\\Foobar2000" to "HKEY\_CURRENT\_USER\\Software\\Foobar2000". To do that, go to "HKEY\_LOCAL\_MACHINE\\Software\\Foobar2000" in the registry and choose File->Export. Then open the resulting \*.reg file using notepad and change "HKEY\_LOCAL\_MACHINE\\Software\\Foobar2000" to "HKEY\_CURRENT\_USER\\Software\\Foobar2000". Save the file and double-click. Done!
2. You need to set the volume to maximum in iTunes to avoid any loss of quality because of attenuation.
3. Even if you don't notice any improvement in the sound quality, this would at least take care of the songs skipping in iTunes (a big problem in iTunes 7.x.x).
4. You can not run both foobar and iTunes at the same time. Otherwise you'd get error "KS output error: error opening device". In fact, you don't _have_ to run foobar to use Multi-plugin. iTunes would launch it automatically in the background.

**Update on September 20, 2006:** Links now point to the latest version of Multi-plugin, 2.4.2.
