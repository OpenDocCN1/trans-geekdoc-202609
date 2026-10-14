# Table 6.3 Comparative Study of Permutation Based Encryption Techniques

| Algorithm Name | Pure Permutation | Zig-Zag Permutation | Huffman Codeword | Compression Logic Based Random Permutation |
|---|---|---|---|---|
| Visual Degradation | High | Unknown | Unknown | Variable |
| Algorithm Name | Pure permutation | Zig-Zag permutation | Huffman codeword | Compression logic based random permutation |
| Encryption ratio | 100% | 100% | Unknown | Variable |
| Speed | Fast | Fast | Fast | Fast |
| Compression friendliness | Satisfied | Satisfied | Not satisfied | Satisfied |
| Format compliance | Unknown | Unknown | Unknown | Satisfied |
| Cryptographic security | Not satisfied | Not satisfied | Not satisfied | Unknown |

of frequency). It is an example of a selective encryption as a small number of blocks are encrypted using the selected permutation group. This method is reliable against brute force attack because of a large keyspace (Table 6.3).

# 6.2.6.3 Selective Encryption

This class of algorithm selectively encrypts the bytes within a frame. Since it is a class of partial encryption technique, it is fast and computationally not costly. A few techniques in this class are discussed below:

Meyer and Gadegast [33]: This method is used for MPEG stream encryption. Encryption is done using standard RSA or DES algorithm in CBC mode. It deals with four levels of security as follows:

+   1. Encrypting the header
+   2. Encrypting all DC and AC lower coefficients
+   3. Encrypting all I frames, I block in P and B blocks
+   4. Encrypting the bit stream

If we encrypt the header, then the encryption ratio is very low as compared to encrypting the entire bitstream. The security and computational complexity increase as we move from point “a” to point “d.”