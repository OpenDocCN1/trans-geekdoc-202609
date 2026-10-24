where i(m,n) is the light illumination, and r(m₁,n₂) is the reflectance of the object to be imaged. Taking the natural logarithm of both sides leads to

ln[I(m,n)] = ln[i(m,n)] + ln[r(m,n)]  (4.2)

The illumination is approximately constant, while the reflectance is variable from object to object. Thus, the term ln[i(m,n)] is approximately constant. We can perform the encryption process on the ln[r(m,n)] term. To avoid the redundancy resulting from the existence of two components of the image in the homomorphic domain, we can embed the illumination component as an LSB watermark to the encrypted reflectance component. The homomorphic cryptosystem is illustrated in Figure 4.1. The 3 × 3 averaging filter shown in Figure 4.2 is used as the low-pass filter, and the reflectance component is obtained by subtracting the log illumination component from the log image intensity.

![](bbox=[0.1, 0.62, 0.9, 0.8])

Figure 4.1 Homomorphic image cryptosystem: (a) encryption subsystem and (b) decryption subsystem.

1/9 × [ 1 1 1 ; 1 1 1 ; 1 1 1 ]

Figure 4.2 The 3 × 3 averaging filter.