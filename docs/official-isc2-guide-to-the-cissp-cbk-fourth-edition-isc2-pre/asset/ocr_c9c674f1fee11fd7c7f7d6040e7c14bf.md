![](bbox=[0.01, 0.01, 0.99, 0.71])

Figure 3.32 - Meet-in-the-Middle attack on 2DES.

# Triple DES (3DES)

The defeat of double DES resulted in the adoption of triple DES as the next solution to overcome the weaknesses of single DES. Triple DES was designed to operate at a relative strength of 2^112 using two different keys to perform the encryption. This effectively rendered a key with a 168 bit strength. There are several different modes that Triple DES can be implemented through, but the four explained above are the most common and of the most concern to the security professional.

# Advanced Encryption Standard

In 1997, the National Institute of Standards and Technology (NIST) in the United States issued a call for a product to replace DES and 3DES. The requirements were that the new algorithm would be at least as strong as DES, have a larger block size (because a larger block size would be more efficient and more secure), and overcome the problems of performance with DES. DES was developed for hardware implementations and is too slow in software. 3DES is even slower, and thus it creates a serious latency in encryption as well as significant processing overhead.

After considerable research, the product chosen to be the new AES was the Rijndael