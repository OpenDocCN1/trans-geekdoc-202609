# Security Goals

I’ve informally defined the goal of security as “nothing can be learned about the cipher’s behavior.” To turn this idea into a rigorous mathematical definition, cryptographers define two security goals that correspond to different ideas of what it means to learn about a cipher’s behavior:

Indistinguishability (IND) Ciphertexts should be indistinguishable from random strings. This is usually illustrated with a hypothetical game: if an attacker picks two plaintexts and then receives a ciphertext of one of the two (chosen at random), they shouldn’t be able to tell which plaintext was encrypted, even by performing encryption queries with the two plaintexts (and decryption queries, if the model is CCA rather than CPA).

Nonmalleability (NM) Given a ciphertext C₁ = E(K, P₁), it should be impossible to create another ciphertext, C₂, whose corresponding plaintext, P₂, is related to P₁ in a meaningful way (for example, to create a P₂ that is equal to P₁ ⊕ 1 or to P₁ ⊕ X for some known value, X). Surprisingly, the one-time pad is malleable: given a ciphertext C₁ = P₁ ⊕ K, you can define C₂ = C₁ ⊕ 1, which is a valid ciphertext of P₂ = P₁ ⊕ 1 under the same key K. Oops, so much for our perfect cipher.

Next, I’ll discuss these security goals in the context of different attack models.

# Security Notions

Security goals are useful only when combined with an attack model. The convention is to write a security notion as GOAL-MODEL. For example, IND-CPA denotes indistinguishability against chosen-plaintext attackers, NM-CCA denotes nonmalleability against chosen-ciphertext attackers, and so on. Let’s start with the security goals for an attacker.

# Semantic Security and Randomized Encryption: IND-CPA

The most important security notion is IND-CPA, also called semantic security. It captures the intuition that ciphertexts shouldn’t leak any information about plaintexts as long as the key is secret. To achieve IND-CPA security, encryption must return different ciphertexts if called twice on the same plaintext; otherwise, an attacker could identify duplicate plaintexts from their ciphertexts, contradicting the definition that ciphertexts shouldn’t reveal any information. But note that even the IND-CPA-secure scheme will inevitably leak one piece of information about the plaintext: its length, or at least approximate length. This is why encrypting compressed data is generally not a good idea, as the size of the compressed data can reveal information on the original data.

One way to achieve IND-CPA security is to use randomized encryption. As the name suggests, it randomizes the encryption process and returns different ciphertexts when the same plaintext is encrypted twice. Encryption