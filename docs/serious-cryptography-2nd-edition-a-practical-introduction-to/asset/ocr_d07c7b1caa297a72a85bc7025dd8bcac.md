plaintext block. Then CMAC sets K1 to (L << 1) if L’s most significant bit (MSB) is 0 and to (L << 1) ⊕ 87 if L’s MSB is 1. (The hexadecimal number 87, or 135 in decimal, is chosen for its mathematical properties when data blocks are 128 bits; a different value is needed when blocks aren’t 128 bits.) The key K2 is set to (K1 << 1) if K1’s MSB is 0 and to K2 = (K1 << 1) ⊕ 87 otherwise.

Given K1 and K2, CMAC works like CBC-MAC, except for the last block. If the final message chunk Mn is exactly the size of a block, CMAC returns E(K, Mn ⊕ Cn−1 ⊕ K1) as a tag, as Figure 7-3 illustrates.

![](bbox=[0.22, 0.28, 0.58, 0.38])

Figure 7-3: The CMAC block cipher–based MAC construction when the message is a sequence of integral blocks

If Mn has fewer bits than a block, CMAC pads it with a 1 bit and 0s and returns E(K, Mn ⊕ Cn−1 ⊕ K2) as a tag, as in Figure 7-4.

![](bbox=[0.22, 0.57, 0.58, 0.67])

Figure 7-4: The CMAC block cipher–based MAC construction when the last block of the message has to be padded with 1 bit and zeros to fill a block

The first case uses only K1 and the second only K2, but both use the main key K to process the message chunks that precede the final one.

Unlike the CBC encryption mode, CMAC doesn’t take an IV as a parameter and is deterministic: for the same key, CMAC always returns the same tag for a given message, M, because the computation of CMAC(M) isn’t randomized—and that’s fine because unlike encryption, MAC computation doesn’t have to be randomized to be secure, which eliminates the burden of having to choose random IV.