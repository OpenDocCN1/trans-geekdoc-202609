
# CHAPTER 9 Algorithm Types and Modes

![](img/e08b4270295105438dabfbd9a81857bf_218_0.png)

Figure 9.5 Ciphertext stealing in CBC mode.

block containing the error is completely garbled. The subsequent block has a 1-bit error in the same position as the error.

This property of taking a small ciphertext error and converting it into a large plaintext error is error extension. It is a major annoyance. Blocks after the second are not affected by the error, so CBC mode recovers and continues to work for all subsequent blocks. CBC is an example of a block cipher being used in a self-synchronizing manner, but only at the block.

While CBC mode recovers from errors, it doesn't recover at all synchronization errors. If a bit is added or deleted from the ciphertext stream, then all subsequent blocks are shifted one out of position and decryption will generate garbage infinity. Any encryption that uses CBC mode must ensure that the block structure remains intact, either by framing or storing data in multiple-sized chunks.

## Security Problems

Some potential problems are caused by the structure of CBC. First, because a ciphertext block affects the following in a simple way, Mallory can add bits to the end of an encrypted message without being detected. It will probably decrypt to gibberish, but in some situations this is undesirable.

If you are using CBC, you should structure your plaintext so that you know where the message ends and can detect the addition of extras.

Second, Mallory can alter a ciphertext bit to introduce controlled changes in the decrypted plaintext block. For example, if Mallory toggles a single ciphertext bit, the entire block will decrypt incorrectly, but the following will have a 1-bit error in the corresponding position. There are situations where this is desirable. The entire plaintext message should include some kind of controlled redundancy or authentication.

Finally, although plaintext patterns are concealed by chaining, very long messages will still have patterns. The birthday paradox predicts that there will be identical blocks $2^{m/2}$ blocks, $m$ is the block size. For a 64-bit block size, that's 34 gigabytes. A message has to be pretty long before this is a problem.

## 9.4 Stream Ciphers

Stream ciphers convert plaintext to ciphertext 1 bit at a time. The simplest implementation of a stream cipher is shown in Figure 9.6. A **keystream generator** (sometimes called a running-key generator) outputs a stream of bits: $k_1, k_2, k_3, \dots, k_i$. This keystream (sometimes called a running key) is XORed with a stream of plaintext bits, $p_1, p_2, \dots, p_i$, to produce the stream of ciphertext bits.

$c_i = p_i \oplus k_i$.

At the decryption end, the ciphertext bits are XORed with an identical keystream to recover the plaintext.

$p_i \oplus k_i \oplus k_i = p_i$

Since this works nicely.

The system's security depends entirely on the insides of the keystream generator. If the keystream generator outputs an endless stream of zeros, the ciphertext will equal the plaintext and the operation will be worthless. If the keystream generator spins out a repeating 16-bit pattern, the algorithm will be a simple XOR with negligible security (see Section 1.4). If the keystream generator spins out an endless stream of random [not pseudo-random, but real random—see Section 2.8 bits], you have a one-time pad and perfect security.

The reality of stream cipher security lies somewhere between the simple XOR and the one-time pad. The keystream generator generates a bit stream that looks random, but actually a deterministic stream that can be flawlessly reproduced at decryption time. The closer the keystream generator's output is to random, the harder a cryptanalyst will have in breaking it.

![](img/e08b4270295105438dabfbd9a81857bf_219_0.png)

Figure 9.6 Stream cipher.

If, however, the keystream generator produces the same bit stream every time it is turned on, the resulting cryptosystem will be trivial to break. An example will show why.

If Eve has a ciphertext and associated plaintext, she can XOR the plaintext and the ciphertext to recover the keystream. Or, if she has two different ciphertexts encrypted with the same keystream, she can XOR them together and get plaintext messages XORed with each other. This is easy to break, and then she can XOR one of the plaintexts she intercepts with the ciphertext to get the keystream.

Now, when Eve intercepts another ciphertext message, she has the keystream necessary to decrypt it. In addition, she can decrypt and read any old ciphertext messages she has previously intercepted. When Eve gets a single plaintext/ciphertext pair, she can read everything.

This is why all ciphers have keys. The output of the keystream generator is a function of the key. Now, if Eve has a plaintext/ciphertext pair, she can only read messages encrypted with a single key. Change the key, and the adversary is ending back to square. Stream ciphers are especially useful for never-ending streams of communications traffic: a T-1 link between two computers, for example.

A keystream generator has three basic parts (see Figure 9.7). The internal state describes the current state of the keystream generator. Two keystream generators, with the same key and the same internal state, produce the same keystream. The output function takes the internal state and generates a keystream. The output function takes the internal state and generates a keystream.

## 9.5 Self-Synchronizing Ciphers

Block ciphers can also be implemented as a self-synchronizing stream cipher, this is called cipher-feedback (CFB) mode. With CBC mode, encryption cannot begin until a complete block of data is received. This is a problem in some applications. In a secure network, a terminal must be able to transmit character to character as it is entered.

## 9.6 CIPHER-FEEDBACK MODE

CFB mode can be encrypted in units smaller than the block size. The following example will encrypt one character at a time (this is 8-bit CFB), but nothing is sacred about the number. You can encrypt data one bit at a time using 1-bit CFB, although using one complete encryption of a block cipher for a single seems like a lot of work; a stream cipher would be a better idea. (Reducing the number of rounds of the block cipher to speed things up is not recommended.)
