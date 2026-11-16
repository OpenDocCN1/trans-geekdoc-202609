# # Rivest Cipher Algorithms

*Rivest cipher* is a general term for a family of ciphers designed by Ron Rivest, including RC2, RC4, RC5, and RC6. Ron Rivest is one of the creators of RSA. RC1 was never released, and RC3 was broken by cryptanalysis before its release.

RC2 is an early algorithm in the series. It features a variable-key-size, 64-bit block cipher that can be used as a drop-in substitute for DES.

RC4 is a fast stream cipher that is faster than block mode ciphers, and it was widely used. It was especially suitable for low-power devices. The 40-bit version is used in Wired Equivalent Privacy (WEP). Although only 40-bit keys (together with a 24-bit IV, creating 64-bit WEP) were specified by the 802.11 standard, many vendors tried to strengthen the encryption through a de facto deployment of a 104-bit key (with the 24-bit IV, making 128-bit WEP).

RC5 is a block-based cipher in which the number of rounds can range from 0 to 255, and the key can range from 0 bits to 2,048 bits. RC6 is similar; it uses a variable key size and key rounds. RC6 added two features (integer multiplication and four 4-bit working registers) not found in RC5.

# # Asymmetric Encryption

Asymmetric encryption is unlike symmetric encryption in that it uses two unique keys, as shown in Figure 4.19. What one key encrypts the other key must decrypt. One of the greatest benefits of asymmetric encryption is that it overcomes one of the big barriers of symmetric encryption: key distribution.