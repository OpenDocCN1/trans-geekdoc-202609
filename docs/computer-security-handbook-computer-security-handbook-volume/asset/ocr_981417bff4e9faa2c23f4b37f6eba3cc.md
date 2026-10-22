so that the first set of ciphertext characters are under 1, the second under 2, and so on:

Key:      3   7   5   8   1   4   2   6
Plaintext: s   e   l   l   e   n   t   i
          r   e   p   o   r   t   f   o
          l   i   o   n   o   w   a   n
          d   b   u   y   g   o   l   d

Ciphertext: EROGT FALSRLDNTWOLPOUIONDEEIBLONY

Although more complex, this transposition will still yield to cryptanalysis because it retains the letter frequency characteristics of the plaintext. The analyst also would look for digraphs and trigraphs while playing around with columns and rows of different length. (Kahn describes French code breakers during World War I literally cutting text into strips and sliding them up and down against each other to break German transposition ciphers.)

What makes transposition difficult to decipher is additional stages of encryption. For example, if the previous ciphertext is run through the system again, using the same key, all semblance of pattern seems to disappear.

Key:      3   7   5   8   1   4   2   6
Plaintext: e   r   o   g   t   f   a   l
          s   r   l   d   n   t   w   o
          l   p   o   u   i   o   n   d
          e   e   i   b   l   o   n   y

Ciphertext: TNILAWNNESLEFT...OOOLOLODYRRPEGDUB

The development of increasingly complex multiple-transposition ciphers pointed out the positive effects of multiple stages of encryption, which also apply to substitution ciphers. The prime examples of this are the rotor machines used by the Germans and Japanese in World War II. Some of the insights gained during the attack on German codes, such as Alan Turing’s 1940 work on the application of information statistics to cryptanalysis, were considered so important that they remained classified for more than 50 years.

Although they eventually were defeated by Allied cryptanalysts, electromechanical systems such as Enigma were not only the most sophisticated precomputer encryption systems, but the effort to crack them was also a major catalyst in the development of computer systems themselves. When people started applying computer systems to code making rather than code breaking, they quickly hit on the idea of chopping plaintext into pieces, or blocks, for easier handling. The term “block cipher” is used to describe ciphers that encrypt one block (e.g., 8 bytes of data) at a time, one block after another. Another result of computerizing the encryption process is a class of ciphers known as product ciphers. A product cipher has been defined as “a block cipher that iterates several weak operations such as substitution, transposition, modular addition/multiplication [such as XOR], and linear transformation.”34

The mathematics of product ciphers are beyond the scope of this chapter, but it is useful to note that “[n]obody knows how to prove mathematically that a product cipher is completely secure . . . [A] product cipher should act as a ‘mixing’ function