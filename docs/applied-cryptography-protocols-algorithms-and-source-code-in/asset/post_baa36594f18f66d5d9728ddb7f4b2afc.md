
## 1.1 Terminology

tion key can decrypt the message. In these systems, the encryption key is often called the **public key**, and the decryption key is often called the **private key**. The private key is sometimes called the secret key, but to avoid confusion with symmetric algorithms, that tag won't be used here.

Encryption using public key $K$ is denoted by:

```
$E_K(M) = C$
```

Even though the public key and private key are different, decryption with the corresponding private key is denoted by:

```
$D_K(C) = M$
```

Sometimes, messages will be encrypted with the private key and decrypted with the public key; this is used in digital signatures (see Section 2.6). Despite the possibility, these operations are denoted by, respectively:

```
$E_K(M) = C$
D_K(C) = M$
```

## Cryptanalysis

The whole point of cryptography is to keep the plaintext [or the key, or both] secret from eavesdroppers [also called adversaries, attackers, interceptors, interlopers, intruders, opponents, or simply the enemy]. Eavesdroppers are assumed to have complete access to the communications between the sender and receiver.

Cryptanalysis is the science of recovering the plaintext of a message without access to the key. Successful cryptanalysis may recover the plaintext or the key. It also results in weaknesses in a cryptographic system [The loss of a key through noncryptanalysis is called a **compromise**].

An attempted cryptanalysis is called an attack. A fundamental assumption in cryptanalysis, first encountered by the Dutch A Kerckhoffs in the nineteenth century, is that the secrecy reside entirely in the key [794]. Kerckhoffs assumes that the cryptyst has complete details of the cryptographic algorithm and implementation. Of course, one would assume that the CIA does not make a hit of telling Mossad about its cryptographic algorithms, but Mossad probably finds out. While real-world cryptanalysts don't always have such detailed information, it is a good assumption to make. If others can't break an algorithm, even with knowledge of how it works, they certainly won't be able to break it without knowledge.

There are four general types of cryptanalytic attacks. Each of them assumes that the cryptanalyst has complete knowledge of the encryption algorithm used:

- 1. **Ciphertext-only attack**. The cryptanalyst has the ciphertext of several messages, all of which have been encrypted using the same encryption algorithm. The cryptanalyst's job is to recover the plaintext of as many messages as possible, or better yet to deduce the key [or keys] used to encrypt the messages, in order to decrypt messages encrypted with the same keys.

Given: $C_1 = E_k(P_1), C_2 = E_k(P_2), \dots C_i = E_k(P_i)$
Deduce: Either $P_1, P_2, \dots P_k$ or an algorithm to infer $P_{i+1}$ from $E_k(C_{i+1})$

- 2. **Known-plaintext attack**. The cryptanalyst has not access to the ciphertext of several messages, but also to the plaintext of those messages. His job is to deduce the key (or keys) used to encrypt the messages or an algorithm to decrypt any new messages encrypted with the same key (or keys).

Given: $P_1 = D_k(C_1), P_2 = D_k(C_2), \dots P_i = D_k(C_i)$
Deduce: Cipher $k$, or an algorithm to infer $P_{i+1}$ from $E_k(C_{i+1})$

- 3. **Chosen-plaintext attack**. The cryptanalyst not only has access to the ciphertext and plaintext for several messages, but he also chooses the plaintext that gets encrypted. This is more powerful than a known-plaintext attack, because the cryptanalyst can choose specific plaintext blocks to encrypt, ones that might yield more information about the key. His job is to deduce the key (or keys) used to encrypt the messages or an algorithm to decrypt any new messages encrypted with the same key (or keys).

Given: $P_1 = E_k(P_1), P_2 = E_k(P_2), \dots P_i = E_k(P_i)$, where the cryptanalyst chooses to choose $P_1, P_2, \dots P_i$
Deduce: Either $k$, or an algorithm to infer $P_{i+1}$ from $E_k(C_{i+1})$

- 4. **Adaptive-chosen-plaintext attack**. This is a special case of a chosen-plaintext attack. Not only can the cryptanalyst choose the plaintext that is encrypted, but he can also modify his choice based on the results of previous encryption. In a chosen-plaintext attack, a cryptanalyst might just be able to choose one large block of plaintext to be encrypted; in an adaptive-chosen-plaintext attack he can choose a smaller block of plaintext and then choose another based on the first, and so forth.

There are three other types of cryptanalytic attack.

- 5. **Chosen-ciphertext attack**. The cryptanalyst can choose different ciphertexts to be decrypted and has access to the decrypted plaintext. For example, the cryptanalyst has access to a tamperproof box that does automatic decryption. His job is to deduce the key.

Given: $C_1 = D_k(C_1), C_2 = D_k(C_2), \dots C_i = D_k(C_i)$
Deduce: $k$

This attack is primarily applicable to public-key algorithms and will be discussed in Section 19.3. A chosen-ciphertext attack is sometimes effective against a symmetric algorithm as well. (Sometimes a chosen-plaintext attack and a chosen-ciphertext attack are together known as a chosen-ciphertext attack.)

- 6. **Chosen-key attack**. This attack doesn't mean that the cryptanalyst can choose the key; it means he has some knowledge about the relationship between different keys. It's strange and obscure, not very practical, and discussed in Section 12.4.

- 7. **Rubber-hose cryptanalysis**. The cryptanalyst threatens, blackmails, or tortures someone until they give him the key. Bribery is sometimes referred to as a purchase-key attack. These are all very powerful attacks and often the best way to break an algorithm.

Known-plaintext chosen-plaintext attacks are more common than you think. It is not unheard of for a cryptanalyst to get a plaintext message that has been encrypted or bribe someone to encrypt a message. You may not even have to bribe someone; if you give a message to an ambassador, you probably find that it gets sent and back for consideration. Many messages have standard beginnings and endings that might be known to the cryptanalyst. Encrypted source code is especially vulnerable because of the regular appearance of keywords. Encrypted executable code has the same kinds of problems: loop structures, and so on. Known-plaintext attacks and even chosen-plaintext attacks were successfully used against the Germans and the Japanese during World War II. David Kahn's books [794,795,796] have historical examples of these kinds of attacks.

And don't forget Kerckhoffs' assumption: If the strength of your cryptography relies on the fact that the attacker does not know the algorithm's inner works, you're sunk. If you believe that keeping the algorithm's secrets more than letting the academic community analyze it, you're wrong. And if you think that someone won't disassemble your code and reverse-engineer your algorithm, you're naive. (In 1994 this was broken with the RC4 algorithm—Section 17.1). The best algorithms we have are the ones that have been made public, have been attacked by the world's best cryptographers for years, and are still unbreakable. The National Security Agency, de does not make a hit of telling Mossad about its cryptographic algorithms, but Mossad probably finds out. While real-world cryptanalysts don't always have such detailed information, it is a good assumption to make. If others can't break an algorithm, even with knowledge of how it works, they certainly won't be able to break it without knowledge.

- 1. **Ciphertext-only attack**. ... Deduce: Either $P_1, P_2, \dots P_k$ or an algorithm to infer $P_{i+1}$ from $E_k(C_{i+1})$ 

- 2. **Known-plaintext attack**. ... Deduce: Cipher $k$, or an algorithm to infer $P_{i+1}$ from $E_k(C_{i+1})$

- 3. **Chosen-plaintext attack**. ... Deduce: Either $k$, or an algorithm to infer $P_{i+1}$ from $E_k(C_{i+1})$

- 4. **Adaptive-chosen-plaintext attack**. ...

- 5. **Chosen-ciphertext attack**. ... Deduce: $k$

- 6. **Chosen-key attack**. ...

- 7. **Rubber-hose cryptanalysis**. ...

## Security of Algorithms

Different algorithms offer different degrees of security; if the cost required to break an algorithm is greater than the value of the data, you're probably safe. If the time required to break the encrypted data must remain secret, then you're probably safe. If the amount of data encrypted with a single key is less than the amount of data necessary to break the algorithm, then you're probably safe.

I say "probably" because there is always a chance of new breakthroughs in cryptography. On the other hand, the value of data decreases over time. It is important that the value of data always remains less than the cost to break it.

Lars Knudsen classified these different categories of breaking an algorithm. In decreasing order of severity [858]:

- 1. **Total break.** The cryptanalyst finds the key, K, such that $D_K(C) = P$.
- 2. **Global deduction.** The cryptanalyst finds an alternate algorithm, A, equivalent to $D_K(C)$, without knowing $K$.
- 3. **Instance (or local deduction)** The cryptanalyst finds the plaintext of an intercepted ciphertext.
- 4. **Information deduction.** The cryptanalyst gains some information about the key or plaintext. This information could be a few bits of the key, some information about the form of the plaintext, and so forth.

An algorithm is **unconditionally secure**, no matter how much a cryptanalyst finds, there is not enough information to recover the plaintext. In point of fact, only a one-time pad [see Section 1.5] is unbreakable infinite resources. All cryptosystems are breakable in ciphertext-only attack, simply by trying every possible key by one and checking whether the resulting plaintext is meaningful. This is a **brute-force attack** [see Section 7].

Cryptography is more concerned with cryptosystems that are computationally infeasible to break. An algorithm is considered **computationally secure** (sometimes called strong) if it cannot be broken with available resources, either current or future. Exactly what constitutes “available resources” is open to interpretation.

You can measure the complexity (see Section 11.1) of an attack in different ways:
