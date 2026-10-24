# 2.7.3 The CFB Mode

In contrast to the CBC mode, the CFB mode begins by encrypting the IV, and then an XOR operation is performed between the bits of the encrypted IV and the corresponding bits of the first block of the image. The result is the encrypted version of the first block. For the encryption of each of the next plaintext blocks, the previous ciphertext block is encrypted, and the output is XORed with the current plaintext block to create the current ciphertext block. The XOR operation conceals plaintext patterns.

Common to the CBC mode, changing the IV to the same plaintext block results in different outputs. Although the IV need not be secret, some applications would see this as desirable [16–18,49,50]. Figure 2.15 shows the CFB mode. The encryption algorithm is

C_j = P_j ⊕ I_j  (2.10)

and the decryption algorithm is

P_j = C_j ⊕ I_j  (2.11)

I_j = E_K(C_{j-1}), j = 1, 2, 3, ...  (2.12)

C_0 = IV  (2.13)

# 2.7.4 The OFB Mode

The OFB mode is similar to the CFB mode. It begins by encrypting the IV. The bits of the encrypted IV are XORed with the corresponding bits of the first plaintext block to obtain the corresponding ciphertext block. Also, the output of the encryption algorithm is used as an input to the next encryption step instead of the IV. This process

![](bbox=[0.08, 0.88, 0.92, 0.96])

Figure 2.15 Using a block cipher in the CFB mode.