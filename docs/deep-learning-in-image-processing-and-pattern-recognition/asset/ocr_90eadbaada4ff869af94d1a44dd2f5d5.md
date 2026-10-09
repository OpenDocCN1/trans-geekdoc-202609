By subtracting the light intensity of the speckle pattern before and after the deformation of the measured object, as follows:

```
$$\Delta I = I_1 - I_2 = 4\sqrt{I_0 I_r}\sin\frac{2\vartheta + \varphi}{2}\sin\frac{\varphi}{2} \tag{4}$$
```

With the change in the value of $\varphi$, the light intensity difference $\Delta I$ also changes, which allows us to observe fringe information that is not visible in a certain light field intensity, resulting in alternating bright and dark fringe images.

The measurement results of ESPI are usually the ESPI fringe pattern derived from the formula and the ESPI-wrapped phase map obtained by installing a phase shifter on the reference optical path and using a stepwise phase shift. As displayed in Figure 2, both contain considerable noise, and the ESPI fringe pattern presents a black and white, alternating light and dark fringe structure, with the density and direction of the fringes reflecting the phase difference changes on the object surface. The ESPI-wrapped phase map limits the phase information to the range $[-\pi, \pi]$ and displays it in grayscale or pseudo-color. The physical quantity to be measured is directly related to the phase distribution information of both. Therefore, studying advanced electronic speckle interferometry phase extraction methods is critical for quickly and accurately analyzing the measured physical quantity from the ESPI fringe pattern or wrapped phase map and has become a critical topic of research in current ESPI.

![](bbox=[0.17, 0.44, 0.45, 0.63])

![](bbox=[0.55, 0.44, 0.83, 0.63])

(a)

(b)

Figure 2. Two measurement results of ESPI technology ((a) ESPI fringe pattern and (b) ESPI-wrapped phase map).

# ### 3. Application of Deep Learning in the Phase Extraction of ESPI Fringe Patterns

The fringe centerline method is a classic phase extraction method for ESPI fringe patterns. Compared with other phase extraction methods, such as Fourier transform and wavelet transform, the fringe centerline method is the most direct phase extraction method based on a single fringe pattern. In this method, first, the fringe pattern is filtered for noise removal, the skeleton line of the ESPI fringe pattern is extracted, the series of skeleton lines is identified, and the phase values at the location of the skeleton lines are obtained. Finally, a specific algorithm is used to interpolate the identified skeleton lines to obtain full-field phase information. Figure 3 displays the steps of the method. The following sections explain the application of deep learning in this method.