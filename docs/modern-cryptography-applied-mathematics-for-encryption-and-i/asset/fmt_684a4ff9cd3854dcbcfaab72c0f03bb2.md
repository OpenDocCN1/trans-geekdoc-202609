
The KHAZAD algorithm was designed by `Rijmen` (one of the creators of the Rijndael cipher) and `Paulo Barreto`. The name is not an acronym but is derived from a fictional Dwarven kingdom from J.R.R. Tolkien’s books called Khazad-dûm. KHAZAD uses eight rounds on a 64-bit block, applying a 128-bit key. This algorithm is not patented and is free to anyone who wants to use it.

#### NESSIE

In Europe, a project similar to the AES competition, named NESSIE (New European Schemes for Signatures, Integrity, and Encryption), lasted from 2000 to 2003, with the goal of not only finding a new standard symmetric cipher, but also finding secure cryptographic primitives. Cryptographic primitives are discussed frequently in this book.

**Note**

Cryptographic primitives are basic cryptographic algorithms used to build cryptographic protocols. Cryptographic hashes, symmetric algorithms, and asymmetric algorithms all qualify as cryptographic primitives. These primitives are combined to create cryptographic protocols such as Secure Sockets Layer (SSL) and Transport Layer Security (TLS), which you will study in [Chapter 13](#part0024.xhtml#ch13).

Several algorithms of various types were selected in the competition, including the block ciphers `MISTY1`, `Camellia`, `SHACAL-2`, and `AES/Rijndael`. `RSA` was also one of the three asymmetric algorithms selected. For cryptographic hashes and message authentication codes, `HMAC` and `SHA` were chosen as well as `Whirlpool`.

#### Stream Ciphers

A stream cipher is a special type of symmetric cipher. Both Feistel ciphers and SPMs break the plain text into blocks and then encrypt each block. Stream ciphers take each bit of plain text and encrypt it with the key stream to produce the cipher text stream. The combination is usually done via XOR operations.

There are two types of stream ciphers: synchronous and self-synchronizing. In a synchronous stream cipher (sometimes called a binary additive stream cipher), the key is a stream of bits produced by some pseudo-random number generator. The production of this key stream is completely independent of the plain text. The key stream is XOR’d with the plain text to produce the cipher text. This is called a *synchronous cipher* because the sender and receiver need to be in synch. If digits are added or removed from the message during transmission (such as by an attacker), that synchronization is lost and needs to be restored.

Self-synchronizing ciphers use parts of the current cipher text to compute the rest of the key stream. In other words, the algorithm starts with an initial key stream, like an initialization vector, and then creates the rest of the key stream based on the cipher text already produced. These types of ciphers are sometimes called cipher text autokeys. The idea was patented in 1946, long before the advent of modern computer systems. With self-synchronizing ciphers, if digits are added or removed in transit, the receiving end can still continue to decrypt.

##### LFSR

There are multiple ways to create the pseudo-random key stream. One of these is to use *linear feedback shift registers* (`LFSR`s). A shift register is a type of register found in digital circuits—basically a chain of flip-flops that shifts the data stored in it by 1 bit, thus the name. `LFSR`s are chosen because they are easy to implement in hardware. An `LFSR` uses its previous state to form the input for the current state.

Usually a linear function is used to modify the data in each round, and most often an XOR is used. The `LFSR` is given an initial value, or seed. Then the register will shift that value and then XOR it with the previous value. Consider this rather simplified example:

Input: `0101110`

First, it is shifted by the `LFSR`:

![Images](Images/image00649.jpeg)

Then that value is XOR’d with the previous state:

![Images](Images/image00650.jpeg)

This can be repeated with yet another shift and another XOR operation. You will see `LSFRs` used later in the book when we discuss pseudo-random number generators.

##### RC4

RC4, designed by `Ron Rivest`, is a widely known and used stream cipher, perhaps the most widely known. The `RC` stands for `Ron`’s cipher or `Rivest` cipher. `Ron Rivest` is a name that is very familiar in cryptography. He is the *R* in *RSA*, which we will explore in [Chapter 10](#part0020.xhtml#ch10). RC4 is widely used in many security situations, including WEP (Wired Equivalent Privacy) and TLS. However, the algorithm was designed in 1987, and some experts have expressed concerns about its security. Some speculate that it can be broken, and many people recommend no longer using it in TLS. Nevertheless, it is the most widely known of stream ciphers and has a similar place in the history and study of stream ciphers as DES has in block ciphers.

###### RC4 Key Scheduling

The key scheduling algorithm is rather simple. It begins with an internal state that is denoted by a capital *S*. This state is a 256-*byte* array. (Although most of what you have seen so far involves bits, not bytes, this is not a typo.) There are two indexes, usually named i and j. These indexes are used to point to individual elements in the array. The key scheduling algorithm involves shuffling this array.

The first step in this algorithm involves initializing the state with what is termed the *identity permutation*. This means that the first element is initialized to 0, the second element to 1, the third to 0, and so on. Now, obviously, this is not very random at all, and in fact it is the antithesis of randomness. So the next step consists of shuffling, which involves iterating 256 times, performing the following actions:

   **1.**  Compute `j = j + S[i] + key[i mod keylength]`.

   **2.**  Swap `S[i]` and `S[j]`.

   **3.**  Increment i.

After 256 iterations of this, the array should be shuffled well. If you happen to have some programming experience, the following pseudo-code may assist you in understanding the shuffling:

![Images](Images/image00651.jpeg)

You may argue that this is too predictable, because it would generate the same key each time. And if the algorithm stopped here, you would be correct. This is generating a state that will be used to create the key stream. But we are not done yet.

The rest of the algorithm allows for the generation of a key stream of any size. The goal is to create a key stream of the same size as the message you want to encrypt.

The first step is to initialize the two pointers i and j, and then generate the key stream 1 byte at a time. For each new byte, the algorithm takes the following steps:

   **1.**  Compute new value of i and j:

        `i := (i + 1) % 256`

        `j := (j + S[i]) % 256`

   **2.**  Swap `S[i]` and `S[j]`.

   **3.**  Retrieve the next byte of the key stream from the S array at the index:

        `S[i] + S[j] % 256`

Again, if you have some background in programming, you may find it easier to understand this using pseudo code:

![Images](Images/image00652.jpeg)

Once you have generated the key stream, you XOR it with the plain text to encrypt, or XOR it with the cipher text to decrypt. One of the security issues with RC4 is that it does not use a *nonce* (a number only used once) along with the key. This means that if a key is being used repeatedly, it can be compromised. More modern stream ciphers, such as eSTREAM, specify the use of a nonce.

In 1994, Rivest published RC5 and then later, working with Matt Robshaw, Ray Sidney, and Yiqun Yin, he released RC6. However, both RC5 and RC6 are block ciphers, not stream ciphers. In fact, RC6 was designed for the AES competition.

##### FISH

The FISH (FIbonacci SHrinking) algorithm was published by the German engineering firm Siemens in 1993. It is a software-based stream cipher using a *Lagged Fibonacci generator* along with a concept borrowed from the shrinking generator ciphers.
