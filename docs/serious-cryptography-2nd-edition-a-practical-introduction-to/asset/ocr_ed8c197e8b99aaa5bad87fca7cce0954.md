Fortuna. I won’t provide the Fortuna specification here or show you how to implement it, but I will try to explain how it works. You’ll find a complete description of Fortuna in Chapter 9 of *Cryptography Engineering* by Ferguson, Schneier, and Kohno (Wiley, 2010).

Fortuna’s internal memory includes the following:

+   - Thirty-two entropy pools, P₁, P₂, . . . , P₃₂, such that Pᵢ is used every 2ⁱ reseeds.
+   - A key, K, and a counter, C (both 16 bytes). These form the internal state of Fortuna’s DRBG.

In simplest terms, Fortuna works like this:

+   - *init()* sets K and C to zero and empties the 32 entropy pools Pᵢ, where i = 1 . . . 32.
+   - *refresh(R)* appends the data, R, to one of the entropy pools. The system chooses the RNGs used to produce R values, and it should call *refresh* regularly.
+   - *next(N)* updates K using data from one or more entropy pools, where the choice of the entropy pools depends mainly on how many updates of K have already been done. The N bits requested are then produced by encrypting C using K as a key. If encrypting C is not enough, Fortuna encrypts C + 1, then C + 2, and so on, to get enough bits.

Although Fortuna’s operations look fairly simple, implementing them correctly is hard. For one, you need to get all the details of the algorithm right—how entropy pools are chosen, the type of cipher to be used in *next*, how to behave when no entropy is received, and so on. Although the specs define most of the details, they don’t include a comprehensive test suite to check that an implementation is correct, which makes it difficult to ensure that your implementation of Fortuna will behave as expected.

Even if Fortuna is correctly implemented, security failures may occur for reasons other than the use of an incorrect algorithm. For example, Fortuna might not notice if the RNGs fail to produce enough random bits, and as a result Fortuna will produce lower-quality pseudorandom bits, or it may stop delivering pseudorandom bits altogether.

Another risk inherent in Fortuna implementations lies in the possibility of exposing associated *seed files* to attackers. The data in Fortuna seed files is used to feed entropy to Fortuna through *refresh* calls when an RNG is not immediately available—for example, immediately after a system reboot and before the system’s RNGs have recorded any unpredictable events. However, if an identical seed file is used twice, Fortuna will produce the same bit sequence twice. Seed files should therefore be erased after use to ensure they aren’t reused.

Finally, if two Fortuna instances are in the same state because they’re sharing a seed file (meaning the same data in the entropy pools, including C and K), then the *next* operation will return the same bits in both instances.