---
layout: post
title: Diving into the DFT
date: 2015-12-26 02:27 
description: Making sense of the Discrete Fourier Transform 
comments: True
---

<img align="left" src="/img/DFT/output_19_0.png" height="100" width="100">Time to look at the Discrete Fourier Transform or DFT. It's a bit daunting to try and figure out what's going on in there - I found it confusing at first, and looked to various online resources for help. I found <a href="https://jackschaedler.github.io/circles-sines-signals/dft_walkthrough.html">Jack Schaedler's tutorial </a> to be very helpful for giving an intuitive picture of the DFT. <a href="https://www.youtube.com/watch?v=h6QJLx22zrE">David Dorran's YouTube tutorial</a> is also very good. <a href="https://ccrma.stanford.edu/~jos/mdft/mdft.html">Julius O. Smith's book </a> lays out the math in great detail, and the <a href ="https://www.coursera.org/course/audio">Coursera Course</a> he does with Xavier Serra covers both the theory and programming aspects of the DFT. So...

The equation for the DFT is:

\\[X[k] = {\sum_{n=0}^{N-1}}x[n]e^{-j2{\pi}kn/N}     k = 0, 1, 2, ..., N-1\\]

I translate this into English by saying "the kth bin of the DFT is the sum of the product of each signal sample x[n] and \\(e^{-j2{\pi}kn/N}\\) from n = 0 to n = N-1."

It is also the dot product of two vectors, which can be thought of as the projection of one vector onto another, or a measure of how much of one vector is in another. More in that in a bit.

The number of DFT frequency bins is related to the number of samples in the signal: 0/N, 2/N,...,N-1/N. 

0/N is the DC component.

\\(e^{-j2{\pi}kn/N}\\), the *transformation kernel*, generates a set of complex frequencies. Just looking at a few examples, starting with k=0, the DC or 0Hz component, gives a sense of what's going on. Note how the frequency goes up as k approaches N/2, and then goes back down as it nears N-1:


```python
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
```

    for k= 0 , n=1 through n=6 are [ 1.+0.j  1.+0.j  1.+0.j  1.+0.j  1.+0.j  1.+0.j]



![png](/img/DFT/output_1_1.png)


Note that the basis frequencies are lowest at k = 1 and k = N-1. They are highest on either side of k = (N-1)/2


```python
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
```

    for k =  1 , n=1 : n=6 =  [ 1.00000000+0.j          0.98078528-0.19509032j  0.92387953-0.38268343j
      0.83146961-0.55557023j  0.70710678-0.70710678j  0.55557023-0.83146961j]



![png](/img/DFT/output_3_1.png)


For k = N-1


```python
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
```

    for k =  31 , n=1 : n=6 =  [ 1.00000000+0.j          0.98078528+0.19509032j  0.92387953+0.38268343j
      0.83146961+0.55557023j  0.70710678+0.70710678j  0.55557023+0.83146961j]



![png](/img/DFT/output_5_1.png)


For k=15


```python
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
```

    for k =  15 , n=1 : n=6 =  [ 1.00000000+0.j         -0.98078528-0.19509032j  0.92387953+0.38268343j
     -0.83146961-0.55557023j  0.70710678+0.70710678j -0.55557023-0.83146961j]



![png](/img/DFT/output_7_1.png)


For k = 16, note that the imaginary component is 0j


```python
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
```

    for k =  16 , n=1 : n=6 =  [ 1. +0.00000000e+00j -1. -1.22464680e-16j  1. +2.44929360e-16j
     -1. -3.67394040e-16j  1. +4.89858720e-16j -1. -6.12323400e-16j]



![png](/img/DFT/output_9_1.png)


At k=17, the plot looks the same as k=15


```python
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
```

    for k =  17 , n=1 : n=6 =  [ 1.00000000+0.j         -0.98078528+0.19509032j  0.92387953-0.38268343j
     -0.83146961+0.55557023j  0.70710678-0.70710678j -0.55557023+0.83146961j]



![png](/img/DFT/output_11_1.png)


Back to the DFT... I'm going to use a signal with frequency 5 cycles per time unit and sample rate 32 samples per time unit for x[n]. I say "per time unit" because although 1 second is what you see most often, any unit of time could be chosen. It looks a bit ragged, but that's just because of the low number of samples per cycle:


```python
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
```


![png](/img/DFT/output_13_0.png)


The DFT Calculation looks like this:


```python
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
```


![png](/img/DFT/output_15_0.png)


Here's another way of looking at it, showing the dot product of the signal x[n] with each basis frequency. As in the plot, the only basis frequency that is correlated with the signal is at k = 5.


```python
A = 1
f = 5
N = 32
n = np.arange(N)
x = A*np.exp(1j*2*np.pi*f*n/N)
k=0
for k in n:
    Xk = sum(x*np.exp(-1j*2*np.pi*k*n/N))
    print "for k=",k," Xk =", np.around([Xk]) 

```

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


That worked nicely for an integer signal frequency. If you use a float, like f = 5.4, the DFT spreads out and doesn't give such a precise result (the blue trace in the plot). It also doesn't make much sense that frquencies on either side of 5 would be correlated and then anticorellated with the basis sinusoid at 5. Things make a lot more sense if you look at the magnitude by taking the absolute value of each X[k] (green trace).


```python
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
```


![png](/img/DFT/output_19_0.png)


Using a real input signal generates two peaks, each only half as high


```python
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
```


![png](/img/DFT/output_21_0.png)


Recall that the transformation kernel generates frequencies in the pattern low - high - low, with the high being at k = N/2 or 16 in this case. The peak at 27 can be thought of as having a frequency of -5 relative to k=N-1   Shifting the indeces around centers the plot around 0 and shows the peaks as frequency components at +/- 5.


```python
A = 1
f = 5
N = 32
n = np.arange(N)
n2 = np.arange(-N/2,N/2)
x = A*np.cos(2*np.pi*f*nv/N)
X = np.array([])
for k in nv:
    Xk = np.exp(-1j*2*np.pi*k*n2/N)
    X = np.append(X,abs(sum(x*Xk)))
    
plt.plot(n2,X)
plt.title("DFT")
plt.axis([-N/2,N/2,-1,N/2])
plt.xlabel('frequency')
plt.ylabel('amplitude')
plt.show()
```


![png](/img/DFT/output_23_0.png)


The same plot as above, with a non-integer frequency of 5.5


```python
A = 1
f = 5.5
N = 32
n = np.arange(N)
n2 = np.arange(-N/2,N/2)
x = A*np.cos(2*np.pi*f*nv/N)
X = np.array([])
for k in nv:
    Xk = np.exp(-1j*2*np.pi*k*n2/N)
    X = np.append(X,abs(sum(x*Xk)))
    
plt.plot(n2,X)
plt.title("DFT")
plt.axis([-N/2,N/2,0,N/2])
plt.xlabel('frequency')
plt.ylabel('amplitude')
plt.show()
```


![png](/img/DFT/output_25_0.png)


There is plenty more to look at here - more in a subsequent post.
