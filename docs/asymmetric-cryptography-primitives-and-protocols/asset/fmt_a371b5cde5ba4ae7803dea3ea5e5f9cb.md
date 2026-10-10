
The loss in the reduction from forgeries against the Schnorr signature scheme to the discrete-logarithm problem seems inevitable. Seurin (2012) gave strong evidence that the linear loss `qH` in the security bound is inherent. His result rules out algebraic reductions with tighter bounds, assuming the one-more discrete logarithm problem. The non-tightness for generic reductions was later confirmed by Fleischhacker et al. (2019).

Concerning the assumption about the hash function being a random oracle, Neven et al. (2009) gave a security proof for the Schnorr signature scheme under standard assumptions about the hash function, but relying on the generic group model. In the analysis, they use a conversion function `f` mapping elements from the idealized group to bit strings for computing `H(f(R), m)`. Brown (2015b,a) later raised the question if the wrong choice of the conversion function allowed for attacks. It remains open if the “right” conversion function resurrects the security proof.

Concerning other possibility to avoid the strong random oracle model, there are meta-reduction results suggesting that this is infeasible. Paillier and Vergnaud (2005) showed that algebraic reductions cannot be used to show security of Schnorr signatures against key-only attacks, assuming the one-more discrete logarithm problem. Fischlin and Fleischhacker (2013) have complemented this, also under the one-more discrete logarithm assumption, for reductions which do not program the random oracle but which run only a single resettable instance of the adversary.

## 2.3. Strong unforgeability

In the EUF-CMA-definition above, we exclude attacks where the adversary copies a previously signed message in the forgery. In the experiment, this is captured by stipulating `m* ∉ Q` for the forgery attempt `m*` has not been queried before. Here, we discuss a stronger security property that prevents the adversary from transforming signatures. In other words, the adversary cannot even produce a new signature to a previously signed message.

### 2.3.1. Discussion

Strong unforgeability of signatures prevents malleability attacks where the adversary modified a pair `(m, σ)` into a related pair `(m, σ*)` for the same message. This is, for example, useful in situations where the signature is part of a ciphertext and one aims to show chosen-ciphertext security of the encryption scheme. In such a chosen-ciphertext attack, the adversary receives a challenge ciphertext `c` and tries to determine some information about the encapsulated message. To do so, the adversary is allowed to query for decryptions of *different* ciphertexts `c*`. If the challenge ciphertext `c` contained a malleable signature `σ`, then the encryption attacker could possibly maul this signature into another signature `σ*` without affecting the authenticity of the signed data, and submit the modified ciphertext `c*` to the decryption oracle to learn the original message.

Indeed, until recently, the usage of strongly unforgeable schemes has mainly been used to ensure non-malleability in ciphertexts (e.g. Canetti et al. 2004) and zero-knowledge proofs (e.g. Sahai 1999). Recently, however, strong unforgeability of signatures has gained quite some attention in the area of cryptocurrencies where signatures are used to authenticate money transfers. There, the issue of signatures which are not strongly unforgeable have emerged under the term transaction malleability attacks.

In a cryptocurrency like Bitcoin transactions used to carry a transaction identifier `TxID`, which was a (double) SHA256 hash value of the raw transaction data `transaction` and the signature information `scriptSig`:

![image](images/p57-1.jpg)

Suppose now that Alice transferred some amount to Bob with this transaction identifier `TxID`, but Bob modified the signature in `scriptSig` to some other valid signature (which may be possible if the signature scheme was not strongly unforgeable). This resulted in another valid transaction under a different identifier

![image](images/p57-2.jpg)

yet still transferring the money to Bob. If now Bob complained that he had not received the amount from transaction `TxID`, correctly claiming that the original transaction identifier does not appear on the ledger, then Alice might have been tricked into re-issuing the transfer, making Bob effectively receive the amount twice.

Besides the attack on the cryptographic property of the signature scheme, an adversary may also target the (ambiguous) encodings of signatures and transaction data, aiming to produce syntactically different but semantically equivalent transactions. That is, modifying `transaction` in such a way would also yield a different identifier `TxID*`. While these attacks sound rather theoretical, transaction malleability has led to the fall of the Bitcoin exchange MtGox in 2014 (Decker and Wattenhofer 2014). To be fair, the attack on MtGox seemed to have targeted the encoding of signatures and transaction data, rather than the malleability of the signature scheme.

Note that one can fix the transaction malleability of the signature scheme by switching to a strongly unforgeable scheme. Indeed, Bitcoin has slightly modified the signature scheme, making it more robust against known malleability attacks; we will discuss this later in [section 2.3.3](#c02.xhtml#sec2-3-3). In order to cover also other transaction malleability attacks, Bitcoin has moved the signature out of the identifier computation with the soft fork `SegWit` in 2017.

### 2.3.2. Strong existential unforgeability under chosen-message attacks

We extend the EUF-CMA-definition above and now store the message-signature pairs generated in the signature queries in `Q`. The adversary then needs to produce a forgery where either the message is new, or where at least the signature for the message in the forgery is new. This is captured by demanding that `(m*, σ*) ∉ Q`:

**DEFINITION 2.5 (sEUF-CMA).** A signature scheme `S` = (`S.KGen`, `S.Sig`, `S.Vf`) is strongly existentially unforgeable under adaptive chosen-message attacks (sEUF-CMA) if for any PPT adversary `A` the advantage

![image](images/p58-1.jpg)

is negligible, where

![image](images/p58-2.jpg)

As in the case of EUF-CMA, we can also define a concrete version of `(t, q, ϵ)`-SEUF-CMA security.

### 2.3.3. Strong unforgeability of practical schemes

We discuss here quickly the question of strong unforgeability of (EC)DSA and Schnorr signatures. This is easy for the case of Schnorr’s scheme, where this is enforced by design: The security reduction of basic unforgeability of the scheme simultaneously shows strong unforgeability.

For DSA, the situation is less clear. The result by Fersch et al. (2016) shows strong unforgeability of DSA, assuming again an idealized conversion function under the discrete logarithm assumption. For the elliptic curve variant ECDSA, it is known that the scheme does *not* provide strong unforgeability. The reason lies in the bad interplay between elliptic curve cryptography and the conversion function, mapping to the `x`-coordinate. To see this, it is instructive to write the main verification check additively, as common for elliptic curves:

![image](images/p58-3.jpg)

It is known that for any point `S` = (`S[x], S[y]`) on the curve, the (additive) inverse point `−S` is also on the curve. In fact, it holds `−S` = (`S[x],` `−S[y]`) such that the points `S` and `−S` coincide in the `x`-coordinate. This allows an adversary to modify a given signature `(r, s)` into another valid signature `(r,` `−s mod q)` for the same message:

![image](images/p58-4.jpg)

and hence the `x`-coordinate of the group element for verification of `s mod q` maps to the same one as for `s`.
