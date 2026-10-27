be an error in the corresponding plaintext block, and it will then creep into the shift register, where it will cause further errors until it is shifted all the way out of the register.

# 13.6.2.4 *Output Feedback Mode*

The operation of Output Feedback (OFB) mode has changed slightly from how it was initially defined. The early version is presented first, and then the update is provided. OFB, like CFB above, allows a block cipher to be used as a stream cipher. In fact, OFB is almost identical to CFB. We can use it to encipher in groups smaller than the block size of the enciphering algorithm. Again, 8 bits will be used for our example. The directions are reproduced below, exactly as for CFB, but with the single change emphasized by being placed in **bold text**.

We start by selecting an initialization vector (IV) of the same size as used by the block cipher. We then compute E(IV) and XOR the leftmost 8 bits of this with the first 8 bits of our message. This provides us with the first 8 bits of the ciphertext, which may then be sent. Now the IV is changed by appending the **8 bits of the enciphered IV** to the right and discarding the 8 leftmost bits. We then repeat the process to encrypt the next 8 bits of the message. This small change makes it possible to generate all of the bytes that will be XORed with the message in advance.

![](bbox=[0.28, 0.413, 0.733, 0.651])

**Figure 13.14  Output Feedback (OFB) mode.**

The only difference between [Figure 13.13](#figure-13-13) and [Figure 13.14](#figure-13-14) is that in the present mode the bits advancing the shift register arise directly from the encryption step, rather than after the XOR. In this mode, an error that creeps into a ciphertext block will affect only the corresponding plaintext block.

At the Crypto ’82 conference held at the University of California, Santa Barbara, a pair of talks addressed weaknesses in using OFB to generate keys in groups of less than 64 bits at a time, as illustrated above. An abstract published in the proceedings of this conference put it bluntly.

The broad conclusion is reached that OFB with *m* = 64 is reasonably secure but OFB with any other value of *m* is of greatly inferior security.[^61]

[^61]: Davies, Donald W. and Graeme I. P. Parkin, “The Average Cycle Size of the Key Stream in Output Feedback Encipherment (Abstract),” in Chaum, David, Ronald L. Rivest, and Alan T. Sherman (editors), *Advances in Cryptology, Proceedings of Crypto 82*, Plenum Press, New York, 1983, pp. 97–98.