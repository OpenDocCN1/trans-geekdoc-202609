nonsecret public key. There is no need for prior secure key exchange as there is in symmetric key encryption.

# PADLOCK AND KEY ANALOGY

Public key encryption can be confusing when you read about it for the first time. Using a “padlock and key” analogy may help illustrate the interconnected relationship between the public and private keys.

Bob goes to a locksmith and orders a dozen padlocks (padlock = Bob’s public key) made with only one unique key (key = Bob’s private key) that will open all of the padlocks. Bob then gives the unlocked padlocks to Alice and keeps his unique key.

Alice can use Bob’s unlocked padlocks (Bob’s public key) to lock (encrypt) a message in a box. Even if the box were intercepted, it couldn’t be opened. Only Bob can open the locked box because he has the unique key (Bob’s private key). In fact, Bob can give his unlocked padlocks (Bob’s public key) to anyone he wants to communicate with. Only Bob can open the locked padlocks with his unique private key.

The process can be reversed if Bob wanted to send messages to Alice. Each would have their own padlocks (public keys) that they could freely give out. They would also have a unique key (private key) that they would keep secret and use it to unlock (decrypt) their own padlocks.

The padlock and key analogy is an intuitive way of understanding how public and private keys work to ensure confidentiality. This analogy will break down when we discuss using public keys for authentication (i.e., to create digital signatures) later in this chapter. However, for first-time readers, the analogy is useful in understanding the idea of how public and private keys work.

# HIGH COST AND SHORT MESSAGE LENGTHS

Symmetric key encryption is fast and inexpensive, but it requires the secure distribution of session keys. Public key encryption is the opposite. We have just seen that in public key encryption there is no need to distribute keys secretly before encryption for confidentiality. No prior keying is necessary. This is highly desirable.

However, public key encryption ciphers are extremely complex and therefore slow and expensive to use. (Typically, public key encryption takes 100 to 1,000 times longer than symmetric key encryption to encrypt a message of a given length.) Consequently, cryptography only uses public key encryption to encrypt very short messages for confidentiality.

# RSA AND ECC

There are only two widely used public key encryption ciphers. The first is the RSA cipher, which dominates public key encryption. The more efficient elliptic curve cryptography (ECC) public key cipher saw moderate use but is being phased out due to weaknesses from quantum computing. We will discuss the implications of quantum computing later in this chapter.

# KEY LENGTH

While symmetric key encryption relies on briefly used session keys, public–private key pairs are rarely changed. For instance, to be able to receive encrypted messages, the receiver needs to protect a private key for weeks, months, or even years. As the duration of key use increases, so does traffic volume, and so must key length for a given degree of security.

While session keys of 112 bits are strong in symmetric key encryption, public keys need to be far longer. For RSA public key encryption, a recommended minimum key length for a strong key is 1,024 bits. Longer key length requires more