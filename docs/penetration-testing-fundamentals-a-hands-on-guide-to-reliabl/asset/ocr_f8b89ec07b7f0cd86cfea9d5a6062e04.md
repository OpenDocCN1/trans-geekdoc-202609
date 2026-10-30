# Rail Fence

All the preceding ciphers we examined are substitution ciphers. Another approach to classic cryptography is the transposition cipher. The rail fence cipher may be the most widely known transposition cipher. You simply take the message you wish to encrypt and alter each letter on a different row. So “attack at dawn” is written as

A  t  c  a  d  w
    t  a  k  t  a  n

Next, you write down the text reading from left to right as one normally would, thus producing

atcadwtaktan

In order to decrypt the message, the recipient must write it out on rows:

A  t  c  a  d  w
    t  a  k  t  a  n

Then the recipient reconstructs the original message. Most texts use two rows as examples; however, this can be done with any number of rows you wish to use.

# Modern Methods

The preceding section was meant to make you comfortable with the essential concepts of cryptography; however, as a penetration tester you need to be familiar with modern methods of cryptography. The historical methods discussed in the last section are no longer used.

It is best if you start with a realistic understanding of cryptography. Unlike what is depicted in many movies, you are unlikely to “crack” modern cryptographic algorithms. Certainly, not in a timeframe that is of any use to you. However, the implementation of cryptography, the passwords used to access an encrypted drive, and the key exchange protocols all at least present the possibility of being subverted or circumvented.

Before we delve too deeply into this topic, let’s start with some basic definitions you will need:

+   - **Key:** The bits that are combined with the plaintext to encrypt it. In symmetric ciphers this is random numbers; in asymmetric ciphers it is the result of some mathematical operation.
+   - **Plaintext:** The unencrypted text.
+   - **Ciphertext:** The encrypted text.
+   - **Algorithm:** A mathematical process for combining the key with the plaintext, to produce the ciphertext.