
The smallest combined key and ciphertext sizes were from SIKE, followed by ROLLO and then Round5.

A great online NIST post-quantum key comparison web page is `https://pqc-wiki.fau.edu/w/Special:DatabaseHome`.

Each algorithm is also being reviewed for many other characteristics beyond key and ciphertext sizes, including

* Performance (in both software and hardware implementations)
* Storage sizes (runtime and on media)
* Key generation
* Encryption speed
* Decryption speed
* Complexity
* Ease of implementation
* Failure rates
* Ability to provide security protection

All of these factors, and more, are being reviewed by stakeholders for each submitted cipher. The ciphers that best handle these factors, along with sustained security resilience, will progress to Round 3 and/or eventually be considered for the NIST post-quantum standard cipher selection.

## Quantum-Resistant Digital Signatures

Quantum-resistant digital signature schemes are cryptographic digital signatures that are not overly susceptible to quantum computers running quantum-based algorithms. They do not use quantum-based properties to defeat attacks. There are over a dozen quantum-resistant digital signature schemes, although one or more of the nine Round 2 NIST asymmetric candidates are likely to be the eventual NIST federal standard. The NIST second-round digital candidates, in alphabetical order, are:

* CRYSTALS-Dilithium
* FALCON
* GeMSS
* LUOV
* MQDSS
* Picnic
* qTESLA
* Rainbow
* SPHINCS+

> `NOTE`  There are at least three other major quantum-resistant digital signature schemes that did not meet NIST submission criteria: Leighton-Micali Signatures (LMS), eXtended Merkle Signature Scheme-MT (XMSS), and Blockchained Post-Quantum Signatures (BPQS). At least the first two are stateful and can cause problems if not handled correctly during data restoration activities, and BPQS uses a relatively untested hybrid approach, which it calls a bridge between stateful and stateless. You can read more about XMSS and LMS at `https://eprint.iacr.org/2017/349.pdf` and about BPQS at `https://eprint.iacr.org/2018/658.pdf`.

### CRYSTALS-Dilithium

CRYSTALS (Cryptographic Suite for Algebraic Lattices) encompasses two lattice-based cryptographic primitives: Kyber, a CCA-secure KEM, and Dilithium (covered earlier), an EUF-CMA-strongly-secure digital signature algorithm, CRYSTALS-Dilithium.

CRYSTALS-Dilithium is based on MLWE, which the authors state can be thought of lattices between unstructured LWE and structured RLWE. It also uses an interactive proof-of-knowledge idea known as `Fiat-Shamir with Aborts` (`https://www.iacr.org/archive/asiacrypt2009/59120596/59120596.pdf`), which is similar to but different from ZPK systems mentioned earlier. In an `interactive proof-of-knowledge` system, the prover doesn't prove to the verifier that it knows the value of `x`. A third process known as the `knowledge extractor` does the proving to the verifier. See `https://en.wikipedia.org/wiki/Proof_of_knowledge` for more details on interactive proof-of-knowledge theories and systems.

Dilithium creates relatively small digital signatures and public keys while providing AES-128-level or larger security. For the beginning of Round 2 for the NIST required security implementations, secret key sizes of 64 bytes for all implementations (NIST Security Levels 1, 2, and 3), public key sizes range from 1,184 to 1,760 bytes, and signature sizes range from 2,044 to 3,366 bytes. Like other quantum-resistant digital signatures, Dilithium starts with a small private key, 64 bits in this case, which is just a seed value that gets pseudo-randomized into another value, which the algorithm then uses to generate the public key and digital signature.

When looking at the size of quantum-resistant digital signatures and not any other characteristic, the sizes that mean the most for comparison purposes are the public key and the resulting digital signature (and their overall combined sizes). The “private key” can often be increased and decreased. Increasing the size of the private key, the original seed value version or the eventually computed larger value actually used to do the real work, would normally decrease performance at least slightly, and vice versa. Implementers can normally, if they choose, increase or decrease the key and signature values to make their own security versus performance trade-off.

NIST instructed submitters to choose particular values to meet the different NIST security level requirements. Teams sometimes slightly modified their algorithm or values to get improved size/performance characteristics. It's part of why NIST has a “contest.” The competition improves many of the algorithms, or at least has them being as thoughtful as possible about their particular suggested implementations.

Interestingly, after CRYSTALS-Dilithium was submitted to NIST in Round 1, reviewers found a weakness, which turned out to be a simple two-line coding transposition error in the CRYSTALS-Dilithium RNG, a bug that the implementers acknowledged and fixed in a quick update. Giving the public and other teams a chance to review all algorithms, if they choose, can only help improve all algorithms. Good cryptographic algorithms sustain and improve under public review. Don't trust cryptographic creators who keep their algorithms private and don't allow the world to review and test. It's never a good sign of security. The Dilithium team is multinational and includes members from IBM and Google. It is part of the Open Quantum Safe project.

For more information on CRYSTALS, see `https://pq-crystals.org/` and `https://pq-crystals.org/dilithium/index.shtml`.

### FALCON

FALCON (FAst fourier Lattice-based COmpact signatures over NTRU) is an NTRU lattice-based digital signature algorithm based on ring short integer solution (SIS) problems (as is qTESLA). SIS problems are very hard to solve, although most lattice-based cryptography uses what is known as shortest vector problems (SVPs). FALCON is also based on a 2008 work that led to a generic framework called the Gentry, Peikert, and Vaikuntanathan (GPV) framework for building secure hash-and-sign lattice-based signature schemes. It also uses floating-point arithmetic with 53 bits of precision.

Dilithium and qTESLA rely on the Fiat-Shamir paradigm, whereas FALCON uses a competing “hash-then-sign” paradigm. Algorithms based on the former rely on proof-of-knowledge systems and can have problems securely signing long messages. Hash-then-sign algorithms overcome the issue by first hashing the message (and getting a much shorter hash result) and signing the hash result instead of the message.

> `NOTE`  CRYSTALS-Dilithium is based on Module-SIS, which is similar to but different from Ring-SIS. Essentially, they are all very hard math problems to solve, but some are harder than others. If you are interested in the mathematical and work effort differences, you can read `https://eprint.iacr.org/2012/090`.

FALCON was specifically designed to have good performance, especially in low memory environments. FALCON's creators intentionally positioned their algorithm to be a strong contender for smallest public key and signature size, but it does use floating point math (which decreases overall performance on platforms that don't inherently support that type of math).

For the beginning of Round 2 for the NIST required security implementations (FALCON submitted to NIST Levels 1 and 5 only), FALCON secret key sizes range from 1,280 to 2,304 bytes, public keys range from 897 to 1,793 bytes, and digital signatures range from 617 to 1,233 bytes. According to its creators, FALCON-512 with a public key size of 897 bytes and a digital signature of 617 bytes has security equivalent to RSA 2,048 bits (which has public keys and signatures of 256 bytes). FALCON's team is multinational, and Thomas Pornin is the primary creator.
