---
layout: post
title: Making Sinusoids with Python
date: 2015-12-24 22:10 
description: Getting started with DSP 
comments: True
---

<img class = "post-thumb" src="/img/sinusoids/output_9_0.png" height="120" width="120">I've been spending a fair amount of time lately learning Python, but most of my efforts have been focused on the turtle graphics module. It's a lot of fun, and some of the images I've been able to come up with are quite interesting (to me, at least), but what I really want to do is learn how to do things with audio. So I've started studying DSP. I'm pretty confortable with continuous functions, but discrete functions can be a bit of a challenge at first - indexes, the meaning of frequency and time, etc. With a little practice - which is all this post is - it becomes clear pretty quickly. Along the way, I get some practice plotting with Matplotlib, Numpy and Scipy. First order of business, I want to understand sinusoid generation. The basic equation is:

\\[x(t) = Acos(2{\pi}ft + {\phi}) \\]

Here is a plot of a 5 Hz sinusoid with a phase delay of pi/4 radians


```python
%matplotlib inline
import numpy as np
import matplotlib.pyplot as plt
A = .8
f = 5
t = np.arange(0,1,.01)
phi = np.pi/4
x = A*np.cos(2*np.pi*f*t + phi)
plt.plot(t,x)
plt.axis([0,1,-1,1])
plt.xlabel('time in seconds')
plt.ylabel('amplitude')
plt.show()
```


![png](/img/sinusoids/output_1_0.png)


The above is "sampled" in a sense, in that it is based on an array of length 100 with each element spaced by .01.

To base it on samples explicitly you can use one of two expressions:

\\(x = Acos(2{\pi}fnT + {\phi})\\), where n is the sample index and T is the sample period, or 

\\(x = Acos(2{\pi}fn/N + {\phi})\\), where n is the sample index and N is the number of samples.

\\(x = Acos(2{\pi}fnT + {\phi})\\) gives:

```python
A = .65
fs = 100
samples = 100
f = 5
phi = 0
n = np.arange(samples)
T = 1.0/fs # Remember to use 1.0 and not 1!
y = A*np.cos(2*np.pi*f*n*T + phi)
plt.plot(y)
plt.axis([0,100,-1,1])
plt.xlabel('sample index')
plt.ylabel('amplitude')
plt.show()
```


![png](/img/sinusoids/output_5_0.png)


\\(x = Acos(2{\pi}fn/N + {\phi})\\) is "independent" of time, in that frequency depends on the sample rate, or really on the time basis of the sample rate. So if your sample rate is 100 samples per day and f = 5, your frequency would 5 cycles per day. 


```python
A = .8
N = 100 # samples
f = 5
phi = 0
n = np.arange(N)
y = A*np.cos(2*np.pi*f*n/N + phi)
plt.plot(y)
plt.axis([0,100,-1,1])
plt.xlabel('sample index')
plt.ylabel('amplitude')
plt.show()
```


![png](/img/sinusoids/output_7_0.png)


Complex sinusoids have the form:

\\(e^{j(2{\pi}ft +{\phi})} = cos(2{\pi}ft) + jsin(2{\pi}ft)\\) for continuous time and \\(x = e^{j(2{\pi}fnT+{\phi})}\\) for discrete. Leaving out the amplitude term, here is the continuous version, with the "imaginary" component shown in green


```python
f = 3
t = np.arange(0,1,.01)
phi = 0
x = np.exp(1j*(2*np.pi*f*t + phi))
xim = np.imag(x)
plt.figure(1)
plt.plot(t,np.real(x))
plt.plot(t,xim)
plt.axis([0,1,-1.1,1.1])
plt.xlabel('time in seconds')
plt.ylabel('amplitude')
plt.show()
```


![png](/img/sinusoids/output_9_0.png)


The discrete version \\( = e^{j(2{\pi}fnT+{\phi})}\\)


```python
f = 3
N = 100
fs = 100
n = np.arange(N)
T = 1.0/fs
t = N*T
phi = 0
x = np.exp(1j*(2*np.pi*f*n*T + phi))
xim = np.imag(x)
plt.figure(1)
plt.plot(n*T,np.real(x))
plt.plot(n*T,xim)
plt.axis([0,t,-1.1,1.1])
plt.xlabel('t(seconds)')
plt.ylabel('amplitude')
plt.show()
```


![png](/img/sinusoids/output_11_0.png)


You can also do it based on \\( = e^{j(2{\pi}fn/N +{\phi})}\\).


```python
f = 3
N = 64 
n = np.arange(64)
phi = 0
x = np.exp(1j*(2*np.pi*f*n/N + phi))
xim = np.imag(x)
plt.figure(1)
plt.plot(n,np.real(x))
plt.plot(n,xim)
plt.axis([0,samples,-1.1,1.1])
plt.xlabel('sample index')
plt.ylabel('amplitude')
plt.show()
```


![png](/img/sinusoids/output_13_0.png)


Finally, you can use Scipy to write the data to a .wav file - here is 1 second at 440 Hz


```python
N = 44100 # samples
f = 440
fs = 44100
phi = 0
n = np.arange(N)
x = A*np.cos(2*np.pi*f*n/N + phi)
#scipy.io.wavfile.write(filename, rate, data)[source]
from scipy.io.wavfile import write
write('sine440_1sec.wav', 44100, x)
```
<audio controls><source src="/audio/sine1sec440.wav" type="audio/wav" preload="auto">
Your browser does not support the audio tag.
</audio><br/> 

