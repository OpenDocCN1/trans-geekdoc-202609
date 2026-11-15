# Discussion

**So if I use a CCA-secure encryption scheme, I should never decrypt a ciphertext that I I encrypted myself?**

Remember: when we define the Enc and Dec algorithms of an encryption scheme, we are describing things from the normal user's perspective. As a user of an encryption scheme, you can encrypt and decrypt whatever you like. It would indeed be strange if you encrypted something knowing that it should never be decrypted. What's the point?

The security definition describes things from the *attacker's* perspective. The $\mathcal{L}_{\text{cca-}\star}$ libraries tell us *what are the circumstances under which the encryption scheme provides security*? They say (roughly):

> an attacker can't tell what's inside a ciphertext $c^*$, even if she has some partial information about that plaintext, even if she had some partial *influence* over the choice of that plaintext, and even if she is *allowed to decrypt any other ciphertext* she wants.

Of course, if a real-world system allows an attacker to learn the result of decrypting $c^*$, then by definition the attacker learns what's inside that ciphertext.

CCA security is deeply connected with the concept of **malleability**. Malleability means that, given a ciphertext that encrypts an unknown plaintext $m$, it is possible to generate a different ciphertext that encrypts a plaintext that is *related* to $m$ in a predictable way. For example:

+   - If $c_0||c_1||c_2$ is a CBC encryption of $m_1||m_2$, then $c_0||c_1$ is a CBC encryption of $m_1$.\n- If $c_0||c_1||c_2$ is a CBC encryption of $m_1||m_2$, then $c_0||c_1||c_2||0^{blen}$ is a CBC encryption of *some plaintext that begins with* $m_1||m_2$.\n- If $c_0||c_1$ is a CBC encryption of $m_1$, then $(c_0 \oplus x)||c_1$ is a CBC encryption of $m_1 \oplus x$.

Note from the second example that we don't need to know *exactly* the relationship between the old and new ciphertexts.

If an encryption scheme is malleable, then a typical attack against its CCA security would work as follows:

+   1. Request an encryption $c$ of some plaintext.\n2. Applying the malleability of the scheme, modify $c$ to some other ciphertext $c'$.\n3. Ask for $c'$ to be decrypted.

Since $c' \neq c$, the security library allows $c'$ to be decrypted. The malleability of the scheme says that the contents of $c'$ should be related to the contents of $c$. In other words, seeing the contents of $c'$ should allow the attacker to determine what was initially encrypted in $c$.