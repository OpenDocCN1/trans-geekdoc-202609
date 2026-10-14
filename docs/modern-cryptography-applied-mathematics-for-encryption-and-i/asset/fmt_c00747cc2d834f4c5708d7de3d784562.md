
The most practical use of quantum cryptography, and the one most likely to be implemented in the foreseeable future, is `quantum key distribution`. The issue of key distribution is at the heart of many algorithms such as Diffie-Hellman and Menezes–Qu–Vanstone, or MQV (recall both algorithms were discussed in [Chapter 10](#part0020.xhtml#ch10)). How do two parties exchange a key in such a way that a third party cannot intercept it? If the key is encoded as quantum bits, then the Heisenberg uncertainty principle provides security for key transmission. Any attempt to read the key will in fact alter the key.^([7](#part0030.xhtml#ch19note7a))

It is also possible to use quantum entanglement for key exchange. If a set of particles is entangled and then separated, the party on one end can encode bits as properties (such as spin) on the particles. By changing the property on the sender’s side, the bits of the key are instantly transmitted to the receiving side. Because there is no known communication medium, it is impossible for someone to intercept the key transmission.

##### Breaking Quantum Code

Quantum computing is still in a nascent stage, a very long way from practical implementation. But the possibilities could radically change cryptography. Current digital computers maintain data in states of bits, a 1 or 0. A quantum computer maintains data in qubits. These qubits can use a 1, a 0, or a superposition of these states. This allows quantum computers to store much more data and to process data much faster.

What this means in practical terms is that a quantum computer would have immensely more computational power than any digital computer. Consider the asymmetric algorithms you’ve studied in this book. They were all based on some problem being infeasible to solve, such as factoring a composite number into its prime factors (as seen in RSA), or solving a discrete logarithm problem (as in elliptic curve cryptography). If quantum computers become a practical reality, these problems will no longer be impractical to solve. In fact, they will be solvable in a reasonably short period of time, thus undermining the basis for all asymmetric algorithms.

Symmetric cryptography will not be safe from the onslaught of quantum computing either. Consider that keys such as the AES 256-bit key are essentially immune from brute-force attacks using current methods; a quantum computer could try far more keys in a shorter period of time, making brute-force attacks far more practical.

Currently there are no working quantum computers, so these issues are only hypothetical at this point. But given the attention and resources committed to quantum computing, it seems likely that we will eventually face these problems. Right now, the only solution is to use much larger keys, but this is only a stopgap solution, not a permanent one. Quantum computing will require an entirely new approach to cryptography—one that has not yet been developed.

#### Conclusions

Cryptography is evolving, and new issues are on the horizon. Currently one of the more immediate issues in cryptography is that of homomorphic encryption, which allows an entity to perform operations on encrypted data without first decrypting the data, and indeed without even having the capability to decrypt the data. Homomorphic encryption has applications in electronic voting, e-commerce, and cloud computing. Cloud computing itself poses cryptographic challenges, and homomorphic cryptography is one of the primary solutions to those challenges.

Quantum mechanics has not only revolutionized physics, but it could revolutionize computing and cryptography as well. Quantum key exchanges is perhaps the most immediate issue in cryptography and could solve secure key exchange issues. Code-breaking could also be enhanced dramatically by quantum computing.

#### Test Your Knowledge

    **[1](#part0030.xhtml#ch19qu1).**  \_\_\_\_\_\_\_\_\_\_ is a mechanism whereby the user can get proof that the vendor has not tampered with the data.

    **[2](#part0030.xhtml#ch19qu2).**  Briefly describe homomorphic encryption.

    **[3](#part0030.xhtml#ch19qu3).**  Who invented the first plausible construction for a fully homomorphic encryption scheme?

    **[4](#part0030.xhtml#ch19qu4).**  \_\_\_\_\_\_\_\_\_\_\_\_ was the first probabilistic public key algorithm that is provably secure.

    **[5](#part0030.xhtml#ch19qu5).**  What is the most widely known homomorphic system?

    **[6](#part0030.xhtml#ch19qu6).**  What is (currently) the most practical application of quantum mechanics to cryptography?

    **[7](#part0030.xhtml#ch19qu7).**  What property of quantum mechanics makes it impossible to tamper with a key being transmitted with quantum bits?

##### Answers

    **[1](#part0030.xhtml#ch19qu1a).**  Proof of storage

    **[2](#part0030.xhtml#ch19qu2a).**  Homomorphic encryption allows an entity to carry out computations on cipher text, without first decrypting the message.

    **[3](#part0030.xhtml#ch19qu3a).**  Craig Gentry

    **[4](#part0030.xhtml#ch19qu4a).**  Goldwasser–Micali

    **[5](#part0030.xhtml#ch19qu5a).**  Paillier system

    **[6](#part0030.xhtml#ch19qu6a).**  Quantum key distribution

    **[7](#part0030.xhtml#ch19qu7a).**  The Heisenberg uncertainty principle

#### Endnotes

    **[1](#part0030.xhtml#ch19note1).**  “Cloud Security & Cryptography,” [http://research.microsoft.com/en-us/projects/cryptocloud/](http://research.microsoft.com/en-us/projects/cryptocloud/).

    **[2](#part0030.xhtml#ch19note2).**  A. Greenberg, “Hacker Lexicon: What is Homomorphic Encryption?” *Wired*, 2014, [www.wired.com/2014/11/hacker-lexicon-homomorphic-encryption/](http://www.wired.com/2014/11/hacker-lexicon-homomorphic-encryption/).

    **[3](#part0030.xhtml#ch19note3).**  E. Naone, “Homomorphic Encryption: Making Cloud Computing More Secure,” *MIT Technology Review*, 2011, [www2.technologyreview.com/article/423683/homomorphic-encryption/](http://www2.technologyreview.com/article/423683/homomorphic-encryption/).

    **[4](#part0030.xhtml#ch19note4).**  K. Lauter, M. Naehrig, and V. Vaikuntanathan, “Can Homomorphic Encryption be Practical?” Microsoft Research, 2011, [www.msr-waypoint.com/pubs/148825/ccs2011_submission_412.pdf](http://www.msr-waypoint.com/pubs/148825/ccs2011_submission_412.pdf).

    **[5](#part0030.xhtml#ch19note5).**  C. Gentry and S. Halevi, “Implementing Gentry’s Fully-Homomorphic Encryption Scheme,” in *Advances in Cryptology – EUROCRYPT 2011 Lecture Notes in Computer Science*, vol. 6632, 2011, 129–148, [http://link.springer.com/chapter/10.1007%2F978-3-642-20465-4_9#page-2](http://link.springer.com/chapter/10.1007%2F978-3-642-20465-4_9#page-2).

    **[6](#part0030.xhtml#ch19note6).**  You can download the Paillier code from [www.csee.umbc.edu/~kunliu1/research/Paillier.html](http://www.csee.umbc.edu/~kunliu1/research/Paillier.html).

    **[7](#part0030.xhtml#ch19note7).**  S. Selvan, R. Rajan, and S. Tamilenthi, “An overview of new trends in cryptography,” *Recent Research in Science and Technology* 2012, 4(6), 38–42.

### A  

**Implementing Cryptography**

This appendix provides brief tutorials for several cryptography products, including those for file/drive and e-mail encryption. It also includes tools to aid in learning cryptography that can provide you with options for implementing cryptography to secure your data. If this book is used as a textbook, the tutorials can be used as labs for the class.

#### Hard Drive/File Encryption
