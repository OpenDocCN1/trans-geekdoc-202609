ASIC miners perform complex calculations, known as hashing. The technique of cryptographic hash is utilized to achieve this. Hash functions compress a string of arbitrary length to a string of fixed length. The purpose of a hash function is to produce a “fingerprint” of a file, message, or other blocks of data. A hash function must have the following requirements [11–13]:

+   - One way property: For any given value h, it is computationally infeasible to find x with H(x) = h.

+   - Weak collision resistance: For any given block x, it is computationally infeasible to find y with H(x) = H(y).

+   - String collision resistance: For any given block x, it is computationally infeasible to find x and y with H(x) = H(y).

The most common hashing algorithm used in the various blockchains is SHA256. SHA256 produces a 64-character hash. The SHA256 hashing algorithm was developed by National Security Agency (NSA) in 2001.
Recommend the use of double SHA256 or SHA512 because of its capability to convert a larger amount of data into hash efficiently. The input to the double SHA256 process is a 1,024-bit message, which includes a 32-bit version, a 256-bit hash of the previous block, a 256-bit hash of the Merkle root, a 32 bit timestamp, a 32 bit target, a 32 bit nonce, and 384-bit padding. The 1,024-bit message is split into two 512-bit message parts. Then SHA2561 calculates a hash value of the first 512 bit and SHA2562 computes the hash value of the final 512-bit message.
The aspects associated are:

+   - Padding: The input message is appended to it to get it to the desired length. The bits that are used for padding are simply “0” bits with a “1” (100....0). Also, according to the algorithm, padding needs to be done even if it is by 1 bit. If we need M the message to be hashed and l length in bits where 1 < 264, then as a first step we create the padded message M, which is M plus padding,

+   - Blocks: M is passed into N blocks of size 512 bits. M1 to Mn and each block is expressed as 16 input sets of size 32 bytes.

+   - Hash initialization: The initial value H0 of generic sets a block and verifies it and will be rewarded for using their CPU power to do so. During the verification of the block, the mines will complete the proof of work which covers all the data of the block, and check whether the hash value of the current block is less than the target. Miners compete to complete the proof of work at the earliest.

+   - Nonce: The nonce is the central part of this proof of work. The nonce is a random number which is a 32-bit field, which is adjusted by miners so that it becomes a valid number to be used for hashing the value of the block. The nonce is the number that can be used only once.