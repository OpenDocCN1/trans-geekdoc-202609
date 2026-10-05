in a block cipher, the sender-end has to wait for one block of data to be received; only then can encryption be performed.

# 6.7.4 Block/Stream Cipher Modes of Operation

There are five modes of operation in the following list that are commonly used. Some of these modes are suitable for both the block and stream cipher, but some modes are suitable only for the block cipher.

+   - Electronic Code Book (ECB) Mode
- Cipher Block Chaining (CBC) Mode
- Cipher Feedback (CFB) Mode
- Output Feedback (OFB) Mode
- Counter (CTR) Mode

# 6.7.4.1 Electronic Code Book (ECB) Mode

+   - ECB is the simplest mode, in which the plaintext is handled 64 bits at a time and each block of plaintext is encrypted using the same key. ECB secures transmission of a single value.
- The plaintext is divided into blocks of, for example, $n$ bits each. If the plaintext length is not a whole number multiple of $n$ the last block is padded with some dummy bits to make its length
- Each block is encrypted using the “Encrypt” function and secret key $K$ The secret key is communicated to the intended recipients by means
- At the receiving end the decryption is performed, using the “Decrypt” function and the same key $K$
- The plaintext consists of a sequence of 64-bit blocks $P_1, P_2, ..., P_n$ corresponding to a sequence of cipher-text blocks $C_1, C_2, ..., C_n$.

# 6.7.4.1.1 Encryption and Decryption of ECB

# Encryption of ECB

Figure 6.15 shows the Electronic Code Book (ECB) Mode encryption.