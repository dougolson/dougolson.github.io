---
layout: post
title: Diving into the DFT
date: 2015-12-26 02:27 
description: Making sense of the Discrete Fourier Transform
thumbnail: /img/DFT/output_19_0.png
comments: True
---

<img class = "post-thumb" src="/img/DFT/output_19_0.png" height="120" width="120">Time to look at the Discrete Fourier Transform or DFT. It's a bit daunting to try and figure out what's going on in there - I found it confusing at first, and looked to various online resources for help. I found <a href="https://jackschaedler.github.io/circles-sines-signals/dft_walkthrough.html">Jack Schaedler's tutorial </a> to be very helpful for giving an intuitive picture of the DFT. <a href="https://www.youtube.com/watch?v=h6QJLx22zrE">David Dorran's YouTube tutorial</a> is also very good. <a href="https://ccrma.stanford.edu/~jos/mdft/mdft.html">Julius O. Smith's book </a> lays out the math in great detail, and the <a href ="https://www.coursera.org/course/audio">Coursera Course</a> he does with Xavier Serra covers both the theory and programming aspects of the DFT. So...

The equation for the DFT is:

\\[X[k] = {\sum_{n=0}^{N-1}}x[n]e^{-j2{\pi}kn/N} \quad k = 0, 1, 2, ..., N-1\\]

I translate this into English by saying "the kth bin of the DFT is the sum of the product of each signal sample x[n] and \\(e^{-j2{\pi}kn/N}\\) from n = 0 to n = N-1." I'm not sure how useful it is to read, but I find it useful to force myself to put equations like this into words.

Another way to think of it is that since \\[e^{-j\theta} =cos(\theta ) - jsin(\theta)\\] The DFT equation can be rewritten as \\[X[k] = {\sum_{n=0}^{N-1}}x[n]cos(\frac{2{\pi}kn}{N}) -  j{\sum_{n=0}^{N-1}}x[n]sin(\frac{2{\pi}kn}{N}) \quad k = 0, 1, 2, ..., N-1\\] 

Which basically says, among other tings, that the number of DFT frequency bins or "Basis Frequencies" is related to the number of samples in the signal as \\[\frac{n}{N} \quad or \quad \frac{0}{N}, \frac{1}{N}, \frac{2}{N},...,\frac{N-1}{N},\\] and that the kth bin, X[k], has both real and imaginary components.  

Looking at a few examples helps to show what's going on. Starting with k=0, the 0Hz component, we get a flat line - DC. 


{% highlight python %}
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
N = 32
n = np.arange(N)
k = 0 # the DC component
basisFreq = np.exp(-1j*2*np.pi*k*n/N)
print "for k=",k,", n=1 through n=6 are", basisFreq[:6]
plt.plot(n,np.real(basisFreq))
plt.plot(n,np.imag(basisFreq))
plt.title("k = 0")
plt.axis([0,N,-1,1])
plt.xlabel('sample index')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}

{% highlight python %}
for k= 0 , n=1 through n=6 are 
[ 1.+0.j  1.+0.j  1.+0.j  1.+0.j  1.+0.j  1.+0.j]
{% endhighlight %}

![png](/img/DFT/output_1_1.png)


For k=1, we get a low frequency component

{% highlight python %}
N = 32
n = np.arange(N)
k = 1
basisFreq = np.exp(-1j*2*np.pi*k*n/N)
print "for k=",k,", n=1 through n=6 are", basisFreq[:6]
plt.plot(n,np.real(basisFreq))
plt.plot(n,np.imag(basisFreq))
plt.title("k = 1")
plt.axis([0,N,-1,1])
plt.xlabel('sample index')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}

{% highlight python %}
for k =  1 , n=1 through n=6 = are 
[ 1.00000000+0.j  0.98078528-0.19509032j  0.92387953-0.38268343j
0.83146961-0.55557023j  0.70710678-0.70710678j  0.55557023-0.83146961j]
{% endhighlight %}


![png](/img/DFT/output_3_1.png)

For k=5, we get a higher frequency component

{% highlight python %}
N = 32
n = np.arange(N)
k = 5
basisFreq = np.exp(-1j*2*np.pi*k*n/N)
print "for k=",k,", n=1 through n=6 are", basisFreq[:6]
plt.plot(n,np.real(basisFreq))
plt.plot(n,np.imag(basisFreq))
plt.title("k = 5")
plt.axis([0,N,-1,1])
plt.xlabel('sample index')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}

{% highlight python %}
for k= 5 , n=1 through n=6 are 
[ 1.00000000+0.j  0.55557023-0.83146961j -0.38268343-0.92387953j
-0.98078528-0.19509032j -0.70710678+0.70710678j  0.19509032+0.98078528j]
{% endhighlight %}

![png](/img/DFT/kEquals5.png)

For k=15 the frequency component is higher still. The apparent modulation of the data is an artifact of plotting a small number of points.


{% highlight python %}
N = 32
n = np.arange(N)
k = 15
basisFreq = np.exp(-1j*2*np.pi*k*n/N)
print "for k=",k,", n=1 through n=6 are", basisFreq[:6]
plt.plot(n,np.real(basisFreq))
plt.plot(n,np.imag(basisFreq))
plt.title("k = 15")
plt.axis([0,N,-1,1])
plt.xlabel('sample index')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}

{% highlight python %}
for k =  15 , n=1 through n=6 are
[ 1.00000000+0.j  -0.98078528-0.19509032j  0.92387953+0.38268343j
-0.83146961-0.55557023j  0.70710678+0.70710678j -0.55557023-0.83146961j]
{% endhighlight %}


![png](/img/DFT/output_7_1.png)


k = 16, or N/2, corresponds to the highest frequency component. Note that the imaginary component here is 0j


{% highlight python %}
N = 32
n = np.arange(N)
k = 16
basisFreq = np.exp(-1j*2*np.pi*k*n/N)
print "for k=",k,", n=1 through n=6 are", basisFreq[:6]
plt.plot(n,np.real(basisFreq))
plt.plot(n,np.imag(basisFreq))
plt.title("k = 16, i.e. (N/2)")
plt.axis([0,N,-1,1])
plt.xlabel('sample index')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}

{% highlight python %}
for k =  16 , n=1 through n=6 are
[ 1. +0.00000000e+00j -1. -1.22464680e-16j  1. +2.44929360e-16j
-1. -3.67394040e-16j  1. +4.89858720e-16j -1. -6.12323400e-16j]
{% endhighlight %}


![png](/img/DFT/output_9_1.png)


At k=17, the plot looks the same as k=15


{% highlight python %}
N = 32
n = np.arange(N)
k = 17
basisFreq = np.exp(-1j*2*np.pi*k*n/N)
print "for k=",k,", n=1 through n=6 are", basisFreq[:6]
plt.plot(n,np.real(basisFreq))
plt.plot(n,np.imag(basisFreq))
plt.title("k = 17")
plt.axis([0,N,-1,1])
plt.xlabel('sample index')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}

{% highlight python %}
    for k =  17 , n=1 through n=6 are
    [ 1.00000000+0.j  -0.98078528+0.19509032j  0.92387953-0.38268343j
    -0.83146961+0.55557023j  0.70710678-0.70710678j -0.55557023+0.83146961j]
{% endhighlight %}


![png](/img/DFT/output_11_1.png)

k = N-1 looks very similar to k = 1, except that the phase of the sin component is inverted.


{% highlight python %}
N = 32
n = np.arange(N)
k = N-1
basisFreq = np.exp(-1j*2*np.pi*k*n/N)
print "for k=",k,", n=1 through n=6 are", basisFreq[:6]
plt.plot(n,np.real(basisFreq))
plt.plot(n,np.imag(basisFreq))
plt.title("k = N-1")
plt.axis([0,N,-1,1])
plt.xlabel('sample index')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}

{% highlight python %}
for k =  31 , n=1 through n=6 are 
[ 1.00000000+0.j  0.98078528+0.19509032j  0.92387953+0.38268343j
 0.83146961+0.55557023j  0.70710678+0.70710678j  0.55557023+0.83146961j]
{% endhighlight %}


![png](/img/DFT/output_5_1.png)




Back to the DFT... I'm going to use a signal with frequency 5 cycles per time unit and sample rate 32 samples per time unit for x[n]. I say "per time unit" because although 1 second is what you see most often, any unit of time could be chosen. It looks a bit ragged, but that's just because of the low number of samples per cycle:


{% highlight python %}
A = 1
f = 5
N = 32
n = np.arange(N)
x = A*np.exp(1j*2*np.pi*f*n/N)
plt.plot(n,np.real(x))
plt.plot(n,np.imag(x))
plt.title("x[n], f = 5")
plt.axis([0,N,-1,1])
plt.xlabel('sample index')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}


![png](/img/DFT/output_13_0.png)


The DFT Calculation looks like this:


{% highlight python %}
X = np.array([]) # create an empty array
for k in n: # loop over k from 0 to N-1 (here n is a numpy array from 0 - 31)
    Xk = (np.exp(-1j*2*np.pi*k*n/N)) # the trasonformation kernel is calculated for each basis frequency k
    X = np.append(X,sum(x*Xk)) # for each k, the dot product is calculated, summed, and appended to array X

plt.plot(X)
plt.title("DFT")
plt.axis([0,N,-1,N])
plt.xlabel('frequency')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}


![png](/img/DFT/output_15_0.png)


Here's another way of looking at it, showing the dot product of the signal x[n] with each basis frequency. As in the plot, the only basis frequency that is correlated with the signal is at k = 5.


{% highlight python %}
A = 1
f = 5
N = 32
n = np.arange(N)
x = A*np.exp(1j*2*np.pi*f*n/N)
k=0
for k in n:
    Xk = sum(x*np.exp(-1j*2*np.pi*k*n/N))
    print "for k=",k," Xk =", np.around([Xk]) 
{% endhighlight %}

{% highlight python %}
for k= 0  Xk = [-0.-0.j]
for k= 1  Xk = [ 0.-0.j]
for k= 2  Xk = [ 0.+0.j]
for k= 3  Xk = [-0.+0.j]
for k= 4  Xk = [-0.-0.j]
for k= 5  Xk = [ 32.+0.j]
for k= 6  Xk = [-0.-0.j]
for k= 7  Xk = [ 0.+0.j]
for k= 8  Xk = [-0.+0.j]
for k= 9  Xk = [-0.+0.j]
for k= 10  Xk = [-0.+0.j]
for k= 11  Xk = [-0.-0.j]
for k= 12  Xk = [-0.+0.j]
for k= 13  Xk = [ 0.-0.j]
for k= 14  Xk = [-0.+0.j]
for k= 15  Xk = [ 0.-0.j]
for k= 16  Xk = [ 0.-0.j]
for k= 17  Xk = [-0.+0.j]
for k= 18  Xk = [ 0.-0.j]
for k= 19  Xk = [ 0.+0.j]
for k= 20  Xk = [ 0.-0.j]
for k= 21  Xk = [ 0.-0.j]
for k= 22  Xk = [ 0.-0.j]
for k= 23  Xk = [ 0.+0.j]
for k= 24  Xk = [ 0.+0.j]
for k= 25  Xk = [ 0.+0.j]
for k= 26  Xk = [-0.+0.j]
for k= 27  Xk = [ 0.-0.j]
for k= 28  Xk = [ 0.+0.j]
for k= 29  Xk = [-0.+0.j]
for k= 30  Xk = [-0.+0.j]
for k= 31  Xk = [-0.-0.j]
{% endhighlight %}


That worked nicely for an integer signal frequency. If you use a float, like f = 5.4, the DFT spreads out and doesn't give such a precise result (the blue trace in the plot). It also doesn't make much sense that frequencies on either side of 5 would be correlated and then anticorellated with the basis sinusoid at 5. Things make a lot more sense if you look at the magnitude by taking the absolute value of each X[k]  (green trace).


{% highlight python %}
A = 1
f = 5.4
N = 32
n = np.arange(N)
x = A*np.exp(1j*2*np.pi*f*n/N)

X = np.array([]) 
for k in n: 
    Xk = (np.exp(-1j*2*np.pi*k*n/N))
    X = np.append(X,sum(x*Xk))
Xabs = abs(X)
plt.plot(X)
plt.plot(Xabs)
plt.title("DFT")
plt.xlabel('frequency')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}


![png](/img/DFT/output_19_0.png)


Using a real input signal generates two peaks, each only half as high


{% highlight python %}
A = 1
f = 5
N = 32
n = np.arange(N)
x = A*np.cos(2*np.pi*f*n/N)
X = np.array([]) 
for k in n:
    Xk = np.exp(-1j*2*np.pi*k*n/N)
    X = np.append(X,abs(sum(x*Xk)))

plt.plot(X)
plt.title("DFT")
plt.axis([0,N,0,N])
plt.xlabel('frequency')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}


![png](/img/DFT/output_21_0.png)


Recall that the transformation kernel generates frequencies in the pattern low - high - low, with the high being at k = N/2 or 16 in this case. The peak at 27 can be thought of as having a frequency of -5 relative to k=N-1   Shifting the indices around centers the plot around 0 and shows the peaks as frequency components at +/- 5. The idea of negative frequency is pretty weird. About the best explanation I have found is that it is like a spinning wheel in that you can think of it spinning clockwise at x rpm or counterclockwise at -x rpm, which is . There is also the explanation that \\(e^{-j{\omega}} = cos({\omega}) - jsin({\omega})\\), and that the imaginary component is orthogonal to the real component and cancels out in the dot product when the signal is complex, but not when it is real.


{% highlight python %}
A = 1
f = 5
N = 32
n = np.arange(N)
n2 = np.arange(-N/2,N/2)
x = A*np.cos(2*np.pi*f*n2/N)
X = np.array([])
for k in n2:
    Xk = np.exp(-1j*2*np.pi*k*n2/N)
    X = np.append(X,abs(sum(x*Xk)))
    
plt.plot(n2,X)
plt.title("DFT")
plt.axis([-N/2,N/2,-1,N/2])
plt.xlabel('frequency')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}


![png](/img/DFT/output_23_0.png)


The same plot as above, with a non-integer frequency of 5.5


{% highlight python %}
A = 1
f = 5.5
N = 32
n = np.arange(N)
n2 = np.arange(-N/2,N/2)
x = A*np.cos(2*np.pi*f*n2/N)
X = np.array([])
for k in n2:
    Xk = np.exp(-1j*2*np.pi*k*n2/N)
    X = np.append(X,abs(sum(x*Xk)))
    
plt.plot(n2,X)
plt.title("DFT")
plt.axis([-N/2,N/2,0,N/2])
plt.xlabel('frequency')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}


![png](/img/DFT/output_25_0.png)

Being an infinite series of odd harmonics in decreasing proportion (1, 1/3, 1/5, 1/7 etc.), a square wave is a little more interesting than a sine, as the DFT shows. The function below generates one for a given frequency and number of harmonics. 


{% highlight python %}
# Generate a square wave additively
def squareGen(fo = 5,length = 1000):
    fmax = length/2
    nmax = np.floor((fmax - 1)/(2.0*fo))
    fIndex = np.arange(nmax)
    n = np.arange(length)
    freqs = fo*(2*fIndex + 1) 
    sq = np.zeros(length)
    for f in freqs:
        harm = (fo/f)*(4/np.pi)*np.sin(2*np.pi*f*n/length)
        sq = sq + harm
    return sq  

sq1 = squareGen()
plt.plot(sq1)
plt.axis([0,len(sq1),-1.1,1.1])
plt.xlabel('sample index')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}



![png](/img/DFT/output_30_1.png)



{% highlight python %}
N = len(sq1)
X = np.array([])
n2 = np.arange(-N/2,N/2)
for k in n2:
    Xk = np.exp(-1j*2*np.pi*k*n2/N)
    X = np.append(X,abs(sum(sq1*Xk)))

plt.plot(n2,X)
plt.axis([0,100,-10,N])
plt.xticks(np.arange(0,100,5))
plt.title("5 Hz Square Wave v1 DFT")
plt.grid(True)
plt.xlabel('frequency')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}


![png](/img/DFT/output_31_0.png)


A cleaner square wave can be generated with a number sequence [1,1,1,...-1,-1,-1]. The DFT for the first ten harmonics is identical. 


{% highlight python %}
sq2 = np.repeat(1.0,100)
sq2 = np.append(sq2,np.repeat(-1.0,100))
sq2 = np.tile(sq2,5)
plt.plot(sq2)
plt.axis([0,1000,-1.1,1.1])
plt.xlabel('sample index')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}


![png](/img/DFT/output_33_0.png)



{% highlight python %}
N = len(sq2)
n2 = np.arange(-N/2,N/2)
X = np.array([])
for k in n2:
    Xk = np.exp(-1j*2*np.pi*k*n2/N)
    X = np.append(X,abs(sum(sq2*Xk)))


plt.plot(n2,X)
plt.axis([0,100,-10,N])
plt.xticks(np.arange(0,100,5))
plt.title("5 Hz Square Wave v2 DFT")
plt.grid(True)
plt.xlabel('frequency')
plt.ylabel('amplitude')
plt.show()

{% endhighlight %}




![png](/img/DFT/output_34_1.png)


A sawtooth wave has both even and odd harmonics in descending proportion of (1, 1/2, 1/3, 1/4, etc.)


{% highlight python %}
def sawGen(f=5,A=1,Sr=1000,length=1):
    T = 1.0/f
    A = float(A)
    N = float(Sr*T)
    n = np.arange(N)
    x = A*n/N - A/2
    x = 2*np.tile(x,f*length)
    return x

saw = sawGen()
plt.plot(saw)
plt.grid(True)
plt.show()

{% endhighlight %}


![png](/img/DFT/output_36_0.png)



{% highlight python %}
N = len(saw)
X = np.array([])
n2 = np.arange(-N/2,N/2)
X = np.array([])
for k in n2:
    Xk = np.exp(-1j*2*np.pi*k*n2/N)
    X = np.append(X,abs(sum(saw*Xk)))


plt.plot(n2,X)
plt.axis([0,100,-10,N])
plt.xticks(np.arange(0,100,5))
plt.title("5 Hz Sawtooth Wave DFT")
plt.grid(True)
plt.xlabel('frequency')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}


![png](/img/DFT/output_37_0.png)


A triangle wave:


{% highlight python %}
def triGen(f=5,A=1,Sr=1000,length=1):
    T = 1.0/f
    #    A = f(A)
    N = (Sr*T)
    n = np.arange(int(N/2))
    x = 2*A*n/N 
    x = np.append(x,[x[-i-1] for i in range(len(x))]) - float(A)/2
    x = 2*np.tile(x,f*length)
    return x

tri = triGen()
plt.plot(tri)
plt.show()
{% endhighlight %}


![png](/img/DFT/output_39_0.png)



{% highlight python %}
N = len(tri)
X = np.array([])
n2 = np.arange(-N/2,N/2)
X = np.array([])
for k in n2:
    Xk = np.exp(-1j*2*np.pi*k*n2/N)
    X = np.append(X,abs(sum(tri*Xk)))


plt.plot(n2,X)
plt.axis([0,100,-10,N])
plt.xticks(np.arange(0,100,5))
plt.title("5 Hz Triangle Wave DFT")
plt.grid(True)
plt.xlabel('frequency')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}


![png](/img/DFT/output_40_0.png)


Finally, an actual audio file. I used a 1 second snippet taken from freesound.org, and the DFT took over five minutes to calculate, which is no doubt why the FFT is used. I used a 5000 sample slice to speed things up.


{% highlight python %}
from scipy.io.wavfile import read
audio = read("waterGlass.wav")
data = audio[1]
data = data[20000:25000]
{% endhighlight %}


{% highlight python %}
N = len(data)
X = np.array([])
n2 = np.arange(-N/2,N/2)
X = np.array([])
for k in n2:
    Xk = np.exp(-1j*2*np.pi*k*n2/N)
    X = np.append(X,abs(sum(data*Xk)))

plt.plot(n2,np.log10(X))
plt.axis([0,N/2,0,8])
#plt.xticks(np.arange(400,500,20))
plt.title("waterGlass.wav DFT")
plt.grid(True)
plt.xlabel('frequency')
plt.ylabel('amplitude')
plt.show()
{% endhighlight %}


![png](/img/DFT/output_44_0.png)


There is plenty more to look at here - more in a subsequent post.
