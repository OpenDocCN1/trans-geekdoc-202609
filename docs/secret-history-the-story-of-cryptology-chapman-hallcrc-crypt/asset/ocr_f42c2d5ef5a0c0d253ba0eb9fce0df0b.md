# 15.1.8 Attack 8. Searching the Message Space

If the sender is in the habit of sending one of a small number of stereotyped messages, a cryptanalyst can simply encrypt each and see which one matches the intercepted ciphertext.

**PATCH:** Make sure the potential message space is large! Or, as in the alternative patch for Attack 7, pad the messages with random bits. This way, if only a small set of messages will typically be sent, repeats can be padded differently to create too many possibilities to check in the manner of the attack described above. For example, if the attacker guesses the message might be “Nothing to report,” but 50 bits of padding have been used, he’d have to encipher all 2⁵⁰ different versions of “Nothing to report,” before being able to decide if that was or was not the actual message. One standard for padding put out by RSA is PKCS #1. It stands for Public Key Cryptography Standard #1. This standard is now at version 2.2, as modifications were demanded by attacks (such as the adaptive chosen ciphertext attack) found against earlier versions.

# 15.1.9 Attack 9. Adaptive Chosen Ciphertext Attacks

![](bbox=[0.367, 0.398, 0.633, 0.618])

**Figure 15.2**  Daniel Bleichenbacher (1964–). *(Courtesy of Daniel Bleichenbacher and Kit August.)*

A chosen ciphertext attack is one in which the attacker gets to create any ciphertext he likes and then get the corresponding plaintext. Adding the adjective “adaptive” means that he can do this repeatedly, using knowledge he gained in previous iterations to adapt his next ciphertext in such a way as to optimize the information it yields. This is the sort of attack Daniel Bleichenbacher (Figure 15.2) launched against RSA padded in accordance with PKCS #1. Actually, his attack was a bit less demanding in that he didn’t need the corresponding plaintexts, but rather just the knowledge of whether or not these plaintexts corresponded to some block of data encrypted using PKCS #1. Describing his attack, he wrote, “we expect that the attack needs roughly 2²⁰ chosen ciphertexts to succeed.”¹¹ This sounds daunting, but Bleichenbacher points out that the attack is practical, because there are servers that will accept ciphertexts and return error messages when

> ¹¹ Bleichenbacher, Daniel, “Chosen Ciphertext Attacks against Protocols Based on the RSA Encryption Standard PKCS #1,” in Krawczyk, Hugo, editor, Advances in Cryptology – *CRYPTO ’98 Proceedings*, Lecture Notes in Computer Science, Vol. 1462, Springer, Berlin, Germany, 1998, pp. 1–12.