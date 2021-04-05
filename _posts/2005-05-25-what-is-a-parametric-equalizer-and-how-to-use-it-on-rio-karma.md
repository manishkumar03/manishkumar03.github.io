---
layout: post
title: "What is a Parametric Equalizer and how to use it on Rio Karma."
date: "2005-05-25"
categories: 
  - "audio"
---

In it's simplest form, a speaker is just an energy conversion device. It converts electrical signals to sound waves of various frequencies. Ideally, all the frequencies in the speaker output should be at the same level of loudness. If we plot the frequency repsones curve of such an ideal speaker, with frequency (in Hertz) on x-axis and loudness (in Decibals) on y-axis, it would be a flat line at 0db. But such ideal speakers don't exist. It's really really difficult to construct such an ideal device. Even if it could be built, it would be too expensive to be practical. That means that we are stuck with ordinary speakers that don't sound so great, atleast not without some tuning.

The frequency response of an ordinary speaker looks like the outline of a mountain. I.e. the low and high frequencies are not amplified as much as the middle ones. My Sennheiser MX500 headphones have this frequency response, taken from [Headroom](http://www.headphone.com/):

![](images/15587761_3ad9128bdf.jpg)

The sole purpose of an equalizer is to compensate for this bias in the speakers. It brings all the frequencies to the same level of loudness. In other words, it equalizes them and hence the name "Equalizer".

Equazliers on sotware based players (Winamp, iTunes etc.) are typically 10-band and those on digital audio players are typically 5-band. A typical 10-band equalizer:

![](images/15588413_0995b16fe9_m.jpg)

The frequency shown under each bar is called the center frequency. Just as there are no ideal speakers, there is no ideal equalizer either. I.e. instead of being a straight vertical line, each of these bars is more like a bell. And the range of frequencies falling under this bell is called a frequency band. So a 10-band equazlier can amplify/attenuate 10 separate, but overlapping, frequency bands. Because these bands extend to some distance on either side of center frequency, boosting the center frequency actually boosts this whole band, with the effect being maximum at the center frequency.

In a normal equalizer, the only thing that a user can control is the amount of amplification for each band. But in a parametric equalizer, in addition to the amplification, you can also change the center frequency and the width of each band. This additional level of control comes in handy when matching a pair of headphones to a particular device. I have set the Equalizer on my Rio Karma as:

<table width="80%" border="0"><tbody><tr><td><strong>Center frequencyuency</strong></td><td><strong>Gain</strong></td><td><strong>Width</strong></td></tr><tr><td>12000 Hz</td><td>+6.0 db</td><td>4.0 octaves</td></tr><tr><td>2500 Hz</td><td>+0.0 db</td><td>4.0 octaves</td></tr><tr><td>500 Hz</td><td>-2.0 db</td><td>4.0 octaves</td></tr><tr><td>150 Hz</td><td>+6.0 db</td><td>4.0 octaves</td></tr><tr><td>40 Hz</td><td>+8.0 db</td><td>4.0 octaves</td></tr></tbody></table>

This setting makes MX500 give an almost flat response when used with Rio Karma. The nice player that the Karma is, it offers 3 custom equalizers. So I have set the other one to match my Philips HP800 cans (Based on subjective tests, since I could not find the frequency response curve for it).

To match your headphone to Rio Karma, you need the frequency response curve of Rio Karma and a way to see how your headphone and Rio karma interact at various equalizer settings. This is exactly what [John M](http://groups.msn.com/JohnMKarmaEQ/) has done with his KarmaEQ application. But the headphone response curve given by headphone.com is not usable as it is. It has to be converted to a text file having frequency-gain pairs. There are many examples of this on John's site. I created a file with 30 sets of frequency-gain pairs for Sennheiser MX500. The values don't have to be highly precise. Just a simple eyeballing would do.

Now all that you have to do is import your headphone response file in the KarmaEQ and start experimenting. The idea is to have the resulting curve as flat as possible. When you are satisfied with the results in KarmaEQ, try that in Rio Karma and see how it sounds. Since sound quality is a subjective thing, the flat curve may not be up to your liking. But take that as the starting point and explore from there on. Happy EQing.

**Update:**The [HydrogenAudio thread](http://www.hydrogenaudio.org/forums/index.php?showtopic=34452) on this post contains lot of interesting points on the differences between listening on headphones and listening on speakers. A highly recommended reading. Also my Rio Karma is dead :-(. I did everything I could but it just won't boot. Well..
