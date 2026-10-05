# MODERN SYMMETRIC CIPHERS • 257

+   The Shift Register is initialized to a value (IV), which is communicated by secure means to the intended recipient of the message.

+   The contents of the Shift Register are encrypted using a secret key K The value of K is also communicated by secure means to the intended recipient of the message.

+   Most significant s bits from the encrypted contents of the shift register XORed with s-bit plaintext block P1 generating s-bit cipher-text block C1

+   The contents of the shift register are shifted left-bits and the s-bit cipher-text C1 is placed in the lowest s-bits of the shift register.

+   Now, the contents of the shift register are encrypted using the key K, and the encrypted contents are used for generation of cipher-text C2 for plaintext P2 This process is repeated for all subsequent plaintext blocks.

# 6.7.4.3.1 Encryption and Decryption of CFB

A schematic diagram of the CFB Encryption/Decryption is indicated in Figure 6.19.

![](bbox=[0.15, 0.532, 0.85, 0.915])