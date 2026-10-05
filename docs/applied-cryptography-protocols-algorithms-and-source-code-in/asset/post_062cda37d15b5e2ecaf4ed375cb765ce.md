
## 11.6 Discrete Logarithms in a Finite Field

to test [4]. Testing against all primes less than 100 eliminates 76 percent of the odd numbers; testing against all primes less than 256 eliminates 80 percent. In general, the fraction of odd candidates that is not a multiple of any prime less than n is 1.12/ n. The larger n you test up to, the more precomputation is required before you get to the Rabin-Miller tester.

One implementation of this method on a Spare B I was able to find 256-bit primes in an average of 2.8 seconds, 512-bit primes in an average of 24.0 seconds, 768-bit primes in an average of 2.0 minutes, and 1024-bit primes in an average of 5.1 minutes [918].

## Strong Primes

If n is the product of two primes, p and q, it may be desirable to use strong primes for p and q. These are primes with certain properties that make the product n difficult to factor by factoring methods. Among the properties suggested have been [1328,651]:

- The greatest common divisor of p-1 and q-1 should be small.
- p-1 and q-1 should have large prime factors, respectively p' and q'.
- p'-1 and q'-1 should have large prime factors.
- p+1 and q+1 should have large prime factors.
- (p-1)/2 and (q-1)/2 should be prime [182]. [Note that if this condition is true, then so are the first two].

Whether strong primes are necessary a subject of debate. These properties were designed to thwart some older factoring algorithms. However, the fastest algorithms have as good a choice of factoring numbers that meet these criteria as they do of factoring numbers that do not [831].

I recommend against generating strong primes. The length of the primes is much more important than the structure. Moreover, structure may be damaging because it is less random.

This may change. New factoring techniques may be developed that work better on numbers with certain properties than numbers without them. If so, strong primes may be required once again. Check current theoretical mathematics journals for updates.

## 11.6 DISCRETE LOGARITHMS IN A FINITE FIELD

Modular exponentiation is another one-way function used frequently in cryptography. Evaluating this expression is easy:

```
a^n \pmod{n}
```

The inverse problem of modular exponentiation is that of finding the discrete logarithm of a number. This is a hard problem:

# CHAPTER 11 Mathematical Background

Find $x$ where $a^x \equiv b \pmod n$.

For example:

If $3^x \equiv 15 \pmod{17}$, then $x = 6$

Not all discrete logarithms have solutions (remember, the only valid solutions are integers). It's easy to see that there is no solution, x, to the equation

$3^x \equiv 7 \pmod{13}$

It's far more difficult to solve these problems using 1024-bit numbers.

## Calculating Discrete Logarithms in a Finite Group

There are three main groups whose discrete logarithms are of interest to cryptographers:

- The multiplicative group of prime fields: GF[p]
- The multiplicative group of finite fields of characteristic 2: GF[$2ⁿ$]
- Elliptic curve groups over finite fields $F$: EC[F]

The security of many public-key algorithms is based on the problem of finding discrete logarithms, the problem has been extensively studied. A good overview of the problem, and the best solutions at the time, can be found in [1189,1039]. The current state on the topic is [1934].

If $p$ is the modulus and prime, the complexity of finding discrete logarithms in GF[p] is essentially the same as factoring an integer $n$ of the same size, when $n$ is the product of two approximately equal-length primes [1378,934]. This is:

$e^{1.9(\ln(p))^{1/3}(\ln\ln(p))^{2/3}}$

$1.923 + o(1)(\ln(p))^{1/3}(\ln\ln(p))^{2/3}$

The number field size grows, with a heuristic asymptotic estimate of

Stephen Pohl and Martin Hellman found a fast way of computing discrete logarithms in GF[p] if $p-1$ has only small prime factors [1253]. For this reason, only fields where $p-1$ has at least one large factor are used in cryptography. Another algorithm [14] computes discrete logarithms at a speed comparable to factoring; it has been expanded to fields of the form GF[$pⁿ$] [716]. This algorithm was criticized [727] for having theoretical problems. Other articles [1588] show how difficult the problem really is.

Computing discrete logarithms is closely related to factoring. If you can solve the discrete logarithm problem, then you can proven to be true). Currently, there are three methods for calculating discrete logarithms in a prime field [370,934,648]: the linear sieve, the Gaussian integer scheme, and the number field sieve.

The preliminary, extensive computing can be done only once per field. Afterward, individual logarithms can be quickly calculated. This can be a security disadvantage for systems based on these fields. It is important that different applications use different prime fields. Multiple users in the same application can use a common field, though.

In the world of extension fields, GF($2^{40}$) hasn't been ignored by researchers. An algorithm was proposed in [727]; Coppersmith's algorithm makes discrete logarithms in fields such as GF($2^{64}$) possible [368]. The precomputation stage of this algorithm is enormous, but otherwise it is nice and efficient. A practical implementation of a less efficient version of the same algorithm, after a seven-hour precomputation period, found discrete logs in GF($2^{64}$) in several seconds [1130,180].

More recently, precomputations for GF($2^{52}$), GF($2^{56}$), and GF($2^{64}$) are done, and significant progress has been made towards being executed on massively parallel computer with 1024 processors [649,650]. Computing discrete logarithms in GF($2^{80}$) is still barely out of reach.

Like discrete logarithms in a prime field, precomputation required to calculate discrete logarithms in the field GF($p^3$) has to be done only once. TaherGamal [520] gives an algorithm for calculating this.

## 12 Data Encryption Standard (DES)

### 12.1 Background

The Data Encryption Standard (DES), known as the Data Encryption Algorithm [DEA] by ANSI and the ISO, has been a worldwide standard for years. Although it is showing signs of age, it has held up remarkably against years of cryptanalysis and is still secure against all but the most powerful adversaries.

### Development of the Standard

In the early 1970s, nonmilitary research was haphazard. Almost no research papers were published in the field. Most people knew that the military used special coding to communicate, but few understood the science of cryptography. The National Security Agency (NSA) had considerable knowledge, but did not publicly admit their existence. Buyers didn't know what they were buying. Several small companies made and sold cryptographic equipment, primarily to overseas governments, and couldn't operate. No one really knew if it was secure, there was no independent body to certify the security. As one government report said [441], the intricacies of relating and working principles of the encryption/decryption were virtually unknown to all buyers, and informed decisions as to key generation, etc., have been most difficult to make.

In 1972, the National Bureau of Standards (NBS), now the National Institute of Standards and Technology (NIST), initiated a program to protect computer communications data. As part of that program, they wanted to develop a single, standard cryptographic algorithm. A single algorithm could be tested and certified, and different cryptographic equipment using it could interoperate. It would also be cheaper to implement and readily available.

In the May 15, 1973 Federal Register, the NBS issued a public request for proposals for a standard cryptographic algorithm. They specified a series of design criteria:

- The algorithm must provide a high level of security.
- The algorithm must be completely specified and easy to understand.
- The security of the algorithm must reside in the key; the security should not depend on the secrecy of the algorithm.
- The algorithm must be available to all users.
- The algorithm must be adaptable for use in diverse applications.
- The algorithm must be economically implementable in electronic devices.
- The algorithm must be efficient to use.
- The algorithm must be able to be validated.
- The algorithm must be exportable.

Public response indicated that there was considerable interest in a cryptographic standard, but little public expertise in the field. None of the submissions came close to meeting the requirements.

The NBS issued a second request in the August 27, 1974 Federal Register. Eventually they received a promising candidate: an algorithm based on one developed by IBM during the early 1970s, Lucifer. IBM had a team working on cryptography at Kingston and Yorkton Heights, Roy Adler, Don Coffmith, Horst Feistel, Edna Grossman, Alan Konheim, Carl Meyer, Bill Notz, Lynn Smith, Walt Tchman, and Bryan Tucker.

The algorithm, although complicated, was straightforward. It used only logical operations on small groups of bits and could be implemented efficiently in hardware.

The NBS requested the NSA's help in evaluating the algorithm's security and determining its suitability as a federal standard. IBM had already filed for a patent [514], but was willing to make its intellectual property available to others for manufacture, implementation, and use. Eventually, the NBS worked out the terms of agreement with IBM and granted a nonexclusive, royalty-free license to use, make, and sell equipment that implemented the algorithm.

Finally, in March 17, 1975 Federal Register, the NBS published both the details of the algorithm and IBM's statement granting a nonexclusive, royalty-free license for the algorithm, and requested comment [536]. Another notice, in the August 1, 1975 Federal Register, again requested comments from agencies and the general public.

And there were comments [721,497,1120]. Many were wary of the NSA's “invisible hand” in the development of the algorithm. They were afraid that the NSA had