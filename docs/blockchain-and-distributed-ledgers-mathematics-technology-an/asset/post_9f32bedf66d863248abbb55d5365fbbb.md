
keys, splitting secret keys into multiple distributed shards, or purpose-built hardware with electronic protections.

A hardware security module, or HSM, is a device offering cryptographic features in a trusted environment. It guarantees data confidentiality and integrity in presence of both cyber threats and physical threats to the system. It is the core component of a public key infrastructure, which manages roles and procedures needed to use and store digital certificates and provide public-key encryption. It typically provides services for the crypto-secure generation and safeguarding of key material, the computation of digital signatures, data encryption, the storage of passwords and credentials, and it occasionally offers a secure execution environment to define conditional access to the HSM services. Although HSMs have been used mainly in critical business contexts, they have become more common also on the retail market in the late 2000s with various portable devices such as YubiKeys and cryptocurrency wallets such as Ledger Nano or Trezor. Even recent mobile phones now embedded secure chips which provide a hardware secure environment for the management of the lifecycle of keys and secrets in general.

## 9.3 Wallet genesis

### 9.3.1 Key space

A wallet corresponds to a set of secret keys and addresses; addresses are used as pseudo-anonymous account identifiers on the distributed ledger. The security of distributed ledgers relies on the capacity to prove ownership with digital signatures. It is essential that secret keys are generated from a good enough entropy so that they cannot be guessed or brute force; randomness being the only defense mechanism, key collision should also be statistically improbable, even when the computational cost of key generation is low.

Let us consider the example of a 32-bit key 4,294,967,296 combinations. Such keys might look good enough when generating the key of a specific user has a probability of $2^{-32}$ which is about 30 times less probable than winning the jackpot at EuroMillions lottery. However, compared to the lottery where one combination might cost several Euros, generating cryptographic keys is inexpensive and may easily be computationally scaled to millions of attempts per second at negligible cost. A full iteration through practice there are multiple users, each possibly managing many keys, therefore dramatically increasing the probability of a collision as reminded by the Birthday paradox in Section 4.9.

Most cryptocurrencies use keys of 256 bits, therefore have approximately $10^{77}$ combinations. In order to illustrate the magnitude of this, we shall loosely compare the number of atoms in the universe, estimated to $10^{80}$. Generating a secret key is akin to selecting a specific atom in the universe and guessing someone else' key amounts to guessing the right atom in the universe. The improbability of a successful collision is such that it is deemed computationally infeasible and the risk can be ignored in practice.

There is no need to test for pre-existence of a key after generation as there should never be two generation events leading to the same outcome within the bounds of human existence.

### 9.3.2 Brain wallet

We emphasize that a 256 bit integer does not necessarily embed 256 bits of entropy. In order to illustrate this point, we present what is probably the most terrible, yet exciting idea that Bitcoin entrepreneurs came with: brain wallets. A brain wallet is a wallet whose keys are deterministically derived from a single human-readable and memorizable (therefore “brain”) passphrase. The passphrase may be anything from a single word, a long sentence, or a series of uncorrelated wordlists. The advantage of this approach is: one may simply remember the passphrase in order to access his wallet from any location in the world, with no need for backup or physical security devices. The brain wallet is a direct mapping from some secret information deep inside the memory of your brain! Figure 9.3 illustrates the principle.

The wallet key 663C658D7F16F48D763C156DCBC28D12887FCC7A097E9F8D53091F4B98152, expressed in hexadecimal, looks like a fully random 256-bit integer. In a simple binomial test is unable to reject the null hypothesis of Bernoulli draws for at a 5% level and it is expected that other tests would fail at identifying any divergence from i.i.d. random draws. The hash function does its job properly in taking a source and compressing it into a truly random-looking integer.

However, the seeding of the hashing algorithm has dangerously low entropy. Information Theory’s father C. E. Shannon showed in Shannon (1951) that the entropy of printed longer than 100-letter sequences of an English text should be bounded between 0.6 and 1.3 bits per letter. His analysis relies on a human prediction approach and ignores punctuation and character case. Other studies further entropy per character between 1.25 and 1.77; see, e.g., Cover and King (1978); Teahan and Cleary (1996); Kontoyiamnis (1997). Blindly applying these results to our 17 characters-long seed “Bitcoin is secure”— and ignoring the aggravating factor that it contains two of the most widely used words in the cryptocurrency community, “Bitcoin” and “secure”— we are able to finally conclude that entropy is lower than 32 bits.

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_314_0.png)

Figure 9.3: Brain wallet key generation. Own graphics.

The defect in the architecture of brain wallets led attackers to build simple brute-force tools to break wallets. Rather than iterating through the 256-bit integer space, attackers would focus on the English language, applying dictionary attacks and scale the system with parallelism to test billions of combinations. Researchers of the study titled “The Bitcoin Drain: A Short Paper on the Abuse of Bitcoin Wallets” by Vasek et al. (2016) identified 300 million passwords based on a wide range of word lists and identified 884 brain wallets over September 2011 and August 2015. Because brain wallets used no salt and plaintext through a single hash iteration, the attackers could trivially implement a large-scale measurement of the use of active community that rapidly steals from vulnerable wallets in nearly all cases. “Many wallets are drained within minutes, and those storing larger values are emptied within 24 hours,” claim the authors. One can see that without investing effort in brute-forcing, the simple use of public dictionaries and databases compromises a substantial number of seemingly secure wallets still hold funds at the time of the attack.

**Table 9.2 Wallets compromised by different data sources.**

| Dictionary Source | # Wallets | # Empty | Total BTC |
| :--- | :--- | :--- | :--- |
| Urban Dictionary | 296 | 3 | 561.95 |
| Two Words | 13 | 3 | 0.79 |
| Eng/Slang | 63 | 14 | 0.90 |
| Eng. Wikipedia | 250 | 0 | 38 |
| WikiQuotes | 35 | 0 | 60.96 |
| Phases | 283 | 0 | 578.69 |
| xkcd | 90 | 3 | 97.66 |
| Lyrics | 329 | 4 | 230.45 |
| Blockchain.info tags | 112 | 0 | 577.93 |
| Rootkit | 123 | 2 | 4.50 |
| MySpace | 59 | 0 | 1.14 |
| RockYou | 415 | 3 | 113.82 |
| LinkedIn | 213 | 0 | 10.11 |
| LEET MRL | 3 | 0 | 0.01 |
| Prince MRL | 295 | 4 | 88.93 |
| CrackStation | 640 | 3 | 396.09 |
| Naxxtao | 388 | 0 | 41.56 |
| Skull Security | 414 | 3 | 71.73 |
| Unipass | 490 | 3 | 134.95 |

### 9.3.3 The need for entropy

This attack emphasizes the importance of generating keys that are truly random with enough entropy and are not vulnerable to prediction or bias. Most key generation systems rely on a process called cryptographically secure Number Generator (or PRNG) for the creation of keys. A PRNG is a deterministic process producing outputs that are computationally indistinguishable from randomness. It is qualified as Cryptographically Secure (CSPNG) when adequate security requirements are verified, including testing of conditional independence between the output bits, and demonstrating that the leak of the PRNG state does not compromise past generations. Equipped with a CSPNG and some initial entropy, an application may create keys on demand in a deterministic way and be confident that every key in the sequence is strong.

However, the weak point still lies in the capacity of the system to properly collect the initial entropy of the CSPNG. Computers are inherently bad at operating tasks due to their deterministic nature: with full knowledge of the state of the system at a given time, such as contents of the disk, RAM and CPU registers, one can replicate the machine behavior and capture any future. This shows that a computer utterly cannot generate true randomness through the consideration of its own state: it must run on sources of noise. Some implementations extract entropy from ad hoc local sources such as fan noise, dice interrupts, temperatures, external inputs such as mouse movements and keyboard pressures, which contain some inherent level of randomness. Alternatively, Random.org is one example of a platform offering true random numbers as a service. The platform aggregates randomness from atmospheric noise, which the company claims, for many purposes is better than the pseudo-random number algorithms typically used in computer programs.

### 9.3.4 A concrete collision attack

In 2015, the largest BTC wallet provider blockchain.info was subjected to a grave security flaw. Blockchain.info security model relies on the generation of a key on the mobile device or computer of the wallet owner directly. The key is immediately encrypted with a passphrase that is only known to the wallet owner. The secret keys, encrypted with the user passphrase, are stored on the servers of Blockchain.info but can be decrypted with the user passphrase makes Blockchain.info resistant to many forms of attacks and makes the possible consequences of a data breach less catastrophic.

The key generation itself was implemented with two sources of entropy at the time: one, the local entropy provided by the user device; the other, entropy provided by Random.org. As multiple hacks led to the suspicion that Blockchain.info had a security flaw, a security audit revealed critical flaws in the implementation of the service. The most serious of the security issues was related to the use of unencrypted HTTP connections for the requests to Random.org. Random.org updated its APIs in January 2015 to require the use of the encrypted, HTTPS protocol. The lack of update of the Blockchain.info wallet application led to the generation of a secret key corresponding
