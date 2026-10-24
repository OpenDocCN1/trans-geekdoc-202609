*R* is shifted 20 positions to *L*, and so on. Figure 1-3 illustrates this principle when encrypting the sentence *THEY DRINK THE TEA*.

![](bbox=[0.115, 0.121, 0.914, 0.272])

The Vigenère cipher is clearly more secure than the Caesar cipher, yet it’s still fairly easy to break. The first step in decrypting it is to figure out the key’s length. Take the example in Figure 1-3, wherein *THEY DRINK THE TEA* encrypts to *WBLBXYLHRWBLWYH* with the key *DUH*. (Spaces are usually removed to hide word boundaries.) Notice that in the ciphertext *WBLBXYLHRWBLWYH*, the group of three letters *WBL* appears twice in the ciphertext at nine-letter intervals. This suggests that the same three-letter word was encrypted using the same shift values, producing *WBL* each time. A cryptanalyst can then deduce that the key’s length is either nine or a value that divides nine (that is, three). Furthermore, they may guess that this repeated three-letter word is *THE* and therefore determine *DUH* as a possible encryption key.

The second step to breaking the Vigenère cipher is to determine the actual key using a method called *frequency analysis*, which exploits the uneven distribution of letters in languages. For example, in English, *E* is the most common letter, so if you find that *X* is the most common letter in a ciphertext, then the most likely plaintext value at this position is *E*.

Despite its relative weakness, the Vigenère cipher may have been good enough to securely encrypt messages in its time. Frequency analysis is limited in that it requires a few sentences, meaning it won’t work if the cipher is used to encrypt short messages. Also, most messages needed to be secret for short periods of time, so it didn’t matter if ciphertexts were eventually decrypted by the enemy. (The 19th-century cryptographer Auguste Kerckhoffs estimated that most encrypted wartime messages required confidentiality for only three to four hours.)

# How Ciphers Work

Basing ourselves on the simplistic Caesar and Vigenère ciphers, we can try to abstract out the workings of a cipher by identifying its two main components: a permutation and a mode of operation. A *permutation* is a function that transforms an item (in cryptography, a letter or a group of bits) such that each item has a unique inverse (for example, the Caesar cipher’s