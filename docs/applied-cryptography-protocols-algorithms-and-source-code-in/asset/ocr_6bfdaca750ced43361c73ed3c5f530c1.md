# CHAPTER 17

# # Other Stream Ciphers and Real Random-Sequence Generators

# ## 17.1 RC4

RC4 is a variable-key-size cipher developed in 1987 by Ron Rivest for RSA Data Security, Inc. For seven years it was proprietary, and details of the algorithm were only available after signing a nondisclosure agreement.

In September, 1994 someone posted source code to the CypherP mailing list—anonymously. It quickly spread to the Usenet newsgroup sci.crypt, and via the Internet to find sites around legal copies of RC4 confirmed compatibility. RSA Data Security, Inc. tried to put the genie back into the bottle, claiming that it was still a trade secret even though it was public, it was too late. It has since been discussed and dissected on Usenet, distributed at conferences, and taught in cryptography courses.

RC4 is simple to describe. The algorithm works in OFB: The keystream is independent of plaintext. It has a $8 \times 8$ box: $S_0, S_1, \dots, S_{255}$. The entries are a permutation of the numbers 0 through 255, and the permutation is a function of the variable-length key $K$. It has two counters, $i$ and $j$, initialized to zero. To generate a random byte, by do the:

```
$i = (i + 1) \bmod 256$
$j = (j + S_i) \bmod 256$
swap $S_i$ and $S_j$
t$t = (S_i + S_j) \bmod 256$
$K = S_t$
```

The byte $K$ is XORed with the plaintext to produce ciphertext or decrypted plaintext. Encryption is fast—about 10 times faster than DES. Initializing the S-box is easy. First it linearly: $S_0 = 0, S_1 = 1, \dots, S_{255} = 255$. Then fill another 256-byte array with the key, repeating the key as necessary to fill the entire array: $K_0, K_1, \dots, K_{255}$. Set the index $j$ to zero. Then: