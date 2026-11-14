# ## 2.3.1 Method 1

Precisely, this FBP algorithm can be implemented according to the steps shown in Figure 2.6, in which the ramp filtering is implemented as follows:

+   (i) Find the 1D Fourier transform of \(p(s, \theta)\) with respect to the first variable \(s\), obtaining \(P(\omega, \theta)\).
+   (ii) Multiply \(P(\omega, \theta)\) with a ramp filter \(|\omega|\), obtaining \(Q(\omega, \theta)\).
+   (iii) Find the 1D inverse Fourier transform of \(Q(\omega, \theta)\) with respect to the first variable \(\omega\), obtaining \(q(s, \theta)\).

![](bbox=[0.176, 0.288, 0.605, 0.35])

**Fig. 2.6:** The procedure of the filtered backprojection (FBP) algorithm.

# ## 2.3.2 Method 2

There are more ways than one to do ramp filtering. In fact, we can perform ramp filtering without using the Fourier transform at all. According to the Fourier transform theory, multiplication in one domain (say, the \(\omega\) domain) corresponds to convolution in the other domain (say, the \(s\) domain) (see Figure 2.7).

Thus steps (i), (ii), and (iii) in Method 1 are equivalent to a mathematical procedure called _convolution_. The ramp-filtered data \(q(s, \theta)\) can be obtained by convolution as follows:

```
\(q(s, \theta) = p(s, \theta) * h(s),\) (2.1)
```

where “*” denotes the convolution operation, which is an integral with respect to the variable \(s\). Here \(h(s)\) is the convolution kernel and is the 1D inverse Fourier transform of \(H(\omega) = |\omega|\).

Here we give an example of convolution so that you can understand what convolution can do for you. If the convolution kernel \(h(s)\) is not symmetric, you first flip it left–right, making it \(h(-s)\). Second, you imagine that your function \(p(s)\) can be decomposed into vertical spikes (or Dirac’s delta functions). Third, replace each spike by \(h(-s)\), that is, the \(s = 0\) position of \(h(-s)\) is at the spike’s position, and scale \(h(-s)\) by the amplitude (which can be negative) of the spike. Finally, sum up all the shifted and scaled versions of \(h(-s)\), obtaining \(q(s)\) (see Figure 2.8).