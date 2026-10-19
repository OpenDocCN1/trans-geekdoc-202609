
To illustrate why an IV is needed when using block ciphers, consider how they are used in various modes of operation using block ciphers. The simplest mode is the Electronic Code Book (ECB) mode where the plaintext is divided into blocks and each block is encrypted separately. However, in the Cipher-Block Chaining (CBC) mode, each block of plaintext is XORed with the previous ciphertext block before being encrypted. In the ECB mode, the same plaintext will encrypt to the same ciphertext for the same key. This reveals patterns in the code.

In the CBC mode, each block is XORed with the result of the encryption of the previous block. This hides patterns. However, two similar plaintexts that have been encrypted using the same key will yield the same ciphertext up to the block containing the first difference. This problem can be avoided by adding an IV block, which starts the keystream randomization process for the first real block, to the plaintext. This will make each ciphertext unique, even when similar plaintext is encrypted with the same key in the CBC mode. There is no need for the IV to be secret, in most cases, but it is important that it is never reused with the same key. Reusing an IV leaks some information about the first block of plaintext and about any common prefix shared by the two messages. Therefore, the IV must be randomly generated at encryption time.

## Key Length

Key length is another important aspect of key management to consider when generating cryptographic keys. Key length is the size of a key, usually measured in bits or bytes, which a cryptographic algorithm uses in ciphering or deciphering protected information. As discussed earlier, keys are used to control how an algorithm operates so that only the correct key can decipher the information. The resistance to successful attacks against the key and the algorithm, aspects of their cryptographic security, is of concern when choosing key lengths. An algorithm’s key length is distinct from its cryptographic security. Cryptographic security is a logarithmic measure of the fastest known computational attack on the algorithm, also measured in bits. The security of an algorithm cannot exceed its key length. Therefore, it is possible to have a very long key and yet it provides low security. As an example, three-key (56 bits per key) Triple DES (i.e., Triple Data Encryption Algorithm aka TDEA) can have a key length of 168 bits but, due to the meet-in-the-middle attack (discussed later), the effective security that it provides is at most 112 bits. However, most symmetric algorithms are designed to have security equal to their key length. A natural inclination is to use the longest key possible, which may make the key more difficult to break. However, the longer the key, the more computationally expensive the encrypting and decrypting process can be. The goal is to make breaking the key cost more (in terms of effort, time, and resources) than the worth of the

The problem with such a system is that because the letters are the same as the plaintext, no substitution has taken place, just a reordering of the letters; the ciphertext is still susceptible to frequency analysis and other cryptographic attacks.

## Rectangular Substitution Tables

The use of rectangular substitution tables was an early form of cryptography. The sender and receiver decided on the size and structure of a table to hold the message and then the order in which to read the message.

Using the same plaintext as the previous example ("Purchase gold and oil stocks") and placing it in a rectangular substitution block results in the following:

| P | U | R | C | H |
|---|---|---|---|---|
| A | S | E | G | O |
| L | D | A | N | D |
| O | I | L | S | T |
| O | C | K | S |  |

Reading the table in a top-down manner would produce the following ciphertext:

```
PALOOUSDICREALKCGNSSHODT
```

Of course, the sender and receiver could agree on reading the table any way – bottom up, diagonally – that suited them.

## Monoalphabetic and Polyalphabetic Ciphers

The Caesar cipher is a simple substitution algorithm that merely shifted the plaintext over three places to create the ciphertext. This was a monoalphabetic system – the substitution was one alphabet letter for another. In the case of the Caesar cipher, the replacement alphabet was offset by three places:

| A | B | C | D | E | F | G | H | I | J | K | ... | Z |
|---|---|---|---|---|---|---|---|---|---|---|-----|---|
| D | E | F | G | H | I | J | K | L | M | N | ... | C |

There is also the scrambled alphabet. In this case, the substitution alphabet is a scrambled version of the alphabet. It could look like this, for example:

| A | B | C | D | E | F | G | H | I | J | K | ... | Z |
|---|---|---|---|---|---|---|---|---|---|---|-----|---|
| M | G | P | U | W | I | R | L | O | V | D | ... | K |

Using the scrambled alphabet above, one can see that the plaintext of BAKE would be substituted as GMDW. The problem with monoalphabetic ciphers, however, is that they are still subject to the characteristics of the plaintext language – an E, for example, would be substituted as a W throughout the ciphertext. That would mean the letter W in the ciphertext would appear as frequently as an E in plaintext. That makes a cryptanalytic attack of a monoalphabetic system fairly simple.

The use of several alphabets for substituting the plaintext is called a polyalphabetic cipher. It is designed to make the breaking of a cipher by frequency analysis more difficult. Instead of substituting one alphabet for another, the ciphertext is generated from several possible substitution alphabets.

For Example:

| Plaintext | A | B | C | D | E | F | G | H | I | J | K | ... | Z |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Substitution 1 | M | G | P | U | W | I | R | L | O | V | D | ... | K |
| Substitution 2 | V | K | P | O | I | U | Y | T | J | H | S | ... | A |
| Substitution 3 | L | P | O | I | J | M | K | H | G | T | U | ... | F |
| Substitution 4 | N | B | V | C | X | Z | A | S | D | E | Y | ... | W |

Using this table, substitute the plaintext FEED as IIJC, using the substitution alphabets in sequence. The power of using multiple alphabets in this example is evident, as the repeated E in the plaintext is substituted for different results in the ciphertext. The
ciphertext has a repeated I, and yet that is for different plaintext values.

## Blaise de Vigenère

Blaise de Vigenère, a Frenchman, developed the polyalphabetic cipher using a key word and 26 alphabets, each one offset by one place. This is shown in the following table. The top row of the table would be the plaintext values and the first column of the table the substitution alphabets.

|   | A | B | C | D | E | F | G | H | I | J | K | L | ... | Z |
|---|---|---|---|---|---|---|---|---|---|---|---|-----|---|
| A | A | B | C | D | E | F | G | H | I | J | K | L | ... | Z |
| B | B | C | D | E | F | G | H | I | J | K | L | M | ... | A |
| C | C | D | E | F | G | H | I | J | K | L | M | N | ... | B |
| D | D | E | F | G | H | I | J | K | L | M | N | O | ... | C |
| E | E | F | G | H | I | J | K | L | M | N | O | P | ... | D |
| F | F | G | H | I | J | K | L | M | N | O | P | Q | ... | E |
| G | G | H | I | J | K | L | M | N | O | P | Q | R | ... | F |
| H | H | I | J | K | L | M | N | O | P | Q | R | S | ... | G |
| I | I | J | K | L | M | N | O | P | Q | R | S | T | ... | H |
| J | J | K | L | M | N | O | P | Q | R | S | T | U | ... | I |
| K | K | L | M | N | O | P | Q | R | S | T | U | V | ... | J |
| L | L | M | N | O | P | Q | R | S | T | U | V | W | ... | K |
| ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... |
| Z | Z | A | B | C | D | E | F | G | H | I | J | K | ... | Y |

The sender and the receiver of the message would agree on a key to use for the message; in this case, one could use the word FICKLE as the key. Just as in the running cipher shown below, one would repeat the key for the length of the plaintext.

To encrypt the message "HIKE BACK," it would be constructed as follows:
