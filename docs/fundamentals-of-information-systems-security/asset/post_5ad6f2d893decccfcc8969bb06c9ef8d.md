
- Given some random input, you can generate associated key pairs that are inverses of each other—Any party can create public-private key pairs, keep one private, and post the other in a directory for any correspondent to use. Because the private key is secret and never transmitted, an eavesdropper cannot learn this value.

Here's how public key cryptography works. Suppose Bob wants to send Alice a message. Alice has already created her private key, which she keeps safe, and her public key, which she puts on her website. Bob uses Alice's public key to encrypt the message, “Hi Alice!” Bob then sends the encrypted message to Alice. Because Bob used Alice's public key to encrypt the message, Alice can decrypt it only with her private key. Because she has access to her private key, she uses it to decrypt and read the message, “Hi Alice!” If Alice wanted to respond to Bob's message, she could encrypt her response with Bob's public key and send the message back to Bob.

One of the closest equivalents in the everyday business world to asymmetric key ciphers is the night deposit box at a bank. A merchant takes his receipts to the bank, opens the slot with his key, and drops the money down the chute. The envelope slides down and into the safe. If he turned around and a robber held him up at gunpoint and demanded his key, the merchant can safely surrender the key and run away. The robber can attempt to recover the money, but because the envelope has dropped out of reach, the robber will be unable to access it. The next morning, the bank officer can use her key to open the safe, remove the money, and deposit it into the merchant's account. Each party has a different key, but they are associated with each other. Make this process reversible, where the bank officer could leave messages for the merchant, and you have the equivalent of an asymmetric or public key cryptosystem.

## Cryptanalysis and Public Versus Private Keys

Encryption makes plaintext unreadable to anyone except an authorized person with the right software and key. If the data are valuable, however, cybercriminals may try to break the encryption.

You can break a cipher in two ways:

- Analyzing the ciphertext to find the plaintext or key
- Analyzing the ciphertext and its associated plaintext to find the key

A cipher is unconditionally secure if no amount of ciphertext will give enough information to yield a unique plaintext. You can break almost any cipher, given enough time and resources. However, a cipher’s main purpose is to make it so difficult to break that it is computationally infeasible to crack. For example, assume that an organization generates new keys every week. If an attacker can crack any key in 13 days, the cracked keys would be useless by the time the attacker tried to use it; it would already have been superseded by a new key. Thus, a cipher that an attacker cannot break economically (relative to the value of the protected data) is strong or computationally secure.

> The only unbreakable cryptographic cipher is the Vernam cipher. Another name for it is a one-time pad cipher. You’ll read more about that later in this chapter. You can also find out more about the Vernam cipher at www.pro-tech-nix.com/information/crypto/pages/vernam_base.html.

There are four basic forms of cryptographic attack:

- **Ciphertext-only attack (COA)**—In a ciphertext-only attack, the cryptanalyst has access only to a segment of encrypted data and has no choice as to what those data may be. An example is the cryptogram in some daily newspapers. Note, however, that by understanding the context of the information, one can infer that certain words or formatting may be present. FIGURE 9-3 shows a ciphertext-only attack. The sample of ciphertext is available, but the plaintext associated with it is not.

- **Known-plaintext attack (KPA)**—In a known-plaintext attack, the cryptanalyst possesses certain pieces of information before and after encryption. For example, all secure logon sessions may begin with the characters LOGON, and the next transmission may be PASSWORD. A secure encryption cipher should resist an attack by an analyst who has access to numerous plaintext-ciphertext pairs. FIGURE 9-4 shows a known-plaintext attack.

- **Chosen-plaintext attack**—In a chosen-plaintext attack, the cryptanalyst can encrypt any information and observe the output. This is the best case for the cryptanalyst. It offers the most flexibility (and insight) into the encryption mechanism. An example is the encryption offered by older versions of Microsoft Office software applications. You could encrypt only the letter A, then B, and so on, to try to discern what the cipher is doing.

![](img/b2a7c1cdb4938c3b37d6925de0425ae9_328_0.png)

![](img/b2a7c1cdb4938c3b37d6925de0425ae9_328_1.png)

- **Chosen-ciphertext attack**—A chosen-ciphertext attack is a special case. It is relevant in asymmetric key systems and hash functions. In a chosen-ciphertext attack, cryptanalysts submit data coded with the same cipher and key they are trying to break to the decryption device to see either the plaintext output or the effect the decrypted message has on some system. As a simple example, consider an owner who trains a guard dog to respond only to commands spoken in Navajo. A burglar doesn’t know Navajo, but he can make a series of noises and sounds. The dog ignores nonsense (from its perspective) but obeys valid commands. Speaking enough gibberish, the burglar might prompt a response from the dog (even if not the response he seeks). By observing the dog’s reaction to various apparently nonsensical commands, the burglar might be able to make the dog lie down and play dead. Chosen-ciphertext attacks have particular uses in attacking encrypted email. The complexity of the mathematics involved is too great to allow a discussion of them here.

## Symmetric and Asymmetric Key Cipher Resistance to Attack

Cryptanalysis has several objectives, including the following:

- Derive the plaintext of a target message.
- Determine the key used to encrypt a target message.
- Derive the algorithm used by a particular cipher.
- Solve the general mathematical problem underlying the cryptography.

Cryptographers use many tools in cryptanalysis. They have such names as linear cryptanalysis, differential cryptanalysis, brute force, exhaustive search, and information theory. In the most direct case, the analyst must use an encrypted message to derive its associated plaintext. Many ciphers used today are open source. That means that the analyst has access to the logic for the encryption and decryption functions. The security of closed-source or proprietary ciphers stems in part from the fact that the analyst does not necessarily know how the cipher works.

For example, the United States did not have access to a Japanese Purple cipher device in World War II. Codebreakers had to determine how the machine worked by analyzing faint patterns in the ciphertext. Once they figured that out, analysts could then change the order of different keys to decrypt message traffic. Once they identified the key, anyone could read all traffic coded for that time period with the same key.

In some cases, analysts found a solution by attacking the underlying mathematics of a cryptosystem. In the late 1970s, some vendors made security products that used asymmetric key cryptography based on a simplified version of the knapsack problem called the _subset sum_ problem. Unfortunately for the vendors, Len Adleman developed a general solution to the subset sum problem in 1982 that could run on an Apple II computer. Overnight, an entire class of security products became obsolete.

Today, the basis of most commercial asymmetric key cryptography is the difficulty of factoring large numbers. For example, it is relatively easy with pen and paper to calculate 757 × 769 = 582,133. Yet given the result 582,133, deriving its two factors is not as easy. The classic approach would involve trying 2, 3, 5, 7, 11, 13, etc., until a prime factor is found. That would take 134 guesses. Although this becomes much easier with a computer, imagine that the two prime factors are 100 digits each! Just to put this into perspective, here is a 100-digit prime number:
