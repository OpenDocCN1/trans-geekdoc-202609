# CHAPTER 15 Combining Block Ciphers

![](bbox=[0.176, 0.115, 0.823, 0.442])

Figure 15.3 Doubling the block length.

$S$, and $T_i$ are internal variables, and $I_1$ and $I_2$ are counters. Two copies of the block algorithm run in a kind of hybrid OFB/counter mode, and the plaintext, $S_0$ and $T_i$ are XORed together. The two keys, $K_1$ and $K_2$, are independent. I know of no cryptanal-ysis of this variant.

# ECB + OFB

This method was designed for encrypting multiple messages of a fixed length, for example, disk blocks [186,188]. Use two keys: $K_1$ and $K_2$. First, use the algorithm and $K_1$ to generate a mask of the required block length. This mask will be repeated-ly to encrypt messages with the same keys. Then, XOR the plaintext message with the mask. Finally, encrypt the XORed plaintext with the algorithm and $K_3$ in ECB mode.

This has not been analyzed outside the paper in which it was proposed. Clearly it is at least as strong as a single ECB encryption and may be as strong as two passes with the algorithm. Possibly, a cryptanalyst could search for the two keys independently if several known plaintext files are encrypted with the same key.

To thwart analysis of identical blocks in the same positions of different messages, you can add an IV in any other mode, here the IV is XORed with every block of the message before ECB encryption.

Matt Blaze designed this mode for his UNIX Cryptographic File System (CFS). It is a nice mode because the latency is only one encryption in ECB mode; the mask can be generated once and stored. In CFS, DES is the block algorithm.