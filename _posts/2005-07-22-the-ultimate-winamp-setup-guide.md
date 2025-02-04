---
layout: post
title: "The ultimate Winamp setup guide!"
date: "2005-07-22"
tags: 
  - "audio"
---

When we call someone an "audiophile", we generally mean that the guy spends insane amounts of money on the audio gear. This is a wrong defintion, and a derogatory one too. To me, an [audiophile](http://www.chesky.com/core/body_librarydetails.cfm?newsid=160) is someone who is passionate about music. Who cares about music enough to invest in high quality gear. But it does not mean that we can't be audiophiles if we don't have all the high-end stuff. All it takes is right set of tools and a little bit of fiddling around.

A typical audio path looks like this: CD --> Encoder --> Winamp (Decoder) --> DSP --> Kmixer --> Soundcard --> Headphones Let's see what we can do to optimize each stage.

**Encoder:** If most of your music comes from internet and other sources in MP3 form, there is nothing you can do about its quality. But if you rip the CDs yourself, read on. MP3/OGG/AAc sound great but why lose quality when you can rip to a lossless format. These lossless formats are really lossless. These are like winzip for audio. You get back the exact same data, with each and every bit intact. The lossless formats do take more space (5 MB for MP3 vs 25 MB for FLAC) but with harddisk space being so cheap, there is no reason to lose quality. The best and most popular foramt for lossless audio is [FLAC](http://flac.sf.net). I use [Yahoo music engine](http://music.yahoo.com/musicengine) to rip the CDs to FLAC and [this plugin](http://www.facquet.com/rubrique66.html) to play it in Winamp. Even though a few of the portable audio players support this format, it is not yet widely available on DAPs. So if your player does not support FLAC and if DAP is your primary source of music, you'd be better off with MP3. Just make sure that you use a high enough bitrate (192 kbps or greater) and LAME to encode. Some people claim that AAC has better quality at same bitrates but I can't vouch for that. These are more like Nikon vs Canon debates.

**Decoder:** The built-in MP3 decoder in winamp has been licensed from FhG which is pretty decent but not the best sounding one. We need something that can do dithering and noise shaping. I would use foobar but iZotope Ozone does not work with that. Fortunately, there is [MAD plugin](http://www.mars.org/home/rob/proj/mpeg/mad-plugin/) which does all this and it is free too. I must say that the difference in the decoders is very subtle and for the most part, insignificant. It is more of a purist thing. You should be ok with stock Winamp decoder.

**DSP:** The next step in the chain is signal processing. This includes things like equalizer, normalizer, and other sound enhancing plugins. It takes a really good understanding of audio fundamentals to not screw up the sound with these things. You can either read tomes on this subject and try to play around with the settings yourselves. This is like using layers and masks and whatnot in photoshop to sharpen the picture where Photokit Sharpener can do a much better job at the press of a button. In other words, leave it to the pros. And the best DSP plugin for Winamp is by iZopte called [Ozone](http://www.winamp.com/plugins/details.php?id=79374). The basic plugin is free but it is so good that you'd never miss the pro version. I brings out the details in the music that you never even knew about. Especially in the mid and high frequency range. The music sounds more lus and the instrument separation improves to a remarkable degree. Listen to a well mastered CD like Gladiator or "The passion of the Christ" with and without this plug-in to fully appreciate it.

You don't need any other plugin with this, not even Winamp equalizer. I just leave the settings at default for both headphones and speakers. If you start experiencing listening fatigue on headphones, try switching to headphone preset. This mode adds a little crossfeed and HRTFs to make you feel as if you are [listening to speakers](http://manishbansal.blogspot.com/2005/06/how-to-simulate-speakers-on-headphones.html). Or if you don't like too much zing in your music, try the preset with less sparkle. I found that default mode gives me the purest sound. Just play aroud with different presets and see what you like.

To use iZotope Ozone with foobar, you can use [bridge DSP plugin](http://pelit.koillismaa.fi/plugins/dsp.php#87) for Winamp. This allows you to use DSP plugins written for Winamp in foobar.

**Kmixer:** The signal coming out of DSP goes into a Windows component called kmixer. All it does is mix different audio streams so that two or more applications can play back audio at the same time. It does something else too. It resamples everything to 48 KHz (the native audio data is at 44.1 KHz) which results in a slight loss of quality. We can bypass this thing by using an output mode called 'Kernel Streaming'. It is more of a hack (experimental feature) to support applications that need very low-latency. This [plugin](http://www.cs.indiana.edu/~cshei/out_ks.dll) does not support buffering (as of now) so the music might skip if you use your PC too heavily while Winamp is running. It should be fine for normal use though. In case you are not happy with KS, use directsound for Win 2K and XP and waveout for Win98/ME. **Update**(Mar 04, 2005): The updated version of kernel streaming plugin can be found at [Steve Monk's homepage](http://www.stevemonks.com/). It supports buffering for both input and output now.

**Soundcard:** This is one of the most misunderstood pieces of hardware. Everyone knows that a Geforce4 is better than Geforce2 video card. You get much better frame rates and almost realistic texture. But a better soundcard? What could a better soundcard do? Play music faster?

Explaining what a good soundcard can do is like explaining color to a blind person. You have to listen to a good setup to really appreciate it. Try not to buy a Creative soundcard. These cards have been optimized for gaming with EAX effects and other 3-D trickery. You want a card built specifically for audio. Chaintech AV-710 and M-audio revolution cards are cheap and one of the best in this category.

If nothing else is available, Creative Soundblaster is a pretty decent solution. Just make sure that you turn off all the so called sound enhancing settings in the soundcard driver.

**Headphones:** Much of what has been said about soundcards applies to headphones too. In fact, having a better headphone is more important than having a better soundcard because ear drums are a precious thing. Once damaged, they stay that way. Better buy a decent headphone and treat them nice.

A word of caution: Do not go overboard in trying to get better sound. Do not give the term audiophile its common misunderstood meaning. Listen to the music for music and become a real audiophile.

Peace!
