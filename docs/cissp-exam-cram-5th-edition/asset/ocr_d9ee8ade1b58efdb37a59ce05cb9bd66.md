Although ECB produces the highest throughput, it is also the easiest form of DES encryption to break. If used with large amounts of data, it can be easily attacked because identical plaintext, when encrypted with the same key, will always produce the same ciphertext. ECB mode is appropriate only when used on small amounts of data. Figure 4.15 illustrates ECB.

![](bbox=[0.116, 0.21, 0.843, 0.415])

FIGURE 4.15 DES ECB Encryption

> **Tip**
> 
> When using ECB, a given block of plaintext encrypted with a given key will always give the same ciphertext. ECB is the weakest form of DES.

# Cipher Block Chaining (CBC) Mode

The CBC mode of DES, which is widely used, is similar to ECB. CBC processes 64-bit blocks of data but inserts some of the ciphertext created from each block into the next block. In this process, called _chaining_, each block is dependent on the previous block, creating a chain; chaining is accomplished by using the XOR operation.

The CBC mode of DES makes the ciphertext more secure and less susceptible to cracking. CBC mode is subject to a slight risk of propagating transmission errors upon reception. Any error experienced will be propagated