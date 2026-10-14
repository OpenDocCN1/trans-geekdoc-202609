# The Data Encryption Standard (DES)

In 1977, the U.S. National Bureau of Standards, which is now the National Institute of Standards and Technology (NIST), created the Data Encryption Standard (DES). DES quickly became the most widely used symmetric key encryption method.

DES is still widely used because it has survived everything except brute-force exhaustive search attacks, because it is widely available, and because it is supported by hardware accelerators.

# 56-BIT KEY SIZE

The DES key is 56 bits long. It comes in a block of 64 bits, of which 56 bits represent the key. The other 8 bits are redundant in the sense that you can compute them if you know the other 56 bits. This redundancy allows parties to detect incorrect keys.

Today, a 56-bit key size is too short for major business transactions and highly sensitive trade secrets.¹⁴ However, it is sufficient for most residential consumer applications, and as we will see next, cryptographers have extended DES to 3DES for industrial-strength security. Even 56-bit DES consumes a moderate amount of RAM and is only moderately fast.

# BLOCK ENCRYPTION

Figure 3-7 shows that DES is a block encryption standard. DES encrypts messages 64 bits at a time. The inputs for the encryption are the key and the 64-bit block of plaintext. The output is a 64-bit block of ciphertext.¹⁵

# Test Your Understanding

+   11. a. How long is a DES key?
+       b. Is this a strong length?
+       c. Describe block encryption with DES.

Figure 3-7 DES Block Encryption

![](bbox=[0.1, 0.63, 0.7, 0.84])

¹⁴ In fairness to NIST, DES was designed to be used only for about 10 years—until the mid-1980s. During that period, a 56-bit key was a fairly strong key.

¹⁵ In block encryption, the specific way that the encryption is done is called a mode. Figure 3-7 specifically shows electronic codebook mode, which is the simplest DES block encryption mode. More complex DES modes offer better protection.