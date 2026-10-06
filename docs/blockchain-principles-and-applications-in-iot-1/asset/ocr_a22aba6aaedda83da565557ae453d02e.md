![](bbox=[0.268, 0.103, 0.732, 0.613])

**FIGURE 15.4**
Block diagram of CLEFIA encryption.

# # 15.5 Lightweight Stream Cipher

Another lightweight cryptographic primitive is a lightweight stream cipher. This type of cipher uses a key whose size is equivalent to the data. European Network of Excellence for Cryptology organized the eSTREAM competition, to find out new ciphers that might be suitable for widespread adoption. In stream cipher, the plaintext, an initialization vector and key stream together performs XOR to generate cipher text. The operation is performed in bit using a key stream, generated from a key. Stream ciphers are potentially more compact for such a type of bit operation. The hardware implementation of stream cipher is much simpler and faster than so-called block ciphers. In a stream cipher, two types of shift registers are generally used. One is a linear feedback shift register (LFSR), and the second one is a nonlinear feedback shift