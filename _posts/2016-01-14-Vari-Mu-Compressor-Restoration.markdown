---
layout: post
title: Vari-Mu Compressor Restoration
date: 2016-1-14 11:20 
description: My friend Reid gave me a tube compressor...
thumbnail: /img/webster/websterThumb.jpg
comments: True
---

My friend Reid called me up the other day and asked if I wanted to help him clear out his audio junk drawer. I rarely pass up such opportunities, and he had all sorts of oddball cables, tubes and old crystal mics for me, but I wasn't expecting him to give me this:

![webster1](/img/webster/webster1.jpg)

It's an old Webster Electric 515 Vari-mu compressor with a 516 mic pre module. Wisconsin made, to boot - Webster was located in Racine. The documentation just states that it is for use "in a sound system," but it has a telephone input channel, which suggests broadcast or paging. The transformers look pretty nice:
 
![webster2](/img/webster/webster2.jpg)

Of course looks can be deceiving, but I wouldn't be surprised if this thing sounds pretty good. I found a <a href="https://www.gearslutz.com/board/attachments/so-much-gear-so-little-time/361859d1378597678-webster-wsc-681-515-vintage-compressor-photo-3.jpg">schematic</a> on gearslutz. It's pretty straightforward:

![schematic](/img/webster/schematic.jpg)

The input is transformer coupled to a triode-connected EF-86 pentode. Theres a little mixer circuit that blends the mic and telephone inputs, which then feeds a 12AU7, with one half connected as a gain stage, and the other as a cathode follower that drives the coupling transformer between the mic pre and the compressor. The telephone transformer is pretty dinky - you can see it tucked away in the image below - but who knows, maybe it will saturate in a cool sounding way. 

![micPre](/img/webster/webster6.jpg)

The compressor has a simple feedback design - the output feeds two diodes, which rectify and provide a negative the control voltage. That goes to an RC filter, which smooths the control voltage and provides a fixed attack and release times of 35 ms and 1 second, according to the documentation. The control signal is fed to the grids of the 6BZ7, which serves as the variable gain element. The data sheet describes it as a VHF cascode amplifier, but looking at the plate characteristics, I can see how it could operate as a variable gain amplifier:

![eqWindow](/img/webster/tubecurve.jpg)

The schematic gives a power supply voltage of around 200 volts, and a plate voltage of around 58 volts, which corresponds with an operating current of about 3 mA, given the DC load of 51k on each section of the 6BZ7 (blue load line). This puts the operating point somewhere near the red dot. The AC load is closer to 23k, represented by the green line. At this point, the tube should have a gain of around 30. But as the output signal increases, the control voltage moves the 6BZ7's grid into increasingly negative territory. At a grid voltage of -4 volts, the tube looks to have a gain of around 12, which would correspond to gain reduction of around \(20\log_{10}(12/30)\) or -8 dB. There's more going on, though, as the plate resistance of the 6BZ7 rises rapidly at low currents, further reducing its gain. The tube curves are so scrunched together at this point, they're probably not the most reliable way to make these sorts of estimates. The documentation states that the maximum gain reduction is 30 dB. I would imagine there is a lot of signal asymmetry, and hence distortion, at high levels of gain reduction, which probably explains the balance control - if the two legs of the balanced circuit have identical gain, many of the distortion components (even order harmonics, if I'm not mistaken) will cancel out. Anyway, that's my brief take on the theory of operation. 

There are quite a few very old electrolytic capacitors in this beast, and it's likely they will all need to be replaced. It isn't visible in any of the pictures, but some of them are blistering a bit, which is always a bad sign. I also wouldn't be surprised if the GR meter no longer works. Other than that, it looks pretty nice - good old point to point wiring. 

![tool](/img/webster/webster5.jpg)

There are a number of mods that could be performed on this unit, and I'm a bit torn on that front. On the one hand, it's a vintage tube pre/compressor - why not just let it be what it is? I see no need to fill it with polypropylene capacitors and ultra low-noise resistors. On the other hand, it would be nice to have the compressor bypass switch on the front panel, and it would be pretty easy to add a couple more time constants to the CV circuit. An output control would be cool as well - it would be nice to be able to drive it hard and back off the output. The specs for the pre give a frequency response for the compressor that is pretty respectable: +/- .6 dB, 30 - 20,000 Hz. The pre is less impressive: -.8 to 0 dB, 100 - 10,000 Hz. Pretty rolled. I would guess that's almost certainly a function of the input transformer, which is probably cheap. It might be worth it to put a good one in. Another possibility would be to convert the EF86 to pentode operation, which lowers the miller capacitance, and *might* improve the high frequency response. Lot's of possibilities... 

I'm going to get the Webster up and running before I delve into any mods. Who knows - it may sound cool as it is, in which case it's probably better to leave well enough alone. 