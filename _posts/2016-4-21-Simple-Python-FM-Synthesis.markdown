---
layout: post
title: Simple Python FM Synthesis
date: 2016-4-21 10:27 
description: A very basic exploration of FM synthesis
comments: True
---

<script src='https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML'></script>
A student of mine showed me the Native Instruments FM8 Virtual Instrument the other day - it's an amazing piece of software. I have to admit two things, though. First, I've never been all that wild about the FM synth sound, which I associate with chimey '80s keyboards like the Yamaha DX7. Second, probably as a result of my general lack of enthusiasm for the FM sound, I've never taken the time to learn how FM synthesis actually works. The FM8 sounded really cool though, and it piqued my curiosity. So I printed out a copy of the 1973 article "The Synthesis of Complex Audio Spectra by Means of Frequency Modulation," by John Chowning, and read up. It gets into some pretty heady math, but at the bottom of it all is a simple formula that is easy to implement in software: 
\\[sin(2\pi{}f_c + \beta sin(2\pi{}f_m))\\]

In essence, a carrier frequency \\(f_c\\), a modulation frequency \\(f_m\\) and a modulation index \\(\beta\\) interact to generate a wide variety of harmonic and inharmonic sounds. Looking at the equation, it's clear that if \\(\beta = 0,\\) the result is simply the carrier frequency. As \\(\beta\\) increases, the modulator "steals" energy from the carrier and spreads it around to side bands. The FM8 takes the above and adds multiple layers, so that one FM sound can be the carrier for another, and that sound can in turn be the carrier for yet another sound, and so on, up to eight layers deep. In addition, at each layer, filters, LFOs and envelope generators can be applied, making it incredibly flexible. I may have to buy one.

In the meantime, I'll have to settle for my very humble Python version, which can only generate single notes in not-real time, but which is still fun to play around with. 


{% highlight python %}
import os
import numpy as np
import matplotlib.pyplot as plt
from scipy.io.wavfile import read, write
from scipy.signal import argrelextrema
from IPython.display import Audio
import warnings
warnings.filterwarnings('ignore')
%matplotlib inline
{% endhighlight %}


{% highlight python %}
class FMsynth(object):
    """
    Simple FM_Synth object for experimentation.
    Defaults: f_carrier = 220, f_mod =220, Ind_mod = 1, length = 5, sampleRate = 44100
    if f_carrier/f_mod = N1/N2 and N1, N2 are integers, harmonic spectra will result
    if N1/N2 is irrational, i.e. sqrt(2) or pi, inharmonic spectra will result 
    f_0, the fundamental = f_carrier/N1 = f_mod/N2
    # k_th harmonic = N1 + n*N2 for n = 0,1,2,3,4,...
    # so for f_carrier = 100 and f_mod = 300, harmonics are [100, 400, 700, 1000, 1300, 1600, 1900, 2200, 2500, 2800] etc
    """
    def __init__(self, f_carrier = 220, f_mod =220, Ind_mod = 1, length = 5, sampleRate = 44100, waveFile = True):
        self.increment = .01
        self.f_carrier = f_carrier
        self.f_mod = f_mod
        self.Ind_mod = Ind_mod
        self.rate = sampleRate
        self.ident = id(self)
        self.name = '%dHz_carrier-%dHz_mod-%s_Index_%d.wav' % (self.f_carrier, self.f_mod, str(self.Ind_mod),self.ident)
        sampleInc = 1.0/self.rate
        x = np.arange(0,length, sampleInc)
        y = np.sin(2*np.pi*self.f_carrier*x + self.Ind_mod*np.sin(2*np.pi*self.f_mod*x))
        mx = 1.059*(max(abs(y))) # scale to max pk of -.5 dB
        y = y/mx
        wavData = np.asarray(32000*y, dtype = np.int16)
        self.wavData = wavData
        if waveFile:
            write('audio/%s' % self.name, 44100.0, self.wavData)
{% endhighlight %}


{% highlight python %}
    def FMplot(self):
        """Generates a plot of the waveform for the FMsynth tone being examined"""
        inc = self.increment
        T = 1./self.f_carrier
        x = np.arange(0,T*1.01, T/100.0)
        y = np.sin(2*np.pi*self.f_carrier*x + self.Ind_mod*np.sin(2*np.pi*self.f_mod*x))
        mx = 1.059*(max(abs(y))) # scale to max pk of -.5 dB
        y = y/mx
        plt.plot(y, label = self.name)
        plt.axis([0,100,-1.1,1.1])
        labels = [str(round(1000*n,2)) for n in np.arange(0,T*1.01,T/10.0)]
        plt.xticks([n for n in np.arange(0, 101, 10)], labels)
        leg = plt.legend(fancybox=True)
        leg.get_frame().set_alpha(0.5)
        plt.xlabel('Milliseconds')
        plt.title('Source Waveform')
        plt.grid(True)
        plt.show()
{% endhighlight %}


{% highlight python %}
    def FM_fft(self):
        """performs an fft and plots the result"""
        rate = self.rate
        data = self.wavData
        T = 1.0/rate # sample period
        N = len(data) # N samples
        xfft = np.linspace(0.0, 1.0/(2.0*T), N/2) # x axis
        yfft = np.fft.rfft(data) # perform fft
        yfft = 2./N*np.abs(yfft[0:N/2])#/pkfft # scale and filter out negative frequency component
        yfftPk = max(yfft) # magnitude of strongest partial
        yfft = yfft / yfftPk
        yfftLog = np.where(abs(yfft)>0, 20*np.log10(abs(yfft)), -101)
        plt.plot(xfft,yfftLog)
        plt.ylim(-100,0)
        plt.xlim(0,5000)
        plt.grid(True)
        plt.title('FFT of %s' % self.name)
        plt.show()
{% endhighlight %}

A simple example: 220 Hz carrier, 220 Hz modulation frequency, modulation index of 1


{% highlight python %}
FM1 = FMsynth() 
{% endhighlight %}


{% highlight python %}
FMplot(FM1)
{% endhighlight %}


![png](/img/SimplePythonFMSynthesis/output_7_0.png)



{% highlight python %}
FM_fft(FM1)
{% endhighlight %}


![png](/img/SimplePythonFMSynthesis/output_8_0.png)



{% highlight python %}
Audio(FM1.wavData,rate=FM1.rate)
{% endhighlight %}





<audio controls="controls" >
    <source src="/audio/fmsynth/220Hz_carrier-220Hz_mod-1_Index_4586280080.mp3" type="audio/mp3">
    Your browser does not support the audio element.
</audio>



Increasing the modulation index to 10 results in a much more complex waveform and harmonic spectrum.


{% highlight python %}
FM2 = FMsynth(220,220,10)
{% endhighlight %}


{% highlight python %}
FMplot(FM2)
{% endhighlight %}


![png](/img/SimplePythonFMSynthesis/output_12_0.png)



{% highlight python %}
FM_fft(FM2)
{% endhighlight %}


![png](/img/SimplePythonFMSynthesis/output_13_0.png)



{% highlight python %}
Audio(FM2.wavData,rate=FM2.rate)
{% endhighlight %}





<audio controls="controls" >
    <source src="/audio/fmsynth/220Hz_carrier-220Hz_mod-10_Index_4634749776.mp3" type="audio/mp3">
    Your browser does not support the audio element.
</audio>




Using an irrational modulation frequency (\)100*\pi\)) results in a non-harmonic spectrum and a very metallic tone:


{% highlight python %}
FM3 = FMsynth(220,314.159,5)
{% endhighlight %}


{% highlight python %}
FMplot(FM3)
{% endhighlight %}


![png](/img/SimplePythonFMSynthesis/output_17_0.png)



{% highlight python %}
FM_fft(FM3)
{% endhighlight %}


![png](/img/SimplePythonFMSynthesis/output_18_0.png)



{% highlight python %}
Audio(FM3.wavData,rate=FM3.rate)
{% endhighlight %}




<audio controls="controls" >
    <source src="/audio/fmsynth/220Hz_carrier-314Hz_mod-5_Index_4652390736.mp3" type="audio/mp3">
    Your browser does not support the audio element.
</audio>




Plotting the same carrier and modulation frequencies with increasing modulation indeces shows how the harmonic complexity changes with the modulation index. In this example the plots have not been normalized along the Y axis. This makes it easier to see the relative energies of the carrier frequency and the side bands.


{% highlight python %}
def FM_fft2(self):
        rate = self.rate
        data = self.wavData
        T = 1.0/rate # sample period
        N = len(data) # N samples
        xfft = np.linspace(0.0, 1.0/(2.0*T), N/2) # x axis
        yfft = np.fft.rfft(data) # perform fft
        yfft = 2./N*np.abs(yfft[0:N/2])#/pkfft # scale and filter out negative frequency component
        plt.plot(xfft,yfft)
        plt.xlim(0,2500)
        plt.grid(True)
        plt.title('FFT of %s' % self.name)
        plt.show()
{% endhighlight %}


{% highlight python %}
FM_0 = FMsynth(220,220,0,waveFile=False)
FM_1 = FMsynth(220,220,1,waveFile=False)
FM_2 = FMsynth(220,220,2,waveFile=False)
FM_3 = FMsynth(220,220,3,waveFile=False)
FM_4 = FMsynth(220,220,4,waveFile=False)
FM_5 = FMsynth(220,220,5,waveFile=False)
FM_fft2(FM_0)
FM_fft2(FM_1)
FM_fft2(FM_2)
FM_fft2(FM_3)
FM_fft2(FM_4)
FM_fft2(FM_5)
{% endhighlight %}


![png](/img/SimplePythonFMSynthesis/output_22_0.png)



![png](/img/SimplePythonFMSynthesis/output_22_1.png)



![png](/img/SimplePythonFMSynthesis/output_22_2.png)



![png](/img/SimplePythonFMSynthesis/output_22_3.png)



![png](/img/SimplePythonFMSynthesis/output_22_4.png)



![png](/img/SimplePythonFMSynthesis/output_22_5.png)


A little movement can be added to the sound by ramping the modulation from one value to another and using a modulation frequency that is a few hertz from an integer multiple of the carrier frequency.


{% highlight python %}
class FMsynth2(object):
    """Same as FMsynth except a ramp is applied to the modulation index to add some movement to the sound
    """
    def __init__(self, f_carrier = 220, f_mod =220, Ind_mod = 1, length = 5, sampleRate = 44100, waveFile = True):
        self.increment = .01
        self.f_carrier = f_carrier
        self.f_mod = f_mod
        self.Ind_mod = Ind_mod
        self.rate = sampleRate
        self.ident = id(self)
        self.name = '%dHz_carrier-%dHz_mod-%s_Index_%d.wav' % (self.f_carrier, self.f_mod, str(self.Ind_mod),self.ident)
        sampleInc = 1.0/self.rate
        x = np.arange(0,length, sampleInc)
        ramp = [rmp/length for rmp in x]
        ramp = ramp[::-1]
        y = np.sin(2*np.pi*self.f_carrier*x + ramp*np.sin(2*np.pi*self.f_mod*x))
        mx = 1.059*(max(abs(y))) # scale to max pk of -.5 dB
        y = y/mx
        wavData = np.asarray(32000*y, dtype = np.int16)
        self.wavData = wavData
        if waveFile:
            write('audio/%s' % self.name, 44100.0, self.wavData)
{% endhighlight %}


{% highlight python %}
FM6 = FMsynth2(220,443,100)
{% endhighlight %}


{% highlight python %}
Audio(FM6.wavData,rate=FM6.rate)
{% endhighlight %}





<audio controls="controls" >
    <source src="/audio/fmsynth/220Hz_carrier-443Hz_mod-100_Index_4651566288.mp3" type="audio/mp3">
    Your browser does not support the audio element.
</audio>






