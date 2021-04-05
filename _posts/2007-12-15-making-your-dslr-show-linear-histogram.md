---
title: "Making your DSLR show Linear Histogram"
date: "2007-12-15"
categories: 
  - "photography"
  - "software"
---

In addition to having greater flexibility during post-processing, one of the main reasons for shooting raw is to capture greater dynamic range. But if you are relying on the histogram on your camera’s LCD to judge exposure, you may not be capturing the full dynamic range that your camera is capable of.

**The Problem:** The histogram shown on the LCD of a digital camera is based on the gamma-corrected jpeg image and not on the linear raw data. This is true even if you are shooting raw. It is not possible technically to create this histogram from raw data because raw data is unusable until it is processed and converted into an image. Since the raw files typically have an exposure latitude of one f-stop and the blown out highlights can be recovered easily in the raw converter, we don’t want the in-camera histogram to treat this as over-exposure. Otherwise we’d be doing negative exposure compensation to get a pleasing in-camera histogram and thus losing valuable shadow detail. In other words, instead of following ‘Expose to the Right (for jpeg)’ (ETTR) principle, we want to follow ‘Expose to the Right (for raw)’. We want to push the shadows as far to the right as possible without _really_ blowing out the highlights. And we want to do this because the way a digital sensor works, shadows are given very little importance when compared to highlights.

**Human Vision vs. Sensor Vision:** Imagine you are sitting in a room where there is one light bulb of 100w burning. You can see things around you and the room appears to be at a certain level of brightness. Now, if a second 100w bulb is turned on, the room appears brighter but it does not appear twice as bright. You’d need lot more bulbs to make the room appear twice as bright. The same is true of human ears when it comes to listening ability. Doubling the sound pressure does not make the music sound twice as loud. This relationship between the actual light intensity and perceived light intensity is said to be logarithmic in nature. In other words, an increase in physical stimuli does not produce an equal increase in its perception. This relationship is described in mathematical terms by [Weber–Fechner law](http://en.wikipedia.org/wiki/Weber-Fechner_law) or [Stevens' power law](http://en.wikipedia.org/wiki/Stevens%27_power_law).

On the other hand, digital sensors (CCD or CMOS) in our digital cameras are linear. Doubling the ambient light will make things appear twice as bright to the digital sensor. This is an important point as the raw files in our digital cameras store linear data.

**Linear Data:** The digital sensor in our cameras being linear, the raw files produced by them are also linear. The brightest f-stop in a linear file is twice as bright as the next f-stop and thus requires twice as many levels. In a 12-bit raw file, there are a total of 4096 brightness levels. That means that the brightest f-stop has 2048 levels in it, the next f-stop has 1024 levels and so on. The deep shadows in this linear file will have only 16 levels! Imagine the banding that will occur if you try to open up these shadows. Thus the brightest f-stop has far more levels in it than our eyes can perceive while the lower f-stops have far fewer levels than required. This non-uniform distribution of luminosity data can be fixed by applying gamma correction on the linear data.

**Gamma:** A _cathode-ray tube_ (CRT), which is used in the computer monitors, is inherently non-linear. The intensity of light reproduced at the screen of a CRT monitor is a non-linear function of its voltage input. This relationship between the input voltage and the output intensity is described by a parameter called gamma. To compensate for this non-linearity, the input signal to a CRT is encoded in such a way so as to make the light produced by the monitor perceptually uniform. This is called [gamma correction](http://steve.hollasch.net/cgindex/color/gamma.html).

As it turns out, the non-linearity of our eyes is very nearly the inverse of non-linearity of CRT. Thus gamma-correcting a raw image (converting to jpeg) not only takes care of the CRT non-linearity, it is also the best perceptual encoding for visual data. It makes the best use of limited bits (8 bits or 255 levels) available to achieve the most appealing visual reproduction. MP3 encoding does the similar thing for audio data. Note that it’s only the input to the CRT (jpeg on the hard disk) which is gamma-corrected. Once an image is displayed on the CRT screen, it’s as good as seeing the image subject in real life. It is this gamma-corrected image from which the LCD histogram is derived.

**LCD Histogram:** To create an in-camera histogram out of raw data, four things have to be done. First, the raw data has to be [de-mosaiced](http://en.wikipedia.org/wiki/Demosaicing), and second, a color space has to be imposed on it. The third step is to apply gamma correction. If a histogram were to be plotted at this stage, it would be bunched up to the left because even though the brightest f-stop occupies half the total number of levels (2048 in a 12-bit raw file) and thus the complete right half of the histogram, there are very few pixels in it. This is true for typical images which comprise mostly of mid-tones and do not contain much shadow or highlight data. This is the histogram (from linear data) that we are after.

The fourth step is to apply all other settings like sharpening, contrast, saturation etc. and create a jpeg image. This jpeg image is then used to plot the in-camera histogram. This histogram looks very different from the linear histogram because gamma correction spreads the luminosity data uniformly (perceptually) across the tonal range. As long as the linear histogram does not show highlight clipping, we are ok even though the gamma-corrected version might indicate that clipping is happening.

So all we need to do to get a linear histogram is get rid of gamma correction and we can do that through custom curves (on Nikon cameras at least).

**Custom Curves:** Most of the Nikon DSLRs have the option to upload a custom tone curve to be applied to the jpeg images and hence to the in-camera histogram. The custom tone curve (or the default tone curves for that matter) is comprised of two parts – an implicit gamma correction and the actual tone manipulation. All the tone curves work on gamma corrected images by default. What we are looking for is a tone curve, which:

1. Does not apply gamma correction so that our data stays linear, and
2. Does not apply any tone manipulation so that the linear data stays pristine.

Enter ToneUp Studio.

**Applying a Custom Curve:** [ToneUp Studio](http://www.toneupstudio.com/) is a raw converter written by Todd Gibbs, and indie software developer. For all of $14 dollars, it not only provides custom curve uploading, but also tethered shooting (only for Nikon cameras). And you have the option to use Nikon SDK so that you see your images exactly as Nikon intended. Here is what is to be done to make your camera show raw histogram using ToneUp Studio (This feature is available only in latest beta as of now).

I have tested this process on D80 and it should work fine on other Nikon cameras too. Please do check the camera compatibility list on the author’s website.

1. Put your camera in PTP (Picture Transfer Protocol) mode instead of USB mass storage mode and turn it off.
2. Connect your camera to your computer with the USB cable and turn it on.
3. Launch ToneUp Studio. You have to connect your camera _before_ you launch this software otherwise it won’t recognize the camera.
4. Go to Edit-> Preferences and enable the option to “Disable Gamma curve when uploading curves”.
5. Go to File->New Curve. A new window with a straight line curve will be displayed. Choose File->Upload Curve. A progress bar will be displayed while the custom curve gets uploaded to the camera.
6. Turn off your camera and disconnect.
7. In your camera menu, choose Optimize Image->Custom Tone curve.
8. Shoot.

That’s it. The images on your camera’s LCD will appear too dark but that’s ok. When you open your images in a raw converter, this custom curve will get ignored and you’ll see a normal (gamma corrected) image. If it looks over-exposed, just use the highlight recovery slider and bring back the detail. If you are using Capture NX or any other Nikon SDK based software, just choose a different tone curve.

**Credits/Links:**

1. [ToneUp Studio](http://www.toneupstudio.com/)
2. [Expose to the Right](http://www.luminous-landscape.com/tutorials/expose-right.shtml)
3. [Exposing for RAW](http://www.digitalphotopro.com/tech/exposing-for-raw.html)
4. [Weber-Fechner Law](http://en.wikipedia.org/wiki/Weber-Fechner_law)
5. [Steven's Power Law](http://en.wikipedia.org/wiki/Stevens%27_power_law)
6. [Gamma Correction](http://steve.hollasch.net/cgindex/color/gamma.html)
7. [Gamma FAQ](http://www.poynton.com/GammaFAQ.html)
