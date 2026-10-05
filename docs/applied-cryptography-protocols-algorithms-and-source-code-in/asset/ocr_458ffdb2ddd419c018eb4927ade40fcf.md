# 13.12 Skipjack 329

16 bits, which are XORed with the remaining sub-block; then the block is circularly shifted 16 bits to become the input to the next round, or shift. This also implies 128 bytes of S-box data. I suspect that the S-boxes are key-dependent.

The structure of Skipjack is probably similar to DES. The NSA realizes that their tamperproof hardware will be reverse-engineered eventually; they won't risk any advanced cryptographic techniques.

The fact that the NSA is using the Skipjack algorithm to encrypt their Data Defense Messaging System [DMS] implies that the algorithm is secure. To convince the skeptics, NIST used a panel of "respected experts from outside the government ... access to the confidential details of the algorithm to assess its capabilities and publicly report its findings" [812].

The preliminary report of these experts [262] (there was never a final report, and probably never will be) concluded that:

Under an assumption that the cost of processing power is halved every 18 months, it will be 36 years before the breaking Skipjack by exhaustive search will be equal to the breaking of DES today. There is no significant risk that Skipjack will be broken by exhaustive search in the next 30–40 years.

There is no significant risk that Skipjack can be broken through a shortcut method of attack, including differential cryptanalysis. There are no weak keys; there is no complementation property. The experts, not having time to evaluate the algorithm to any great extent, instead evaluated NSA's own design and evaluation process.

The strength of Skipjack against a cryptanalytic attack does not depend on the secrecy of the algorithm.

Of course, the panelists did not look at the algorithm long enough to come to any conclusions themselves. They all did to look at the results that the NSA showed them.

One unanswered question is whether the Skipjack keyspace is flat [see Section 8.2]. Even if Skipjack has no weak keys in the DES sense, sense of the keyscheduling process could make some keys stronger than others. Skipjack could have $2^{70}$ keys, far more than DES; the odds of choosing one of those keys at random would be 1 in 1000. I personally think the Skipjack keyspace is flat, but the fact that no one has ever said this publicly is worrisome.

Skipjack is patented, but the patent is being withheld from distribution by a patent secrecy agreement [1122]. The patent will only be issued when and if the Skipjack algorithm is successfully reverse-engineered. This gives the the best of both worlds: the protection of a patent and the confidentiality of a trade secret.