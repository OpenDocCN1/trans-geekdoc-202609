newer and simpler BCryptGenRandom() interface for Windows doesn’t require the code to explicitly open a handle (or at least makes it much easier to use without a handle).

# A Hardware-Based PRNG: Intel Secure Key

We’ve discussed only software PRNGs so far, so let’s take a look at a hardware one. The Intel Digital Random Number Generator, or Intel Secure Key, is a hardware PRNG introduced in 2012 in Intel’s Ivy Bridge microarchitecture. It’s based on NIST’s SP 800-90 guidelines with the Advanced Encryption Standard (AES) in CTR_DRBG mode. Intel’s PRNG is accessed through the RDRAND assembly instruction, which offers an interface independent of the operating system and is in principle faster than software PRNGs.

Whereas software PRNGs try to collect entropy from unpredictable sources, Intel Secure Key has a single entropy source that provides a serial stream of entropy data as zeros and ones. In hardware engineering terms, this entropy source is a dual differential jamb latch with feedback—essentially, a small hardware circuit that jumps between two states (0 or 1) depending on thermal noise fluctuations, at a frequency of 3 GHz. This is usually pretty reliable.

The RDRAND assembly instruction takes as an argument a register of 16, 32, or 64 bits and then writes a random value. When invoked, RDRAND sets the carry flag to 1 if the data set in the destination register is a valid random value, and to 0 otherwise; be sure to check the CF flag if you write assembly code directly. Note that the C intrinsics available in common compilers don’t check the CF flag but do return its value.

> NOTE Intel’s PRNG framework provides an assembly instruction other than RDRAND: the RDSEED assembly instruction returns random bits directly from the entropy source, after some conditioning or cryptographic processing. It’s intended to be able to seed other PRNGs.

Intel Secure Key is only partially documented, but it’s built on known standards and has been audited by the well-regarded company Cryptography Research (see its report titled “Analysis of Intel’s Ivy Bridge Digital Random Number Generator”). Nonetheless, there have been some concerns about its security, especially following Edward Snowden’s revelations about cryptographic backdoors: PRNGs are indeed the perfect target for sabotage. If you’re concerned but still want to use RDRAND or RDSEED, mix them with other entropy sources. Doing so will prevent effective exploitation of a hypothetical backdoor in Intel Secure Key’s hardware or in the associated microcode in all but the most far-fetched scenarios.

# How Things Can Go Wrong

To conclude, I’ll present a few examples of randomness failures. There are countless examples to choose from, but I’ve chosen four that are simple enough to understand and illustrate different problems.