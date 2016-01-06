---
layout: post
title: Audio Surgery with Audacity
date: 2015-12-26 22:20 
description: Audacity's powerful spectral EQ feature
comments: True
---

<img class = "post-thumb" src="/img/AudacitySpectralEQ/3.png" height="120" width="120">I recently spent some time playing around with the latest version of Audacity, and was quite surprised by how powerful some of its features are. One of the most impressive is spectral EQ. It is quite easy to use, and it is very precise. And Pro Tools doesn't have it (let alone even a basic spectrogram!). Adobe Audition has some very nice spectral tools, but it's not free.

Anyway, here's an example of how you can use spectral eq to almost completely separate two sounds that have been mixed together. Not all sounds can be separated this way, of course - if the harmonics overlap too much, the sounds will be altered a lot in the process. But many sounds can be separated, and less extreme applications of spectral eq can be found all over - a guitar arpeggio with one note that is too loud, for example. For this demonstration, I put together an admittedly odd sound - a water glass mixed with an oboe - using files obtained on <a href="http://www.freesound.org">freesound.org</a>. Probably not something you're going to hear in a dubstep remix, but it works well for the present purpose. Here it is:

<audio controls><source src="/audio/WaterGlassOboeMix.mp3" type="audio/mp3" preload="auto">
Your browser does not support the audio tag.
</audio><br/> 

We're going to use Spectral Selection, which can be found in the Mix menu found at the top left of the track in question.

![waveform](/img/AudacitySpectralEQ/1a.jpg)

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