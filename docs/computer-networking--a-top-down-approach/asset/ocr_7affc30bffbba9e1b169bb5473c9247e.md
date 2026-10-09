Plaintext letter: a b c d e f g h i j k l m n o p q r s t u v w x y z

$C_1(k=5)$: f g h i j k l m n o p q r s t u v w x y z a b c d e

$C_2(k=19)$: t u v w x y z a b c d e f g h i j k l m n o p q r s

![](bbox=[0.25, 0.22, 0.76, 0.24])

monoalphabetic cipher to encode a letter in a specific position in the plaintext message. Thus, the same letter, appearing in different positions in the plaintext message, might be encoded differently. An example of a polyalphabetic encryption scheme is shown in Figure 8.4. It has two Caesar ciphers (with *k* = 5 and *k* = 19), shown as rows. We might choose to use these two Caesar ciphers, C$_{1}$ and C$_{2}$, in the repeating pattern C$_{1}$, C$_{2}$, C$_{2}$, C$_{1}$, C$_{2}$. That is, the first letter of plaintext is to be encoded using C$_{1}$, the second and third using C$_{2}$, the fourth using C$_{1}$, and the fifth using C$_{2}$. The pattern then repeats, with the sixth letter being encoded using C$_{1}$, the seventh with C$_{2}$, and so on. The plaintext message “bob, i love you” is thus encrypted “ghu, n etox dhz.” Note that the first *b* in the plaintext message is encrypted using C$_{1}$, while the second *b* is encrypted using C$_{2}$. In this example, the encryption and decryption “key” is the knowledge of the two Caesar keys (*k* = 5, *k* = 19) and the pattern C$_{1}$, C$_{2}$, C$_{2}$, C$_{1}$, C$_{2}$.

# Block Ciphers

Let us now move forward to modern times and examine how symmetric key encryption is done today. We focus on block ciphers, which are used in many secure Internet protocols, including PGP (for secure e-mail), TLS (for securing TCP connections), and IPsec (for securing the network-layer transport).

In a block cipher, the message to be encrypted is processed in blocks of *k* bits. For example, if *k* = 64, then the message is broken into 64-bit blocks, and each block is encrypted independently. To encode a block, the cipher uses a one-to-one mapping to map the *k*-bit block of cleartext to a *k*-bit block of ciphertext. Let’s look at an example. Suppose that *k* = 3, so that the block cipher maps 3-bit inputs (cleartext) to 3-bit outputs (ciphertext). One possible mapping is given in Table 8.1. Notice that this is a one-to-one mapping; that is, there is a different output for each input. This block cipher breaks the message up into 3-bit blocks and encrypts each block according to the above mapping. You should verify that the message 010110001111 gets encrypted into 101000111001.

Continuing with this 3-bit block example, note that the mapping in Table 8.1 is just one mapping of many possible mappings. How many possible mappings are there? To answer this question, observe that a mapping is nothing more than a permutation of all the possible inputs. There are 2$^{3}$ (= 8) possible inputs (listed under the