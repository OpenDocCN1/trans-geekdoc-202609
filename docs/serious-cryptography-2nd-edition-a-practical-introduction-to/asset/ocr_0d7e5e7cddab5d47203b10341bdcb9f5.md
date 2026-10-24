the result of 2x₁ + 10x₂ + x₃ + 3x₄. Such a transformation corresponds to a multiplication of a vector by a matrix. Poseidon’s matrices must satisfy certain security properties and should be designed for efficient implementation.

A full round of Poseidon applies the three layers in this order: ARC(), S to each element, and M(). A partial round applies S to only one element and may use a different matrix in M(). A Poseidon instance then iterates full rounds, partial rounds, and full rounds—the number of which depends on the instance, number of elements, finite field, and target security level.

NOTE For more details on Poseidon, see https://www.poseidon-hash.info as well as the initial Poseidon paper (https://eprint.iacr.org/2019/458.pdf) and the improved design Poseidon2 paper (https://eprint.iacr.org/2023/323.pdf).

Poseidon is one of many algebraic hash functions created to address practical use cases. Other designs include MiMC, Monolith, Rescue-Prime, and Tip5.

# How Things Can Go Wrong

Let’s look at some security failures that involve hash functions and their applications in the blockchain world.

# Broken Custom Hash

The 2017 blockchain project Iota was quite weird. It claimed to use an architecture different from the sequential chain of blocks of most blockchains, closer to direct acyclic graph (DAG), which was much less secure. It also encoded data not in bits but in trits, units taking three values instead of two, supposedly to make computations more efficient on processors that don’t exist.

Iota didn’t use an elliptic curve-based signature scheme like ECDSA or Ed25519 but rather a hash-based signature scheme based on the established Winternitz construction, thus offering post-quantum security—except Iota also designed its own custom hash function, Curl.

Iota became one of the top 10 most popular cryptocurrencies and made grandiose claims about its potential usefulness and its security. But its custom hash function, which it claimed to develop with the aid of artificial intelligence, turned out to be very weak against collision attacks. Using off-the-shelf hardware, researchers found collisions within minutes, which could be exploited only in contrived attack scenarios. Iota quickly patched its hash function.

> After this fiasco, renowned cryptography and security expert Bruce Schneier commented, “In 2017, leaving your crypto algorithm vulnerable to differential cryptanalysis is a rookie mistake. It says that no one of any caliber analyzed their system, and that the odds that their fix makes the system secure is low.”