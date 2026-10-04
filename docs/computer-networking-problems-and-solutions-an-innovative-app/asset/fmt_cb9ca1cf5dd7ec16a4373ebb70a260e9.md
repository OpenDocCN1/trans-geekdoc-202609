
There is one problem with this phrase, however: it is often used out of context. To understand the real meaning of the phrase, you need to go back in time to the origin of encryption algorithms. In the physical lock world, revealing the plans of a lock will often reveal various passageways to bypassing or defeating the lock. This habit was carried over to early software security vendors; the reasoning is if an attacker knows how the encryption algorithm works, he will be able to find ways to defeat the encryption algorithm.

But encryption algorithms are not door locks; what is an important safeguard in one realm can be a dangerous crutch in another. Hiding code developed to encrypt plaintext does not really make the code more secure; in fact, just the opposite happens. Instead of improving security, obscuring encryption code and processes simply prevents experts in the field from finding flaws and possible ways to defeat the code before these are exposed in real deployments. Ultimately, security by obscurity is dangerous in this particular context.

So this is a good principle, but it can be misapplied. For instance, if a network operator attempts to hide internal network architecture, addressing, or even blocking external hosts from reaching internal ones, at least some security experts will counter with “this is simply security by obscurity; you should not do that.” Taken in this sense, however, *encrypting data is also security by obscurity*. Hiding information and hiding information about your infrastructure are both essentially hiding information, and hiding information is essentially a form of obscurity.

How can you tell when you should apply “no security by obscurity,” and when you should not? Perhaps the best rule of thumb is this: hiding processes, algorithms, and implementations is not a useful addition to security in the cyber world. Hiding information, however, often is. It can be hard to apply this rule of thumb in many situations, but it should be a good start in thinking through the issues and making the right decision in each particular case.

What happens if you are using a 128-bit block, and you have 56 bits of data to transport? The most natural thing to do in this situation would be to pad the plaintext with some number; most likely all 0s or all 1s. The quality of the output is dependent, to some degree, on the sparseness of the input; the fewer the range of numbers used as an input, the more predictable the output of the cryptographic function will be. In this case, it is important to use padding that is *as close to random as possible;* there is an entire field of study around how to pad blocks of plaintext to “help” the cryptographic function produce ciphertext that is as close to random as possible.

### Multiple Rounds of Encryption

It is possible to process the same information through a cryptographic function multiple times. For instance, if you have a 128-bit block and a 128-bit key, you can

• Take the plaintext and, using the key, calculate a ciphertext; call this `ct1`.
• Take `ct1` and, using the key, calculate a second-round ciphertext; call this `ct2`.
• Take `ct2` and, using the key, calculate a third-round ciphertext; call this `ct3`.

The actual transmitted ciphertext would be the final `ct3`. What does this process accomplish? Remember the quality of the encryption process is related to the randomness of the output against the input. Each round will, in many situations, increase the randomness just a bit more. There is a point of diminishing returns in this process; normally after the third round, the data is not going to become “any more random,” and hence more rounds are essentially just wasting processing power and time for very little gain.

### Public versus Private Key Cryptography

There is a class of cryptographic functions that can transform the plaintext into ciphertext, and back, using two different keys. This capability is useful when you want to be able to encrypt a block of data with one key and allow someone else to unencrypt the data using a different key. The key you keep secret is called the *private key*, and the key you give to others, or publish, is called the *public key*.

To prove you are the actual sender of a particular file, for instance, you can encrypt the file with your private key. Now anyone with your public key can unencrypt the file, which could only have been sent by you. You would not normally encrypt the entire block of data with your private key (in fact most systems using key pairs are designed so you *cannot* do this); rather a signature is created using your private key that can be verified using your public key. To ensure only the person you want to read something can, you can encrypt some data with her public key, publish it, and only the person with the correct private key can unencrypt it.

Such systems are called public key cryptography (sometimes the names engineers choose are, perhaps, a little *too* obvious), or asymmetric cryptography. In public key cryptography, the public key is often “released into the wild;” it is something anyone with access to a key server or some other source can look up.

The alternative to public key cryptography is symmetric key cryptography. In symmetric key cryptography, the sender and receiver share a single key that is used to both encrypt and unencrypt the data (the shared secret). Given shared secrets are (obviously) difficult to create and use, why is symmetric key cryptography ever used? There are two basic tradeoffs to consider when choosing between symmetric and public/private key cryptography:

• **Processing complexity:** Public key cryptography systems generally require a good deal more processing power to encrypt and unencrypt the transmitted data. Symmetric key systems are generally much easier to develop and deploy in a way that does not require large amounts of processing power and time. Because of this, public key cryptography is often used to encrypt very small amounts of data, such as a private key (see the example in the following section).

• **Security:** Public key cryptography generally requires a somewhat unique set of mathematical transform mechanisms. Symmetrically keyed systems tend to have a wider range of available transforms that are also more complex and hence more secure (they provide more randomness in the output and hence are harder to break).

There is a place for both kinds of systems, given these tradeoffs and real-world requirements.

#### Key Exchange

Some of the earliest cryptographic systems involved wrapping paper around a cylinder of a specific size; the cylinder had to be somehow carried between the two parties to the encrypted communication without being captured by an enemy. In more recent years, pads of keys were physically carried between the two end points of an encrypted system. Some of these were arranged so a particular page would be used for a certain time period and then ripped out, securely destroyed, and replaced by a new page for the next day. Others were designed so each page in the pad would be used to encrypt one message, at which point the page would be ripped out and replaced—a one-time pad.

**Note**

The concept of a one-time pad has been carried into the modern world with authentication systems that allow the user to create a code that is used once, and then discarded, to be replaced by a new code the next time the user tries to authenticate. Any system that relies on a code that is used once is still called a one-time pad.

In the modern world, there are other ways you can exchange cryptographic material, whether it is using a shared secret key or retrieving a private key.
