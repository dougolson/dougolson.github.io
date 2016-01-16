---
layout: post
title: Vari-Mu Compressor Restoration
date: 2016-1-14 11:20 
description: My friend Reid gave me a tube compressor...
comments: True
---

<img class = "post-thumb" src="/img/AudacitySpectralEQ/3.png" height="120" width="120">My friend Reid called me up the other day and asked if I wanted to help him clear out his audio junk drawer. He had all sorts of oddball cables and old crystal mics for me, but I wasn't expecting this:
 ![webster1](/img/webster/webster1.jpg)

The track view will switch to a spectrogram. You can see where the Oboe comes in, and where it's unique harmonics are. 

![spec1](/img/AudacitySpectralEQ/3.png)

<audio controls><source src="/audio/WaterGlassOboeMix.mp3" type="audio/mp3" preload="auto">
Your browser does not support the audio tag.
</audio><br/> 

I changed a few settings in the preferences for the spectrogram. For better frequency resolution, I set the window size to the maximum, and went with a rectangular window. Otherwise, I left the default settings in place
![specSettings](/img/AudacitySpectralEQ/3a.png)

Next, from the Effect menu, you need to select "Spectral edit parametric EQ"

![eqMenu](/img/AudacitySpectralEQ/4a.jpg)

There's not much to adjust in the effect itself. I went with -24 Db, the maximum cut. 

![eqWindow](/img/AudacitySpectralEQ/5.png)

Finally, you want to use the Selection tool:

![tool](/img/AudacitySpectralEQ/6.png)

At this point, it's simply a matter of making a time selection, adjusting the height of the horizontal window that controls the filter, and then applying it to each harmonic you want to remove. There are a few things to remember and a few tricks you can use:

* The height of the spectral selection controls the width of the filter
* If you mouse over the frequency scale on the left, you'll get a zoom tool, allowing you to really fine tune the selection
* To zoom back out, right click with the zoom tool active
* Sometimes it is necessary to apply the filter more than once
* Use Command-R to repeat the filter effect and avoid a lot of mousing

![surgery1](/img/AudacitySpectralEQ/7.png)

Zoomed in:
![surgery2](/img/AudacitySpectralEQ/8.png)

Here's what a harmonic looks like before and after the application of Spectral EQ:

![beforeAfter](/img/AudacitySpectralEQ/beforeAfter.jpg)

In general, I made all my selections span the entire length of the clip, reasoning that it would be more sonically transparent / consistent to filter everything, rather than just filtering where the Oboe plays. There was one harmonic that seemed to be associated with the attack of the Oboe, and in that case, I selected it specifically:

![surgery3](/img/AudacitySpectralEQ/9.png)

After selecting and attenuating each Oboe harmonic - a somewhat tedious process - the final result looks like this:

![final](/img/AudacitySpectralEQ/10.png)

And sounds like this. The Oboe is almost completely inaudible, other than a bit of the initial transient and the noise component:

<audio controls><source src="/audio/WaterGlassOboePostEQ.mp3" type="audio/mp3" preload="auto">
Your browser does not support the audio tag.
</audio><br/>

I was really pleased to see such a powerful tool on a free, open source application. I'm looking forward to learning more about Audacity. 