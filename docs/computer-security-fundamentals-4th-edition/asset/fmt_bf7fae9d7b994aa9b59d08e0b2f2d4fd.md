
The chosen plain text attack is closely related to the known plain text attack, but with the chosen plain text attack, the attacker has found a method to get the target to encrypt messages the attacker chooses. This can allow the attacker to attempt to derive the key used and thus decrypt other messages encrypted with that key. The method can be difficult but is not impossible. It requires many thousands of chosen plain text samples to be successful.

##### Cipher Text Only

With a cipher text only attack, the attacker only has access to a collection of cipher texts. This is much more likely than known plain text, but it is also the most difficult type of attack. A cipher text only attack is completely successful if the corresponding plain texts can be deduced or, even better, if the key can be deduced. Even the ability to obtain any information at all about the underlying plain text is considered a success.

##### Related-Key Attack

A related-key attack is like a chosen plain text attack except that the attacker can obtain cipher texts encrypted under two different keys. This is actually a very useful attack if you can obtain the plain text and matching cipher text.

### Cryptography Used on the Internet

What sort of encryption is used on bank websites and for e-commerce? In general, symmetric algorithms are faster and require a shorter key length to be as secure as asymmetric algorithms. However, there is the problem of how to securely exchange keys. So most e-commerce solutions use an asymmetric algorithm to exchange symmetric keys and then use the symmetric keys to encrypt the actual data.

When visiting websites that have an HTTPS at the beginning rather than HTTP, the *S* denotes *Secure*. It means traffic between your browser and the web server is encrypted—usually with either SSL (Secure Sockets Layer) or TLS (Transport Layer Security). SSL, the older of the two technologies, was developed by Netscape. Both SSL and TLS are asymmetric systems.

### Quantum Computing Cryptography

One of the most engaging cryptography-related topics in recent times is quantum computing. Here we explain a bit about quantum computing and then look at its impact on cryptography.

The essential issue with quantum computing is the ability to represent more than two states. Current computing technology, using classical bits, can represent only binary values. Qubits, or quantum bits, store data via the polarization of a single photon. The two basic states are horizontal polarization and vertical polarization; however, quantum mechanics allows for a superposition of the two states at the same time—which is simply not possible in a classical bit. The two states of a qubit are represented with quantum notation as |0> and |1>, representing horizontal polarization and vertical polarization. A qubit involves the superposition of these two basis states. This superposition is represented as |ψ> = α|0> + β|1>. Essentially a classical bit can represent a 1 or a 0. A qubit can represent a 1, a 0, or any quantum superposition of those two qubit states, which allows for much more powerful computing.

Contrary to what you might have heard, current quantum computing is not at a stage to be useful in practical applications. Cutting-edge quantum systems of today have only 20 to 50 qubits and can only maintain data for a very short time. This makes for great research but not practical computing applications. However, many experts believe that within 10 years we will have a working, practical quantum computer. What does that mean for cryptography? Well, in 1995 Peter Shor published Shor’s algorithm, which proved that a quantum computer would be able to factor large numbers in a much shorter time than classical computers. A quantum computer can factor an integer *N* in polynomial time; actual time is log *N*. This is substantially faster than the most efficient known classical factoring algorithm (the general number field sieve) which works in subexponential time. RSA is based on the difficulty of factoring large numbers. A quantum computer is expected to be similarly efficient at solving discrete logarithm problems. Diffie-Hellman, MQV, Elgamal, and ECC are all based on the difficulty of solving the discrete logarithm problem.

What all this means is that when quantum computers become a practical reality, current asymmetric (public key) algorithms will become obsolete. At that point, current security for e-commerce, VPNs, and many other applications will no longer be secure. The U.S. National Institute of Standards and Technology (NIST) is already working on finding a quantum proof cryptography standard.^([1](#ch01.xhtml#ch01fn1)) That study is due to be finished in about 2022.

### Summary

A basic element of computer security is encryption. Sending sensitive data that is not encrypted is simply foolish. This chapter provided the basic information on how cryptography works. The most important thing to remember is that, ultimately, it is not your computer or your network that can be compromised but rather your data. Encrypting data when transmitting it is an integral part of any security plan.

In the exercises at the end of this chapter, you will practice using different cipher methods and learn more about a number of encryption methods.

### Test Your Skills

#### MULTIPLE CHOICE QUESTIONS

**[1](#app02.xhtml#ch08ans1).** It is important to understand the concepts and application of cryptography. Which of the following most accurately defines encryption?

**A.** Changing a message so it can only be easily read by the intended recipient

**B.** Using complex mathematics to conceal a message

**C.** Changing a message using complex mathematics

**D.** Applying keys to a message to conceal it

**[2](#app02.xhtml#ch08ans2).** Which of the following is the oldest encryption method discussed in this text?

**A.** PGP

**B.** Multi-alphabet encryption

**C.** Caesar cipher

**D.** Cryptic cipher

**[3](#app02.xhtml#ch08ans3).** Many classic ciphers are easy to understand but not secure. What is the main problem with simple substitution?

**A.** It does not use complex mathematics.

**B.** It is easily broken with modern computers.

**C.** It is too simple.

**D.** It maintains letter and word frequency.

**[4](#app02.xhtml#ch08ans4).** Classic ciphers were improved with the addition of multiple shifts (multiple substitution alphabets). Which of the following is an encryption method that uses two or more different shifts?

**A.** Caesar cipher

**B.** Multi-alphabet encryption

**C.** DES

**D.** PGP

**[5](#app02.xhtml#ch08ans5).** Which binary mathematical operation can be used for a simple (but unsecured) encryption method and is in fact a part of modern symmetric ciphers?

**A.** Bit shift

**B.** OR

**C.** XOR

**D.** Bit swap

**[6](#app02.xhtml#ch08ans6).** Why is binary mathematical encryption not secure?

**A.** It does not change letter or word frequency.

**B.** It leaves the message intact.

**C.** It is too simple.

**D.** The mathematics of it is flawed.

**[7](#app02.xhtml#ch08ans7).** Which of the following is most true regarding binary operations and encryption?

**A.** They are completely useless.

**B.** They can form a part of viable encryption methods.

**C.** They are only useful as a teaching method.

**D.** They can provide secure encryption.

**[8](#app02.xhtml#ch08ans8).** What is PGP?

**A.** Pretty Good Privacy, a public key encryption method

**B.** Pretty Good Protection, a public key encryption method

**C.** Pretty Good Privacy, a symmetric key encryption method

**D.** Pretty Good Protection, a symmetric key encryption method

**[9](#app02.xhtml#ch08ans9).** Which of the following methods is available as an add-in for most email clients?

**A.** DES

**B.** RSA

**C.** Caesar cipher

**D.** PGP

**[10](#app02.xhtml#ch08ans10).** Which of the following is a symmetric key system that uses 64-bit blocks?

**A.** RSA

**B.** DES

**C.** PGP

**D.** Blowfish
