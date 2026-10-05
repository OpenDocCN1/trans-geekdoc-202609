# 18.11 Symmetric Block Algorithms

The most obvious method is to encrypt the message with the algorithm in CBC or CFB mode, a fixed key, and IV; the last ciphertext block is the hash value. These methods are described in various standards using DES; both modes in [1143]. CFB in [1145]. CBC in [55,66,54]. This is not enough for one-way hash functions, although it will work for a MAC [see Section 18.14] [29].

A clever approach is to use the block as the key, and the current hash value as the output.

The actual hash functions are even more complex. The block size is usually the key length, and the size of the hash value is the block size. Since most algorithms are 64 bits, several schemes are designed around a hash that is twice the block size.

Assuming the hash function is correct, the security of the scheme is based on the security of the underlying block function. There are exceptions, though. Differential cryptanalysis is easier against block functions in hash functions than against block functions used for encryption: The key is known, so only one pair is needed for security and you can generate as much plaintext as you want. Some work on these lines in [126,858,1313].

What follows is a summary of the various hash functions that have appeared in the literature [92,1465,1262]. Statements about attacks against these schemes that assume the underlying block cipher is secure; are, the best attack against them is brute force.

One measure for hash functions based on block functions is the hash rate, or the number of n-bit message blocks, where n is the block size of the algorithm, processed per encryption. The higher the rate, the faster the algorithm. [This measure was given the opposite definition in [1262], but the definition given here is more intuitive and is widely used.]

# Schemes Where the Hash Length Equals the Block Size

The general scheme is as follows (see Figure 18.8):

```
$H_0 = I_H$, where $I_H$ is a random initial value
nH_i = E_A(H_{i-1}) \oplus C$
```

where $A, B$, and $C$ can be either $M_i, H_{i-1}, (M_i \oplus H_{i-1})$, or a constant (assumed to be 0). $H_0$ is some random initial value: $I_H$. The message is divided up into block-size chunks, $M_i$ and processed individually. And there is some kind of MD-strengthening, perhaps the same padding procedure used in MD5 and SHA.

![](bbox=[0.14, 0.805, 0.415, 0.91])

Figure 18.8 General hash function where the hash length equals the block size.