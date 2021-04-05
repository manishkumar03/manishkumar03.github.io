---
layout: post
title: "How to fix iPod Eq distortion."
date: "2005-11-08"
categories: 
  - "apple"
  - "audio"
---

**The Problem:** iPod gives a somewhat harsh and metallic sound when the equalizer is turned on. It does not matter which preset you choose (except Flat). If you don’t keep the equalizer off, the sound comes out distorted and is not pleasant to listen to. It happens on all the iPod models, even on the latest 5G one which has the best sound among hard disc based models. The 5G fixes lot of problems with the earlier iPods like Noise Defect and comes with a [number of improvements](http://www.ilounge.com/index.php/articles/comments/top-ten-things-techies-wanted-to-know-about-the-5g-iPod), especially in bass performance but the sound still clips with the equalizer.

**The Reason:** There is nothing wrong with iPod. [Really](http://machrone.home.comcast.net/playertest/distortion.htm).

It has as good a sound as any other player. Though it sounds a little bright, the sound has lot of detail and really insignificant amount of distortion. Even the equalizer is well designed and behaves as it is supposed to. But that metallic sound? That clipping? Well, it’s a classic case of “garbage in garbage out".

It’s those damn mp3s. Or rather the original CDs themselves.

In a race to sound louder and louder, the CD mastering engineers [push the recording level](http://www.johnvestman.com/disease.htm) to its limits. This is especially true for mainstream pop/rock music. Somehow the producers think that the CDs have to be [really loud](http://georgegraham.com/compress.html) to make a better impression.

Now when these hot mastered CDs (or mp3s made from them) are played with the equalizer on, the total loudness level goes beyond what an iPod can produce. Some of my mp3s had a loudness level of 99.6db!! Yikes! What can the poor iPod do when presented with this crap? Say I choose Dance preset which would typically apply a boost of 6 db. Add this to 97db (a typical figure) and you get a level of 103 db. Most players have an upper limit of about 95db, some even going till 100db but that’s it. No wonder the sound comes out distorted and harsh.

**The Fix:** All we need to do is bring down the loudness level of the mp3s down so that we get a little headroom to apply the Eq. The generally agreed upon loudness level for this is 89db.

Download [mp3gain](http://mp3gain.sourceforge.net/). It’s an open source freeware program. Add the folder containing the mp3s. Choose ‘track gain’ and click on the ‘track analysis’. It will calculate and display the loudness level for each song and also how much correction needs to be applied. When this analysis is done, just hit ‘track gain’ and it will apply the required correction to each song.

Mp3gain does not re-encode or otherwise modify/degrade the file in anyway. All it does is set a flag in the file. When a player reads this flag, it knows how loud to play this song.

This whole correction process is a little slow. It took about one hour per GB on my Pentium 4 machine, 30 hours total for my entire collection. It’s the analysis part that is slow. The correction is instantaneous. So instead of hitting the analysis and waiting for 30 hours to do the correction, a better way to do this is to hit the track gain directly. It will analyze and correct in one step.

After all this is done, erase all the songs from your iPod, resync, and enjoy!

**Notes:**

1. You can directly point mp3gain to iPod\_control folder on the iPod but it is not recommended. You don't want that tiny hard disc on your iPod to be spinning continously for 30 hours. Moreover, if you do it on the PC, other mp3 players can also use this info.
2. You can stop/cancel the track gain process anytime you want. Mp3gain will pick up from where it left when you start it next time.
3. Mp3gain is more accurate at doing normalization than SoundCheck feature found in iTunes/iPod. Mp3gain is based on [ReplayGain](http://replaygain.hydrogenaudio.org/) standard which takes into account the mechanism of how humans perceive loudness. Turns out that human ears use average energy over time to perceive how loud a certain sound is. So mp3gain divides each file into 50ms blocks and calculates the RMS energy value of each of these blocks. These values are then used to arrive at the overall RMS energy of the entire song. This is the value which is then used to normalize the song file. SoundCheck works in similar way but it seems to take much longer blocks ([fewer samples](http://www.hydrogenaudio.org/forums/index.php?showtopic=39018&view=findpost&p=345591)) to calculate the average RMS energy. This makes it less accurate (but a lot faster) than mp3gain.
