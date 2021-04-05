---
layout: post
title: "Getting the best sound out of your PC."
date: "2005-04-13"
categories: 
  - "audio"
---

_This article [originally appeared](http://www.osnews.com/story.php?news_id=10324) on Osnews.com._

[Chesky records](http://www.chesky.com/), a small record label, produces what is called audiophile friendly music. To learn how to create music with this high detail and how to play it right, just read some of their [articles](http://www.chesky.com/Articles/body_library.cfm). There is a lot of talk there on tube amps and stereo mics and horn speakers etc. Forget the high-end gear, there is one complete article on how to set up your power supply for best audio experience. But mere mortals like us listen to the music on our PCs. Though it does not even begin to compare with all that exotic gear out there, it can be set up to deliver a surprisinlgy good quality sound.

This is a highly simplified diagram of how the music flows: mp3 file --> mp3 decoder --> processor --> soundcard --> speakers --> Ears

Each one of these stages has to be optimized if you want the best quality sound. If the mp3 file is low-bit rate to begin with, no amount of tweaking can make it sound lush and full. Or if you are using tin boxes for speakers, even a SACD would sound crappy on them. One weak link in the chain and there goes your listening experience.

**Input:** MP3 technology was developed by Fraunhoffer Institute in Germany. They also provide software to encode/decode MP3 files and that is what is used in winamp by default. But these official decoders are not the best sounding ones. That honor goes to an open source (surprise! surprise!) decoder called [mpg123](http://www3.cypress.ne.jp/otachan/in_mpg123.html). It supports ReplayGain and 24-bit output, both of which are lacking from the official decoder. The difference in quality may not be that apparent on ordinary songs but this plugin really shines when the MP3 file contains a lot of detail.

To use this plugin, Just copy the file 'in\_mpg123.dll' to 'C:\\Program Files\\Winamp\\Plugins' and launch winamp. Then under Preferences->input, choose mpg123 and double click on it to set its properties. Under Decoder tab, check 'Enable' and choose output format as '16 bit' (or '24 bit' if your sound card supports it). Under Replay Gain tab, check 'Enable', choose 'Album gain', and choose 'Hard Limiter'. ReplayGain will make sure that all the songs play back at the same loudness, thus freeing you from changing the volume for different songs which had been mastered at different levels. No changes are made by ReplayGain to the original MP3 file. It just puts a tag on the file which is used by the decoder to decide whether to amplify or attenuate.

An alternative MP3 decoder called [MAD](http://www.mars.org/home/rob/proj/mpeg/mad-plugin/) also has a lot of following. There is no conclusive evidence that it is [better than mpg123](http://handhelds.org/pipermail/ipaq/2000-September/000896.html) but [arguments](http://www.hydrogenaudio.org/forums/lofiversion/index.php/t4794.html) go on.

PS - The official mp3 encoder is also not the best one out there! That honor goes (again) to an open source encoder called [LAME](http://lame.sourceforge.net).

**Processing:** After a mp3 file gets decoded, it is fed to a Windows component called kmixer. It does exactly what its name implies - it mixes all the audio streams being fed to it and sends them to the soundcard. This is how we can hear those annoying Windows event sounds alongwith "sweet home alabama". If this were the only thing that kmixer was doing, it won't be so bad except that the kmixer resamples everything, just to make it easier for it to mix all those audio streams. It also fiddles with signal to noise ratio and does [many other undesirable](http://www6.head-fi.org/forums/showthread.php?t=77185) things. The end result is that the audio stream comes out sounding very flat and dull. So we need to find a way to bypass this mixer thing and send the audio stream directly to the soundcard. Enter kernel streaming.

Download this [plugin](http://www.cs.indiana.edu/~cshei/out_ks.dll) and just copy it to 'C:\\Program Files\\Winamp\\Plugins'. Then choose 'kernel streaming' under Output preferences. There are no settings for this plugin (as yet). Since it bypasses the kmixer, the winamp volume control won't work with this plugin. You have to use that little speaker icon in the task bar. This is also way too loud at normal volumes, so keep the volume to a minimum when you try it for the first time. In some cases, when you double click on a file after choosing kernel streaming, the winmap might quit. This is normal. Just relaunch the winamp and it should run fine from there on.

**Output:** This section applies only if you have Creative soundcard or a soundcard based on 10K2 chipset. After a mp3 files gets decoded by winamp, it gets fed to soundcard drivers. These drivers make sense of this audio data and convert it to a format suitable for the soundcard to play. But the drivers supplied by Creative are a bit crappy and bloated. So head over to kxproject homepage and download these [drivers](http://kxproject.lugosoft.com/index.php?language=en). These drivers have a cleaner sound ouput and are much more stable than the stock ones. You also gain much more control over your soundcard settings.

**Ears:** Finally, the most critical link in the sound quality chain - the ears. If you cannot tell the difference between an MP3 file and the original CD, don't despair. Most people can't. It takes time and practice and a really good audio setup to hone the listening skills. I leave you here with some [commentary](http://www.fix-it.org/thread418.html) from an audiophile who does not just hear music, but actually listens to it. Be inspired!

**Credits:** The article that made me interested in all this fiddling is [here](http://www.fix-it.org/thread441.html). It deals specifically with foobar2000 but the concepts are same. Infact foobar2000 comes with kernel streaming preloaded. If you can stand its UI, it is said to be the best audio player around.
