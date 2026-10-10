
One of the major issues with some encryption technologies, such as many symmetric encryption algorithms, is the fact that they only do encryption and decryption of the data and do not authenticate the request to do the encryption or decryption (this is known as *unauthenticated encryption*). This can lead to weaknesses in the encryption scheme, and it allows an attacker to intercept a cipher text message and modify it, which essentially will change the plain text value after the data is decrypted by the receiver. As a fix, you can use *authenticated encryption* protocols, which provide authenticity and integrity to the encrypted data. For example, you could use *Message Authentication Code (MAC),* which is a cryptographic checksum value that is based off the encrypted data and can be used to detect if the encrypted data has changed.

### Padding

When data is encrypted, plain text messages usually do not take up an even number of blocks. Many times *padding* must be added to the last block to complete the data stream.

The data added can contain all 1’s, all 0’s, or a combination of 1’s and 0’s. The encryption algorithm used is responsible for determining the padding that will be applied. Various padding techniques are available, depending on the algorithm implementation.

### XOR

An exclusive OR (XOR) is a mathematical operation that is common in cryptography. With an XOR operation, if one, and only one, of two bits being compared has a value of 1, then the result is a 1 for that calculated bit. But if both of the bits being compared have a value of 1, or neither has a value of 1, then the answer for that resulting bit is a 0.

The following summarizes the formula for XOR functions when two bits are being XORed against one another:

![Images](p0521-01.jpg)

For encryption, the plain text is XORed with the key to create the cipher text. Consider the following example:

![Images](p0521-02.jpg)

After the plain text is encrypted to create the cipher text, the principle behind the XOR function is that you can decrypt the information by XORing the cipher text against the key again:

![Images](p0521-03.jpg)

Now that you understand the basic cryptography terminology, let’s take a look at the different types of encryption.

![Image](exam.jpg)

**For the Security+ exam, be familiar with the terms *work factor, onetime pad (OTP)*, and *exclusive OR (XOR)*.**

### Salt, IV, and Nonce

Most encryption implementations use a key, but many also use salt values, initialization vectors, and nonce values to strengthen the encryption or hashing function.

A *salt* is a random value that is generated and combined with the data before the data is hashed. This is a technique known as *salting* and is used to ensure that the same data input (typically a password) will generate different hash values when the password hashes are generated.

Similar in concept to a salt, an *initialization vector,* or *IV,* is a random value generated that is used with the encryption key to encrypt data. The purpose of joining the IV with the key is to ensure that if a hacker were to gain access to the encrypted data, they could not compare different parts of the encrypted data to try to determine the key value. The IV is giving randomness to each segment of data that is encrypted with the same key.

A *nonce* is a randomly generated number that is only used once and is typically applied to authentication traffic. The typical scenario for a nonce is at the beginning of the authentication process. The client sends a request to the server for a nonce value. The server sends a random number to the client, which then uses that number to hash the password (with a hashing algorithm) and sends the hashed authentication information across the network to the server. A nonce can also be used with encryption as a way to ensure that the key stream is unique with each message sent. In this case, the encryption key + nonce value would be used to encrypt data sent (the message). Since each message will use a unique nonce, each message is technically encrypted with a different key.

### Weak/Deprecated Algorithms

While we are on the topic of algorithms, I want to stress a point about working with different encryption algorithms. Always ensure that you are selecting the most secure algorithm to get the job done. Do some research and be aware of which algorithms are weaker than others and have been deprecated (no longer recommended for use). For example, 3DES was a popular symmetric encryption algorithm for many years but has been replaced by AES.

### Diffusion, Confusion, and Obfuscation

Cryptography is all about keeping things secret, and three principles that strong ciphers follow to ensure secrecy are confusion, diffusion, and obfuscation.

*Confusion* is the principle of ensuring that the relationship between the encryption key and the data after it is encrypted is as complex as possible so it is difficult to figure out. Substitution is an example of a cryptography feature that implements confusion.

*Diffusion* is ensuring that the repeating of characters in the plain text will not help someone decipher the cipher text (data after it is encrypted). Transposition is a feature that provides diffusion.

*Obfuscation* is the concept of making something complicated on purpose to make it difficult to understand. For example, in order to hide the details of the cryptographic implementation of a product, you could make sure that the documentation for that product is hard to understand.

### Random/Pseudo-Random Number Generation

As referenced a bit earlier in the chapter, random number generation or pseudo-random number generation is used by algorithms to ensure that multiple streams of data encrypted or hashed with the same key do not create the same cipher text or hash value. With encryption, the random number is appended to the key before encryption, while with hashing, the random value is appended to the data before it is hashed.

### Implementation vs. Algorithm Selection

In implementations of cryptography solutions, the *crypto service provider (CSP)* is the library of code that provides the functions to encrypt and decrypt data. The crypto service provider offers the different encryption and hashing algorithms that can be used within the software.

Software applications can implement different cryptography features by loading *crypto modules,* which are software, hardware, or firmware components added to a system to provide cryptography functions such as encryption, decryption, hashing, and authentication.

When looking at implementing cryptographic solutions, be sure to select the encryption and hashing algorithms that are of the highest strength and that have been proven over time.

### Blockchain

*Blockchain* is a common term we hear today due to cryptocurrency. Blockchain is a database, or listing, of transactions that are stored in a table or ledger format. Blockchain is used to track assets such as money. Blockchain gets its name because the data is stored in blocks, where each block is linked to the previous block.

Blockchain uses a public ledger system, which keeps track of transactions yet keeps the individual’s identity secure and anonymous. The transactions in the public ledgers of the chain have a relationship, in that each block that holds the transactions contains the hash of the previous block of transactions. This means that once a block (and its contained transactions) is recorded, it cannot be changed, as the chain would be broken. The public ledger is used so that there are multiple copies of the ledger across the Internet, with the transactions being validated by people who are mining the data. Note that the action of mining is the act of validating a section of the chain.

## CERTIFICATION OBJECTIVE 12.02

## Symmetric Encryption
