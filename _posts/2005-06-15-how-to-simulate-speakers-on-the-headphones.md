---
title: "How to simulate speakers on the headphones."
date: "2005-06-15"
categories: 
  - "audio"
---

One of the reasons that we have two ears (or two eyes) is that it allows us to experience this world in three dimensions. We can see just fine with one eye but we need two eyes to gauge the depth of the scene. Similarly, two ears allow us to have spatial hearing. I.E we can localize the source of the sound. We can figure out whether the sound is coming from left or right, from up or down etc.

Say we are listening to some music being played on a speaker. Typically, the sound from the speaker would reach one of the ears earlier than the other (far) ear. This is because our ears are separated by about 10 inches and sound has a finite velocity. This time difference is called Interaural Time Difference (ITD) and is generally in microseconds. And the ear closer to the speaker would receive the sound waves directly, making the signal level at this ear slightly stronger than the far ear. This difference in level is called Interaural Level Difference (ILD). Together, ITD and ILD allow us to localize the azimuth (angle in the plane) of the sound source. These are also called binaural cues since these involve both the ears. We cannot determine the elevation of the sound source using just these cues though.

The sound that comes out of the speaker and the sound that we hear are not the same. Several things affect the sound before it can be heard by us. The distance of the speakers from the ear, shape of our head, the structure of our outer and inner ear, the angle at which the sound waves strike the ear, indirect sound from reflections off the walls etc. All these influences on the sound waves are collectively called as head related transfer functions (HRTFs). Mathematically, HRTF is the impulse response of the medium that carries the sound. These HRTFs allow us to determine the elevation of the sound source. These are also called monaural cues.

But what happens when both ears receive the same level of sound at the same time and there are no external influences on the sound? Since both ITD and ILD are zero and HRTFs are absent, there is no information to localize the sound. So the sound seems to come from the center of the head. This is what happens with the headphones. Our brains loses all its localization clues and constantly tries to figure out where the sound is coming from. This results in fatigue and uneasiness, the extreme case of which happens when we listen with only one headphone (right or left). Speakers, on the other hand, sound much more natural and pleasant since brain has all the information needed to figure out the spatial location of the sound. And all the music itself is recorded in such a way that it would sound most plesant when played back on speakers only.

So if we have to simulate the speakers on the headphones, all we have to do is make ITD and ILD non-zero and introduce some HRTFs and we are set. One of the best Winamp plug-ins to do this is [Speakers Simulator](http://www.Url.Ru/~copah/speakerssimulator.Htm) by Vladimir Kopjov.

**Interaural level difference (ILD):** When listening to speakers, both ears receive the sound from both the speakers. But in case of headphones, left ear receives the sounds only from the left channel and right ear receives the sound only from the right channel. To simulate this on headphones, we have to take a bit of left channel and send it to right ear and vice versa. This is called 'crossfeed'. Its value varies from 0 to 80% in the above plug-in, default being 70%. The higher the crossfeed, the stronger the localization but lesser scene width.

**Interaural time difference (ITD):** The sound coming from, say, left speaker would reach the near ear earlier than the far ear. To simulate this in headphones, the signal that is cross fed is also delayed by a small amount, the delay being roughly equivalent to what would be realized in practice. In the speaker simulation plug-in, the default setting for delay is 113.38 microsecond. More delay gives more scene width but less focus. If increased too much, this delay can cause some sound artifacts.

**Head related transfer functions (HRTFs):** This is one of the most difficult parameters to measure because of interaction of so many different factors and different head/ear structures in different people. Lord Rayleigh modeled it assuming our head to be a perfect sphere and using wave propagation equations along a curved surface. The results show that the high frequencies get attenuated much more as they travel than the low frequencies. Though they are mathematically complex, the HRTFs are really easy to simulate. All we have to do is make the high frequencies roll off gradually and we'll get the same effect as the speakers. And unless your headphones cost $500 or more, it already has this desired frequency response (it is not so by design but rather from a desire to keep the costs down). So just make sure that the equalizer in winamp is flat for high frequencies. My Winamp equalizer looks like this.

> ![](images/19475242_4edca6396e.jpg)

The effect of speaker simulation plug-in is very subtle. It doesn't seem to have much effect in beginning, but after a few hours of listening, the difference is clear as day and night. And, of course, it is much more pleasant this way and you can listen for longer periods of time without having any fatigue.

**Credits:**

1. [Sound Localization Using Head Related Transfer Functions](http://www-ece.rice.edu/~crozell/courseproj/431report/)
2. [Speakers Simulator](http://www.headwize.com/projects/showfile.php?file=kopjov_prj.htm) plug-in
3. [Sound localization](http://en.wikipedia.org/wiki/Sound_localization) on Wikipedia
4. [Comments](http://www.hydrogenaudio.org/forums/index.php?showtopic=34452&st=0&p=303642&#entry303642) by Chris on HydrogenAudio forums

**Update:** After trying out various other plug-ins, I have finally settled on [4Front Headphones](http://www.yohng.com/headphones.html). It does not apply as much equalization as Speaker Simulator so the sound is more or less unchanged. It also gives much better stereo imaging and puts the sound directly in front of you. The default setting of 30% gives a very distorted and artificial sound but at 10%, it sounds superb.
