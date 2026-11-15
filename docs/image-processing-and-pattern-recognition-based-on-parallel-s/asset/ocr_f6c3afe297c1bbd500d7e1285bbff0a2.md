of the process according to the existing per cent of noise elements in the input image (pN). The following parameters were used to determine the coefficient of efficiency:

+   - kC – number of circle images provided for recognition.
+   - kCn – number of circle images that are not recognised by the system.
+   - eC – efficiency coefficient of circle recognition.

The efficiency coefficient value of circle recognition is determined by the following formula:

```
\( eC = \frac{kC - kCn}{kC} \). (6.16)
```

We denote the analogous parameters for the square (kS, kSn, eS), for the rectangle (kR, kRn, eR), for the triangle (kT, kTn, eT).

In the process of figure recognition, the following errors are used dk = 0.04, dS = 0.1, dN = 0.01. These values correspond to the analytically calculated range.

The process of identification of the figures was carried out to find the noise inclusion per cent from 0 to 20 corresponding to a range of effective noise removal by the chosen method. A total of 500 test images was submitted for each class of simple figures for each pN (kC = kS = kR = kT = 500). Using the obtained coefficients values, the average value of the coefficient of efficiency of recognition of simple shapes (eAs) was calculated for the pN parameter equaling 0 per cent, 5 per cent, 10 per cent, 15 per cent and 20 per cent. Efficiency coefficients are calculated by the following formula:

```
\( eAs = \frac{eC + eS + eR + eT}{4} \). (6.17)
```

Graphically, the average value of the efficiency coefficient of simple shapes recognition depend on the percentage of the noise is shown in Fig. 6.4.

![](bbox=[0.22, 0.615, 0.78, 0.85])

Fig. 6.4: Average values of efficiency coefficients of simple shapes recognition depending graphically on the noise percentage