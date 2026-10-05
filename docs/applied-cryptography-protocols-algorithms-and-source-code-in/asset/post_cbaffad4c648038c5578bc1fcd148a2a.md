
# 534 CHAPTER 23 Special Algorithms for Protocols

... using M in place of H(m). This means that the message will be smaller than $p^qr$. She then chooses a random value, $u$, and calculates

```
x' = M' + ur
```

Then, use this $x'$ as the “random number” $x$ to sign $M'$. This second $s$ is sent as a signature.

Walter verifies that $s$ (the second $s$) is a valid signature of $M'$. Bob can also authenticate the message in the same way. But if he also knows $r$, he can calculate

```
s = x' + ypqr = M + ur + ypqr = M [mod r]
```

This implementation of a subliminal channel is far better than the previous two. In the Ong-Schnorr-Shamir and ElGamal implementations, Bob has Alice's private key. Being able to read subliminal messages from Alice, Bob can impersonate Alice and sign normal documents. Bob can do anything about this; Alice must trust Bob to use this subliminal channel.

The ESIGN scheme doesn't suffer from this problem. Alice's private key is the set of three primes: $p, q$, and Bob's secret key is $r$. However, if Alice chooses a particular $k$, then $n=pq$, but to recover $p$ and $q$ he has to factor the number. If the primes are large enough, Bob has much trouble impersonating Alice as would Walter or anyone else.

# DSA

There is also a subliminal channel in DSA (Section 20.1)[1468,1469,1473]. In fact, there are several. The simplest subliminal channel involves the choice of $k$. If Alice chooses a particular 160-bit random number, then Bob, who knows Alice's private key, can recover it. Alice can send Bob a 160-bit subliminal message in each DSA signature; everyone simply verifies Alice's signature. Another complication: Since $k$ would be random, Alice and Bob need to share a one-time pad and encrypt the subliminal message with the one-time pad to generate a $k$.

DSA subliminal channels that do not require Bob to know Alice's private key. These also involve choosing particular values of $k$, but cannot be used to send 160 bits of information. This scheme, presented in [1468,1469], allows Alice and Bob to exchange one bit of subliminal information per signed message.

- (1) Alice and Bob agree on a random prime, $P$ (different from the parameter $p$ in the signature scheme). This is their secret key for the subliminal channel.
- (2) Alice sends an anonymous message, $M$. If she wants to send Bob the subliminal bit, she makes the $r$ parameter of the signature a quadratic residue modulo $P$. If she wants to send him 0, she makes the $r$ parameter a quadratic nonresidue modulo $P$. She does this by signing the message with an $r$ with the requisite property. Since quadratic residues and quadratic nonresidues are equally likely, this shouldn't be too difficult.
- (3) Alice sends the signed message to Bob.

# 23.3 Subliminal Channel

(4) Bob verifies the signature to make sure the message is authentic. Then he checks whether $r$ is a quadratic residue or a quadratic nonresidue modulo $P$ and the subliminal bit.

Multiple bits via this method involves making $r$ either a quadratic residue or a quadratic nonresidue for a variety of parameters. See [1468,1469] for details.

This scheme can be easily extended to send multiple subliminal bits per signature. If Alice and Bob agree on two random primes, $P$ and $Q$, Alice can send two bits by choosing a random $k$ such that $r$ is either a quadratic residue mod $P$ or a quadratic nonresidue mod $P$, and either a quadratic residue mod $Q$ or a quadratic nonresidue mod $Q$. A random value of $k$ has a 25 percent chance of producing $r$ of the correct form.

Here's Mallory, an unscrupulous implementer of DSA, can have the algorithm-limit 10 bits of Alice's private key every time she signs a document.

- (1) Mallory puts its implementation of DSA in a tamperproof VLSI chip, so that no one can examine its inner workings. It creates a 14-bit subliminal channel in its implementation of DSA. That is, he chooses 14 random primes, and has the choose value of $k$ such that $r$ is either a quadratic residue or quadratic nonresidue modulo each of those 14 primes, depending on the subliminal message.
- (2) Mallory distributes the chips to Alice, Bob, and everyone who wants them.
- (3) Alice signs a message normally, using her 160-bit private key, $x$.
- (4) The chip chooses a 10-bit block of $x$: the first 10 bits, the second 10 bits, and so on. Since there are 16 possible 10-bit blocks, a 4-bit number can identify which block it is. This 4-identifier, plus the 10 bits of the key, is the 14-bit subliminal message.
- (5) The chip tries random values of $k$ until it finds one that has the quadratic residue properties to the subliminal message. The odds of a random $k$ being of the correct form are 1 in 16. Assuming the chip can test 10,000 values of $k$ per second, it will find one in less than two seconds. This computation does not involve the message and can be performed offline, before Alice waits to sign a message.
- (6) The chip signs the message normally, using the value of $k$ chosen in step (5).
- (7) Alice sends the digital signature to Bob, or publishes it on the network, or whatever.
- (8) Mallory recovers $r$, and because he knows the 14 primes, decrypts the subliminal message. It's even that if Alice knows what is happening, she cannot prove it. As long as those 14 primes stay secret, Mallory is safe.

# CHAPTER 23 Special Algorithms for Protocols

# Foiling the DSA Subliminal Channel

The subliminal channel relies on the fact that Alice can choose $k$ to transmit subliminal information. To foil the subliminal channel, Alice cannot be allowed to choose $k$. However, neither can anyone else; if someone else were allowed to choose $k$, it would allow them to forge Alice's signature. The only solution is for Alice to jointly generate $k$ with another party, call him Bob, in such a way that Alice cannot control a single bit of $k$ and Bob cannot know a single bit of $k$. At the end of the protocol, Bob should be able to verify that Alice used the $k$ they jointly generated.

- (1) Alice chooses $k$ and sends it to Bob: $u = g^k \mod p$.
- (2) Bob chooses $k''$ and sends it to Alice.
- (3) Alice calculates $k = kk'' \mod (p-1)$. She uses $k$ to sign her message, $M$, and sends the signature: $r$ and $s$.
- (4) Bob verifies $(u^k \mod p) = r$.

If it does, then $k$ was used to sign $M$. After step (4), Bob knows that no subliminal information can be embedded in $r$. If he is a trusted party, he can certify that Alice's signature is subliminal-free. Others will have to trust his certification; Bob cannot prove this fact to a third party with a transcript of the protocol. A surprising result is that if Bob wants to, he can use this to create his own subliminal channel. Bob can embed a subliminal message in one of Alice's signatures by choosing $k'$ with characteristics. When Simmons discovered this, he dubbed it the "Cuckoo's Channel." Details on how the Cuckoo's Channel works, and a three-pass protocol for generating $k$ that prevents it, are discussed in [1471,1473].

Other Schemes

Any signature scheme can be converted into a subliminal channel [1458,1460,1406]. A protocol for embedding a subliminal channel in the Fiat-Shamir and Feige-Fiat-Shamir protocols, as well as possible abuses of the subliminal channel, can be found in [485].

# 23.4 UNDENABLE DIGITAL SIGNATURES

This undeniable signature algorithm [see Section 4.3] is by David Chaum [343,327]. First, a large prime, $p$, and a primitive element, $g$, are made public, and used by a group of signers. Alice has a private key, $x$, and a public key, $g^x \mod p$.

# 23.4 Undeniable Digital Signatures

To sign a message, Alice computes $z = m^x \mod p$. That's all she has to do. Verification is a little more complicated.

- (1) Bob chooses two random numbers, $a$ and $b$, both less than $p$, and sends Alice:
$c = z^{(g^a)} \mod p$
- (2) Alice computes $t=x^{-1} \mod {p-1}$, and sends Bob:
$d = c^t \mod p$
- (3) Bob confirms that $d = m^{g^b} \mod p$

If it is, Alice accepts the signature as genuine. Imagine Alice and Bob went through this protocol, and Bob is convinced that Alice signed the message. Bob wants to convince Carol, so he shows her a transcript of the protocol. Dave wants to convince Carol that some other person signed the document. He creates a fake transcript of the protocol. First he generates the message in step (1). Then in step (3) he generates the fake transcript from this other person in step (2). Finally, he generates the message in step (2). Carol, both Bob and Dave's transcripts are identical. She cannot be of the signature's validity unless she goes through the protocol herself. Of course, if she was watching over Bob's shoulder as he completed the protocol, she would be convinced. There may be a problem with this signature scheme, but I know of no details. Please pay attention to the literature before you use it. Another protocol not only has a confirmation—Alice can convince Bob that her signature is valid—but also has a disavowal protocol; Alice can use a zero-knowledge interactive protocol to convince him that the signature is not valid, if it is not [329].

Like the previous protocol, a group of signers use a shared public prime, $p$, and a primitive element, $g$. Alice has a unique private key, $x$, and a public key, $g^x \mod p$. To sign a message, Alice computes $z = m^x \mod p$. To verify a signature:

- (1) Bob chooses two random numbers, $a$ and $b$, both less than $p$, and sends Alice:
$c = z^{g^b} \mod p$
- (2) Alice chooses a random number, $q$, less than $p$, and computes and sends to Bob:
$s_1 = cg^q \mod p, s_2 = \{cg^q\}^a \mod p$
- (3) Bob sends Alice $a$ and $b$, so that Alice can confirm Bob did not cheat in step (1).
