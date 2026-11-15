Example Below are some examples of valid and invalid PKCS#7 padding (using 16-byte blocks):

01 34 11 d9 81 88 05 57 1d 73 c3 05 05 05 05 05 => valid
95 51 05 4a d6 5a a3 44 af b3 85 03 03 03 03 03 => valid
71 da 77 5a 5e 77 eb a8 73 c5 50 b5 81 d5 96 01 => valid
5b 1c 01 41 5d 53 86 4e e4 94 13 e8 7a 89 c4 71 => invalid
d4 0d d8 7b 53 24 c6 d1 af 5f d6 f6 04 c0 04 04 => invalid

**ISO/IEC 7816-4 standard:** The data is padded with a `80` byte followed by null bytes. To remove the padding, remove all trailing null bytes and ensure that the last byte is `80` (and then remove it too).

The significance of `80` is clearer when you write it in binary as `10000000`. So another way to describe this padding scheme is: append a `1` bit, and then pad with `0` bits until reaching the blocklength. To remove the padding, remove all trailing `0` bits as well as the rightmost `1` bit. Hence, this approach generalizes easily to padding data that is not a multiple of a byte.

Example Below are some examples of valid and invalid ISO/IEC 7816-4 padding (using 16-byte blocks):

01 34 11 d9 81 88 05 57 1d 73 c3 80 00 00 00 00 => valid
95 51 05 4a d6 5a a3 44 af b3 85 03 03 80 00 00 => valid
71 da 77 5a 5e 77 eb a8 73 c5 50 b5 81 d5 96 80 => valid
5b 1c 01 41 5d 53 86 4e e4 94 13 e8 7a 89 c4 71 => invalid
d4 0d d8 7b 53 24 c6 d1 af 5f d6 f6 c4 00 00 00 => invalid

The choice of padding scheme is not terribly important, and any of these is generally fine. Just remember that **padding schemes are not a security feature!** Padding is a public method for encoding data, and it does not involve any secret keys. The only purpose of padding is to enable functionality — using block cipher modes like CBC with data that is not a multiple of the block length.

Furthermore, as we will see in the next chapter, padding is associated with certain attacks against improper use of encryption. Even though this is not really the fault of the padding (rather, it is the fault of using the wrong flavor of encryption), it is such a common pitfall that it is always worth considering in a discussion about padding.

# Ciphertext Stealing

Another approach with a provocative name is **ciphertext stealing** (CTS, if you are not yet tired of three-leter acronyms), which results in ciphertexts that are not a multiple of the blocklength. The main idea behind ciphertext stealing is to use a standard block-cipher mode that only supports full blocks (e.g., CBC mode), and then **simply throw away some bits of the ciphertext**, in such a way that decryption is still possible. If the last plaintext blocks is j bits short of being a full block, it is generally possible to throw away j bits of the ciphertext. In this way, a plaintext of n bits will be encrypted to a ciphertext of blen + n bits, where blen is the length of the extra IV block.