
## CHAPTER 2 Protocol Building Blocks

- (2) Bob sends Alice his public key.
- (3) Alice encrypts her message using Bob's public key and sends it to Bob.
- (4) Bob decrypts Alice's message using his private key.

How public-key cryptography solves the key-management problem with symmetric cryptosystems. Before, Alice and Bob had to agree on a key in secret. Alice could choose one at random, but still had to get to Bob. She could hand it to him beforehand, but that requires foresight. She could send it by secure courier, but that takes time. Public-key cryptography makes it easy. With no prior arrangements, Alice can send a secure message to Bob. Eve, listening on the entire exchange, has Bob's public key and message encrypted in that key, but cannot recover Bob's private key or the message.

More, a network of users agrees on a public-key cryptosystem. Every user has his or her public key and private key, and the public keys are all published in a database somewhere. Now the protocol is even easier:

- (1) Alice gets Bob's public key from the database.
- (2) Alice encrypts her message using Bob's public key and sends it to Bob.
- (3) Bob decrypts Alice's message using his private key.

In the first protocol, Bob had to send Alice his public key before she could send him a message. The second protocol is more like traditional. Bob is not involved in the protocol until he wants to read his message.

## Hybrid Cryptosystems

The first public-key algorithms became public at the same time as DES was being presented as a proposed standard. This resulted in some partisan policies in the cryptographic community. As Diff described it [494]:

The excellent public-key cryptosystems provoked in the public and scientific press was not matched by corresponding acceptance in the cryptographic establishment. In the year that public key cryptography was discovered, the National Security Agency (NSA), proposed a conventional cryptosystem, designed by International Business Machines [IBM], as a Federal Encryption Standard [DES]. Marty Hellman and I criticized the proposal on the ground that it was too small, but manufacturers were gearing up to support the standards-making process and our criticism was seen by many as an attempt to disrupt the advantage of our work. Public cryptography in turn was attacked, in sales literature [125] and technical papers [849,1159], as though it were competing from a recent research discovery. This, however, did not deter the NSA from claiming its share of the credit. Its director, in the words of the Encyclopedia Britannica [1461], pointed out that “two-key cryptography had been discovered at the agency decade earlier,” although no evidence for this claim was offered publicly.

## 2.5 Communications Using Public-Key Cryptography

In the real world, public-key algorithms are not a substitute for symmetric algorithms. They are not used to encrypt messages; they are used to encrypt keys. There are two reasons for this:

1. Public-key algorithms are slow. Symmetric algorithms are generally a thousand times faster than public-key algorithms. Computers are getting faster and faster, and in 15 years computers will be able to do public-key cryptography at speeds comparable to symmetric cryptography today. Bandwidth requirements are also increasing, and there will always be the need to encrypt data faster than public-key cryptography can manage.
2. Public-key cryptosystems are vulnerable to chosen-plaintext attacks. If $C=E[P]$, where $P$ is a plaintext out of a set of $n$ possible plaintexts, a cryptanalyst can only encrypt all $n$ possible plaintexts and compare the results with $C$ (remember, the encryption is public). He will not be able to recover the decryption key, but will be able to determine $P$.

A chosen-plaintext attack can be particularly effective if $P$ were a dollar amount less than $1,000,000, this attack would work; the cryptanalyst tries million possible dollar amounts. (Probabilistic encryption solves the problem; see Section 23.15.) Even if $P$ is not well-defined, this attack can be very effective. Simply knowing that a ciphertext does not correspond to a particular plaintext can be useful information. Symmetric cryptystems are not vulnerable to this attack because a cryptanalyst cannot perform trial encryptions with an unknown key.

In most practical implementations public-key cryptography is used to secure and distribute **session keys**, those keys are used with symmetric algorithms to secure message traffic [879]. This is sometimes called a **hybrid cryptosystem**.

- (1) Bob uses his public key.
- (2) Alice generates a random session key, $K$, it encrypts it using Bob's public key and sends it to Bob.
- (3) Bob decrypts Alice's message using his private key to recover the session key.
- (4) Both of them encrypt their communications using the same key.

Using public-key cryptography for key distribution solves a very important problem. With symmetric cryptography, the key stays around until it is used. With the previous protocol, session key is created when it is needed and destroyed when it is no longer needed. This drastically reduces the risk of compromising it.

## Merkle's Puzzles

Ralph Merkle invented the first construction of public-key cryptography. In 1974 he registered for a course in computer security at the University of California, Berkeley, by Lance Hoffman. His term paper topic, submitted early in the term, addressed "Secure Communication over Insecure Channels" [1064]. Merkle could not understand Merkle's proposal and eventually dropped the course. He continued to work on the problem, despite continuing failure to make his results understood.

Merkle's technique was based on "puzzles" that were easier to solve for the receiver and sender for an eavesdropper. Here's how Alice sends an encrypted message to Bob without first exchanging a key with him.

- (1) Bob generates $2^{20}$, or about a million, messages of the form: "This is puzzle x. This is the secret key y," where x is a random number and y is a secret key. Both x and y are different for each number. Using a symmetric algorithm, he encrypts each message with a different 20-bit key and sends them all to Alice.
- (2) Alice chooses one message at random and performs a brute-force attack to recover the plaintext. This is a large, not impossible, amount of work.
- (3) Alice encrypts her secret message with the key she recovered and some symmetric algorithm, and sends it to Bob along with x.
- (4) Bob knows which secret y he encrypted in message x, so he can decrypt the message.

Eve can break this, but she has to do far more work than either Alice or Bob. To recover the message in step [3], she has perform a brute-force attack against Bob's $2^{20}$ messages in step [1]; this attack has the complexity of $2^{20}$. The x values do not help Eve, either they were selected randomly in step [1]. In general, Eve has to expend approximately the square of the effort that Alice spends.

This to $n$ advantage is small by cryptographic standards, but in some circumstances may be enough. If Alice and Bob can take thousand keys per second, it will take them a minute each to perform their steps and another minute to communicate the puzzles from Bob to Alice on a 1.544 MB link. If Eve had comparable facilities, it would take her about a year to break the system.

## 2.6 DIGITAL SIGNATURES

Handwritten signatures have long been used as proof of authorship of, or at least agreement with the contents of a document. What is it a signature that is so compelling [1392]?
