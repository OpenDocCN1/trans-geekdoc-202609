
one and only one of the inputs is true. The exclusive OR function, represented as $\oplus$, has the following properties:

- 0 $\oplus$ 0 = 0
- 0 $\oplus$ 1 = 1
- 1 $\oplus$ 0 = 1
- 1 $\oplus$ 1 = 0

Note that this is equivalent to the $\neq$ (not-equal) function. Using this approach, you can combine a binary stream of data with a binary keystream (stream of characters from a key) to produce ciphertext. This is how hardware or software uses modern substitution ciphers.

## Product and Exponentiation Ciphers

A product cipher is a combination of multiple ciphers. Each could be a transposition or substitution cipher. The Data Encryption Standard (DES) is a product cipher with a 56-bit key consisting of 16 iterations of substitution and transformation. First published as a Federal Information Processing Standard (FIPS) in 1977, DES is still in use. Its developers thought it was highly secure because the computers available in 1977 would take more than 90 years to break an encrypted message. Many civil libertarians and conspiracy theorists as well as professional cryptographers think designers built certain weaknesses into DES to let the National Security Agency (NSA) open a backdoor in the algorithm to decrypt messages easily. However, after more than 25 years, no one has found such a weakness. Advances in cryptography—including differential cryptanalysis, which involves looking for patterns in vast amounts of ciphertext—actually imply that the DES design was even more secure than vast suspected. Nonetheless, advances in computing power have made the 56-bit keyspace (72,057,594,037,927,900 keys) less daunting to search. Finally, in 1998, the Electronic Frontier Foundation built a special-purpose computer called Deep Crack, which can search the keyspace in less than three days. You'll read about DES in more detail later in this chapter.

Some ciphers rely on the difficulty of solving certain mathematical problems. This is the basis for asymmetric key cryptography. These ciphers use a branch of mathematics known as field theory. Without getting into too much mathematics, a field is any domain of numbers in which every element other than 0 has a multiplicative inverse. For example, all rational numbers form a field. Given x ≠ 0, you can always compute 1/x. Fields do not have to be infinite. Instead of counting to infinity, you can restart counting after reaching a particular value. For example, in the United States, people tell time with a 12-hour clock. One hour past 10:00 is 11:00, but one hour past 12:00 is 1:00, not 13:00. Many countries use a 24-hour clock, but the wraparound effect is the same. Things get interesting mathematically when the number of integers in a set is prime. The set of integers from 1 to a prime number represents a finite field.

An exponentiation cipher involves computing exponentials over a finite mathematical field. The Rivest-Shamir-Adleman (RSA) encryption scheme relies on the difficulty of factoring large numbers. It's straightforward to multiply two numbers together, but it's very difficult to factor one large number. You'll learn the details of this process later in this chapter.

## Symmetric and Asymmetric Key Cryptography

In this section, you'll learn more about the differences between symmetric and asymmetric key cryptography and the relative advantages and disadvantages of both.

### Symmetric Key Ciphers

Symmetric key ciphers use the same key to encrypt and decrypt. As a result, they require that both parties first exchange keys to communicate. This represents a basic limitation for these cryptosystems. Before you can send a message to another party, you must first talk securely to exchange keys. This chicken-and-egg problem is what made cryptography difficult in the past for any large, dispersed organization, with the exception of governments, the military, and well-funded people.

To illustrate this problem, imagine that two correspondents, Alice and Bob, want to exchange information securely. In this scenario, Alice and Bob work for the ABC Company. They want to exchange pricing information for a proposal to a new client, MNO Plastics. Bob is in the field at the client site and cannot get to the company's internal network. All information must go back and forth across the Internet.

Eva works for an overseas competitor of ABC. Her job is to gather as much intelligence as she can about ABC's proposal and bid. She has authorization to monitor, disrupt, or masquerade any communications to achieve her mission. The obvious legal issues here can be set aside for the sake of discussion. Assume that Eva can monitor all communications to and from Bob. Any messages he sends or receives pass through a node Eva controls.

Here's the problem: How do Alice and Bob create a secure communications session if they have not agreed on anything in advance? Let's say that Alice and Bob agree to use DES to encrypt their information. Because DES is a publicly available algorithm, Eva can download a copy of DES software. Alice sends a message to Bob to use BIGBUCKS as the key. Bob acknowledges this convention and sends his encrypted message to Alice using this key. Eva, listening in on the communications, uses the same key to decrypt Bob's message and sends his information to her company.

Alice and Bob can agree to change keys any number of times, but each time they do, Eva learns of this key change and adjusts accordingly. Using symmetric key cryptography, there is no way around this problem. Each party must exchange keys with the other party to know what key the other is using. Even if you encrypt a key with a special-purpose key or a key-encrypting key, you must exchange the key-encrypting key at some point. Key-encrypting keys are keys that you use only to encrypt other keys. Exchanging key-encrypting keys means that an attacker can intercept the key-encrypting key when you exchange it.

The solution to this dilemma requires a message that travels on a different path that Eva can't monitor. This is out-of-band communication using a secure channel. Let's say in this case that Alice and Bob agree to use DES, and Alice tells Bob to call her on his cell phone and tell her what key to he wants to use. Eva, who can read all Internet traffic, can't monitor cell phones. Alice and Bob agree on a 56-bit key and begin exchanging information. Eva is out of the loop. Of course, before Bob left on the business trip, Alice and Bob could have agreed to use a particular key. This, too, is out-of-band communication. It takes place outside the communications channel used for sending and receiving messages.

Now ABC Company has a choice to make. It can issue the same key to all employees, which makes correspondence easy. Any employee can correspond securely with any other employee around the world. This model works well until a disgruntled employee quits and joins a competitor, taking the key with him. Now what? ABC has to create a new key and re-issue the new key to everyone worldwide. This could be time-consuming and expensive.

Alternatively, ABC could decide that a single point of failure is unacceptable and issue separate keys to each employee. However, because both parties have to use the same key with symmetric key ciphers, each employee-employee pair must have its own unique key. Thus, if there were 10 employees, ABC would need 45 key pairs (9 + 8 + 7 + 6 + 5 + 4 + 3 + 2 + 1) to begin this scheme. If ABC had 100 employees, it would need 4,950 key pairs. If ABC had 10,000 employees, it would need 49,995,000 key pairs! The number of key pairs required for n correspondents is (n (n - 1)) / 2. Moreover, each time an employee joined or left the company, you would have to add or delete a key pair for each of the other employees.

Clearly, symmetric key systems do not scale well. This remained an intractable problem for cryptologists (and governments, militaries, and businesses) until 1976, when Whitfield Diffie and Martin Hellman published their paper, “New Directions in Cryptography,” in the IEEE Transactions on Information Theory journal. In this paper, they proposed a radical new approach that offered a potential solution to the scalability problem.

### Asymmetric Key Ciphers

In their introduction, Diffie and Hellman pointed out, “The cost and delay imposed by this key distribution problem is a major barrier to the transfer of business communications to large teleprocessing networks.” They introduced the concept of public key cryptography. (Note that this text refers to this concept as asymmetric key cryptography.) Public key cryptography is a system that allows correspondents to communicate only over a public channel using publicly known techniques. They can create a secure connection. They do not need to wait until an out-of-band letter arrives with a key in the envelope. Nor do they need to issue and manage millions of key pairs just in case someone wants to communicate securely with a new correspondent. The impact of this discovery is profound and has far-reaching effects on cryptography.

Asymmetric key ciphers have four key properties:

- Two associated algorithms that are inverses of each other exist—This solution involves two components associated with each other. That means you use one algorithm to encrypt and another to decrypt.
- Each of these two algorithms is easy to compute—You can use this approach in computer software without much difficulty. As a result, it becomes a practical approach for secure digital communications.
- It is computationally infeasible to derive the second algorithm if you know the first algorithm—You can post one key widely for anyone to use without compromising the contents of its associated key. These are pairs of a public key and its associated private key, or a public-private key pair. Since public key cryptosystems have private keys, you can see why this chapter has stuck to the asymmetric key-naming convention!
