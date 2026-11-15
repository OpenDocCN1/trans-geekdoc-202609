# # 15 Public-Key Encryption

So far, the encryption schemes that we’ve seen are **symmetric-key** schemes. The same key is used to encrypt and decrypt. In this chapter we introduce **public-key** (sometimes called *asymmetric*) encryption schemes, which use different keys for encryption and decryption. The idea is that the encryption key can be made *public*, so that anyone can send an encryption to the owner of that key, even if the two users have never spoken before and have no shared secrets. The decryption key is private, so that only the designated owner can decrypt.

We modify the syntax of an encryption scheme in the following way. A public-key encryption scheme consists of the following three algorithms:

KeyGen: Outputs a *pair* $(pk, sk)$ where $pk$ is a public key and $sk$ is a private/secret key.

Enc: Takes the public key $pk$ and a plaintext $m$ as input, and outputs a ciphertext $c$.

Dec: Takes the secret key $sk$ and a ciphertext $c$ as input, and outputs a plaintext $m$.

We modify the correctness condition similarly. A public-key encryption scheme satisfies *correctness* if, for all $m \in \mathcal{M}$ and all $(pk, sk) \leftarrow \mathsf{KeyGen}$, we have $\mathsf{Dec}(sk, \mathsf{Enc}(pk, m)) = m$ (with probability 1 over the randomness of Enc).

# ## 15.1 Security Definitions

We now modify the definition of CPA security to fit the setting of public-key encryption. As before, the adversary calls a CHALLENGE subroutine with two plaintexts — the difference between the two libraries is which plaintext is actually encrypted. Of course, the encryption operation now takes the public key.

Then the biggest change is that we would like to make the public key *public*. In other words, the calling program should have a way to learn the public key (otherwise the library cannot model a situation where the public key is known to the adversary). To do this, we simply add another subroutine that returns the public key.

Definition 15.1 Let $\Sigma$ be a public-key encryption scheme. Then $\Sigma$ is **secure against chosen-plaintext at-**