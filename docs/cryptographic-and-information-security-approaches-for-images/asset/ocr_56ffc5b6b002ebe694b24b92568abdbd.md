```
StdQuanTable = $\begin{pmatrix} 16 & 11 & 10 & 16 & 24 & 40 & 51 & 61 \\ 12 & 12 & 14 & 19 & 26 & 58 & 60 & 55 \\ 14 & 13 & 16 & 24 & 40 & 57 & 69 & 56 \\ 14 & 17 & 22 & 29 & 51 & 87 & 80 & 62 \\ 18 & 22 & 37 & 56 & 68 & 109 & 103 & 77 \\ 24 & 35 & 55 & 64 & 81 & 104 & 113 & 92 \\ 49 & 64 & 78 & 87 & 103 & 121 & 120 & 101 \\ 72 & 92 & 95 & 98 & 112 & 100 & 103 & 99 \end{pmatrix}$
```

Figure 14.6 The standard illumination quantization table, corresponding to the quality factor 50.

```
StdQuanTable = $\begin{pmatrix} 17 & 18 & 24 & 47 & 99 & 99 & 99 & 99 \\ 18 & 21 & 26 & 66 & 99 & 99 & 99 & 99 \\ 24 & 26 & 56 & 99 & 99 & 99 & 99 & 99 \\ 47 & 66 & 99 & 99 & 99 & 99 & 99 & 99 \\ 99 & 99 & 99 & 99 & 99 & 99 & 99 & 99 \\ 99 & 99 & 99 & 99 & 99 & 99 & 99 & 99 \\ 99 & 99 & 99 & 99 & 99 & 99 & 99 & 99 \\ 99 & 99 & 99 & 99 & 99 & 99 & 99 & 99 \end{pmatrix}$
```

Figure 14.7 The standard chrominance quantization table, corresponding to the quality factor 50.

At the same quality factor, elements in chrominance quantization matrix are larger than those in luminance quantization matrix. The principle of designing these two quantization matrix is based on the fact that HVS (human visual system) is more sensitive to luminance than chrominance.

After the forward DCT, each of the 64 DCT coefficients is quantized by the quantization matrix Q (it can be represented as Q(u,v), 0 ≤ u,v ≤7):

$QD(u,v) = round\left(\frac{D(u,v)}{Q(u,v)}\right)$ (14.4)

where QD(u,v) is quantized index of the DCT coefficient D(u,v), and the Q(u,v) is the quantization step obtained from the quantization table Q. This quantization will lead to many zeros. Hence, a small amount of 64 DCT coefficients are non-zero coefficients after quantization. It is the idea of compression. There existing systems hide bits with JPEG-compressed images. In general, they operate by modifying some subset of the quantized coefficients by ±1 to hide bits. ±1 hiding is also equivalent to equivalent partition mentioned above.