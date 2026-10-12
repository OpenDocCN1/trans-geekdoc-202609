
The problem relative to the RSA algorithm is to find two large primes `p` and `q`. With the Solovay and Strassen approach, you first guess a large candidate prime `p`. You then generate a random number `r` and compute `gcd(p,r)` and `J(r, p)`. If either of these tests fails, `p` was not a prime, and you stop the procedure. If both pass, the likelihood that `p` was not prime is at most 1/2. You repeat the process with a new value for `r` chosen at random. If this second `r` passes, the likelihood that a nonprime `p` could pass both tests is at most 1/4. In general, after the process is repeated `k` times without either test failing, the likelihood that `p` is not a prime is at most 1/2^(k).

### Cryptanalysis of the RSA Algorithm

The RSA method has been scrutinized intensely by professionals in computer security and cryptanalysis. Several minor problems have been identified with it, none of significant concern; Boneh [[BON99](#bib01.html#bib_86)] catalogs known attacks on RSA. He notes no successful attacks on RSA itself, but several serious but improbable attacks on implementation and use of RSA.

RSA is by far the most popular public key encryption algorithm in use. Now we turn to two applications of cryptography: message digests and digital signatures, both of which we introduce in [Chapter 2](#ch02.html#ch02). In this chapter we explore the algorithms in more detail.

## 12.4 Message Digests

In [Chapter 2](#ch02.html#ch02) we introduce the concept of error detection and correction codes. In particular, we describe one-way and cryptographic hash functions, both of which are designed to protect against malicious attempts to modify data and also adjust the code value to match the modified data.

### Hash Functions

As presented in [Chapter 2](#ch02.html#ch02), hash or message digest functions are ways to detect possible changes to a block of data. These functions signal unintentional changes as well as intentional (malicious) ones.

For unintentional changes, the signal function can be open, for example, parity bits or more complicated error detection and correction codes, such as Hamming codes [[HAM50](#bib01.html#bib_257)] and Reed Solomon codes [[REE60](#bib01.html#bib_514)]. In this book we are more interested in schemes for detecting malicious change and preventing the attacker from subverting the detection technique.

### One-Way Hash Functions

One-way hash functions are a cryptographic construct with multiple uses. They are used in conjunction with public-key algorithms for both encryption and digital signatures. They are used in integrity checking. They are used in authentication. They are used in communications protocols. Much more than encryption algorithms, one-way hash functions are the workhorses of modern cryptography.

One-way functions prevent an outsider from taking an existing hash result and determining other data values that match that hash result. Thus, Hector might have received a message saying "I willingly give to Hector my prized golden sponge cake recipe" and some other things. Hector can certainly change "sponge cake recipe" to "bullion collection" but then Hector is stuck: He needs to make other changes to the message, but he needs to know other content that would produce the original hash value. With a one-way function he can guess "recipe file," "box of pieces of string too short to use," and so forth. But he has to invent each such phrase and test it. It would be easier if he could run the hash function in reverse and get a list of inputs that would produce a given hash result. Alas, with a one-way function Hector is going to have to keep trying until he finds a match.

Modern hash functions must meet two criteria: They are one-way, meaning that they convert input to a digest, but it is infeasible to start with a digest value and infer an input that could have produced that digest. Second, they do not have obvious collisions, meaning that it is infeasible to find a pair of different plaintexts that produce the same digest.^([3](#ch12.html#ch12fn03a))

[3](#ch12.html#ch12fn03). Note: Some authors refer to this second property as "collision free," but that is a misleading term. Every hash function will have collisions—many of them, because the function takes a relatively large input and produces a relatively small digest. It is physically impossible to reduce 512 bits to a 128-bit digest and not have collisions. The point is that the collisions are unpredictable. We know collisions will occur; it is just infeasible to predict which pairs will collide or, given one input, to enumerate other inputs with which the first will collide.

### Message Digests

The most widely used cryptographic hash functions are `MD4`, `MD5` (where MD stands for Message Digest), and `SHA` or `SHS` (Secure Hash Algorithm or Standard). The MD4/5 algorithms were invented by Ronald Rivest and RSA Laboratories in 1990–1992. MD5 is an improved version of MD4. Both condense a message of any size to a 128-bit digest.

SHA is actually a growing family of algorithms: SHA-0, the original SHA, based on MD4/MD5, was published by NIST in 1993 but was withdrawn shortly thereafter because of an undisclosed "significant flaw." It was replaced by a slightly revised version, known as SHA-1. SHA-1 produces a 160-bit message digest from any input up to 2^(64) bits.

Wang et al. [[WAN05](#bib01.html#bib_644)] announced cryptanalytic attacks on SHA-1, MD4, and MD5. For SHA-1, the attack is able to find two plaintexts that produce the same hash digest in approximately 2^(63) steps, far short of the 2^(80) steps that would be expected of a 160-bit hash function, and very feasible for a moderately well financed attacker. Although this attack does not mean SHA is useless (the attacker must collect and analyze a large number of ciphertext samples), it does suggest use of long digests and long keys.

#### SHA-2

In 2008, NIST published a new hash standard, FIPS 180-3 [[NIS08](#bib01.html#bib_445)], that defines algorithms based on the SHA algorithm, but producing significantly longer digests, which counteract the attack described by Wang. These new algorithms are known collectively as SHA-2.

#### SHA-3

NIST also commenced a competition in 2008 to select a new hash algorithm to be known as SHA-3. In 2012 NIST formally announced selection of Keccak [[NIS14](#bib01.html#bib_449), [BER14](#bib01.html#bib_62)] as winner, to be designated SHA-3; like SHA-2 it is also a family of algorithms.

Immediately after the announcement there arose a controversy because of changes NIST sought in the internal algorithm. The basis of concern was a fear that NSA had somehow weakened the internals to make the algorithm easier for it to break. In fact, it seems that NIST requested some minor changes for performance reasons, but those changes do not weaken the algorithm. Cryptologist Bruce Schneier essentially put such concerns to rest in his blog [[SCH13](#bib01.html#bib_550)]:

> The Keccak permutation remains unchanged. What NIST proposed was reducing the hash function's capacity in the name of performance. One of Keccak's nice features is that it's highly tunable.
>
> I do not believe that the NIST changes were suggested by the NSA. Nor do I believe that the changes make the algorithm easier to break by the NSA. I believe NIST made the changes in good faith, and the result is a better security/performance trade-off.

The structure of SHA-3 is different from its predecessors in that it uses far fewer cycles, thus improving performance significantly. The algorithms do use significantly more internal memory (1600 bits as opposed to 512 for SHA-2), but the added space is available for most application domains.

Properties of MD5 and the SHA algorithms are presented in [Table 12-1](#ch12.html#ch12tab01).

![Image](graphics/12tab01.jpg)

**TABLE 12-1** Current Secure Hash Standard Properties

## 12.5 Digital Signatures
