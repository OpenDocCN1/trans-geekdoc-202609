# Homomorphic Image Encryption

# 4.1 Overview

This chapter presents a new image cryptosystem. This system is based on homomorphic image processing, which has evolved primarily as a tool of image enhancement for images captured in bad lighting conditions. The main idea of homomorphic image processing is based on modeling the image as a product of constant illumination and varying reflectance. The product is dealt with as a summation using the logarithmic operation. The reflectance component can be separated using a high-pass filter, while the illumination component is separated using a low-pass filter. Most of the image details lie in the reflectance component, while the illumination component is approximately constant [76,77].

We can carry out the encryption process in the homomorphic domain on the reflectance component, which is the most significant component of the image. Rather than encrypting the illumination component, which causes redundancy in image information, it is appended as a least-significant bit (LSB) watermark in the encrypted reflectance component. Two algorithms are used for the encryption of the reflectance component: the RC6 block cipher algorithm and the chaotic Baker map scrambling algorithm. A comparison is made between them.

# 4.2 Homomorphic Cryptosystem

The idea of the homomorphic cryptosystem is based on homomorphic image processing. It is known that the image intensity can be represented as follows [78–80]:

I(m,n) = i(m,n)r(m,n)    (4.1)