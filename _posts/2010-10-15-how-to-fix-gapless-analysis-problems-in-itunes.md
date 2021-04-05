---
layout: post
title: "How to fix gapless analysis problems in iTunes?"
date: "2010-10-15"
categories: 
  - "apple"
  - "audio"
  - "software"
---

**The Problem:** If you use iTunes, on windows or mac, it is inevitable that you'd come across this dialog where iTunes says that it's Determining Gapless Playback Information. It doesn't matter whether you want your albums to play gapless or not. iTunes just goes ahead and does it. There is no way to turn it off. It would have been pretty harmless, except for one little thing - it often gets stuck and the only way out is to reboot your computer (and lose any unsaved data, not to mention the frustration caused). Though there is no way to turn this process off, there is a way to make it go smooth. The solution is to repair your corrupt MP3 files.

**The Reason:** There are plenty of reasons for MP3 files being corrupt but the most common one is bad encoders. All the modern encoders are ok but those present during Napster era (late 90s and early 2000s) were really bad. So if you have any songs encoded during that period, chances are that they are not as per MP3 encoding standards. These songs would play just fine but otherwise cause a lot of problems in terms of tagging and gapless analysis etc. If you do a scan on your collection, you'd be surprised by the number of songs with potential problems. These kind of files are the reason iTunes gets stuck.

**The Fix:** The fix is pretty simple, fortunately. All you need is [foobar](http://www.foobar2000.org/) and a bit of time. Don't worry. The songs will NOT be re-encoded or subject to anything else which might reduce their audio quality. These operations are completely harmless. You can take a backup in case you'd like to be really careful.

Ok, here we go:

1. Download and install foobar. Make sure that you choose all the utilities and extras during the install.
2. Launch foobar and go to 'File -> Preferences -> Shell Integration'. In the right-hand side pane, enable the option 'Folder context menus'. In the same pane, type '\*.mp3' for 'Restrict incoming files to'. This will make sure that only MP3 files come into foobar as this fix is not applicable for AAC or WAV files etc.
3. Go to your songs folder in Windows explorer, right-click and choose 'Enqueue in foobar2000'. Or you and drag your songs folder to foobar.
4. In foobar, Select all files, right-click and choose 'Utilities -> Rebuild MP3 Stream'. This will recreate the MP3 file by removing all the non-standard data and other garbage. It will also fix the tags by rewriting them in a standard-compliant way. It took about 3 hours to fix 20k files on my aging PC. A nice side benefit of this fix is that a few more songs will now show up in your iTunes library because of standards-compliant tags.
5. Once step 4 is over, select all files again, right-click and choose 'Utilities -> Fix VBR MP3 Header'. This will add the missing VBR header data to the Variable Bit Rate files. The absence of this header causes problems in seeking and also in calculating the duration of song which impacts gapless analysis. This process also took about 3 hours on my somewhat old PC.
6. This step is optional but I did it anyway. Clean up your iTunes library and add all the songs again. The only thing I care about is song ratings which I store in BPM field so I don't lose them even if I clean up the iTunes library.
7. Let iTunes go through 'Determining Gapless Playback Information'. Typically it won't get stuck now but there are chances that it still won't like a few of the songs. The only fix for these songs is to remove them from iTunes library. In my case, I had about 1000 songs in a particular folder which were giving problems. These were the songs which I had converted from FLAC to MP3 a long time back, prehaps using a crappy non-standard encoder. I just removed these songs from iTunes, re-encoded them from FLAC using Lame and everything went fine.

**Notes:** To validate your MP3 files, you can use a free program called [MP3val](http://mp3val.sourceforge.net/). It can even fix some of the common problems.
