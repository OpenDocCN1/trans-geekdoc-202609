# 2.5 Communications Using Public-Key Cryptography 33

In the real world, public-key algorithms are not a substitute for symmetric algorithms. They are not used to encrypt messages; they are used to encrypt keys. There are two reasons for this:

+   1. Public-key algorithms are slow. Symmetric algorithms are generally a thousand times faster than public-key algorithms. Computers are getting faster and faster, and in 15 years computers will be able to do public-key cryptography at speeds comparable to symmetric cryptography today. Bandwidth requirements are also increasing, and there will always be the need to encrypt data faster than public-key cryptography can manage.
2. Public-key cryptystems are vulnerable to chosen-plaintext attacks. If $C=E[P]$, where $P$ is a plaintext out of a set of $n$ possible plaintexts, a cryptanalyst can only encrypt all $n$ possible plaintexts and compare the results with $C$ (remember, the encryption is public). He will not be able to recover the decryption key, but will be able to determine $P$.

A chosen-plaintext attack can be particularly effective if $P$ were a dollar amount less than $1,000,000, this attack would work; the cryptanalyst tries million possible dollar amounts. (Probabilistic encryption solves the problem; see Section 23.15.) Even if $P$ is not well-defined, this attack can be very effective. Simply knowing that a ciphertext does not correspond to a particular plaintext can be useful information. Symmetric cryptystems are not vulnerable to this attack because a cryptanalyst cannot perform trial encryptions with an unknown key.

In most practical implementations public-key cryptography is used to secure and distribute **session keys**, those keys are used with symmetric algorithms to secure message traffic [879]. This is sometimes called a **hybrid cryptosystem**.

+   (1) Bob uses his public key.
(2) Alice generates a random session key, $K$, it encrypts it using Bob's public key, and sends it to Bob.
$E_B[K]
(3) Bob decrypts Alice's message using his private key to recover the session key.
$D_B(E_B[K]) = K
(4) Both of them encrypt their communications using the same session key.

Using public-key cryptography for key distribution solves a very important management problem. With symmetric cryptography, the data encryption key stays around until it is used. If Eve ever gets hands on it, she can decrypt messages encrypted with it. With the previous protocol, the session key is created when it is needed to encrypt communications and destroyed when it is no longer needed. drastically reduces the risk of compromising the session key. Of course, the private