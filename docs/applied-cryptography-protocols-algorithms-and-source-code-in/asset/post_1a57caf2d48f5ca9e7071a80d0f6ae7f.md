
# 13.9 IDEA

agreement, and have claimed to allow analysts to publish any negative results they find. I don't know of any cryptanalyst outside the employ of the company who studied it, it would amount to doing their analysis work for them.

Still, Ron Rivest is not our usual snake-oil peddler. He is a respected and competent cryptographer. I put a fair degree of trust in the algorithm, even though I've personally inspected the code. RC4, the proprietary intellectual property of RSADI, was posted to the Internet (see Section 17.1), and it's probably just a matter of time before RC2 is posted as.

An agreement between the Software Publishers Association [SPA] and the U.S. government gave RC2 and RC4 (see Section 17.1) special export status [see Section 25.14]. Products that implement one of these algorithms have a much simpler export approval process, provided that the keys are no more than 40 bits.

Is a 40-bit key enough? There are a total of one trillion keys. Assuming that brute force is the most efficient method of cryptanalysis (a big assumption, considering that the algorithm has never been published), and assuming that a brute-force cryptanalysis can test one million keys per second, it will take 12.7 days to find the key in twenty minutes.

RSA Data Security, Inc., maintains that when encryption and decryption are quick, exhaustive key search is not significant. Amount of time is spent setting up the schedule. While this is time when encrypting and decrypting messages, it is not when trying every possible key.

The U.S. government would never allow export of any algorithm it couldn't, at least in theory, break. They could create a magnetic tape or CD of a specific plaintext with every possible key. To break a given message, they could just run the tape and the ciphertext blocks in the message with the ciphertext blocks on the tape. If there is a match, they could try the candidate key and if the message makes any sense. If they find a common plaintext block (all zeros, the ASCII characters for a space, etc.), this method should work. The storage requirement for a 64-bit plaintext encrypted with $10^{12}$ possible keys is 8 terabytes—certainly possible.

For information on licensing RC2, contact RSADI (see Section 25.4).

# 13.9 IDEA

The first incarnation of the IDEA cipher, by Xuejia Lai and James Massey, survived in 1990 [929]. It was called PES [Proposed Encryption Standard]. The next year, after Biham and Shamir demonstrated differential cryptanalysis, the authors strengthened against the attack and called the new algorithm IPES [Improved Encryption Standard] [931, 1924]. IPES changed its name to IDEA (International Data Encryption Algorithm) in 1992 [925].

IDEA is based on some impressive theoretical foundations, and although analysis has made some progress against reduced-round variants, the algorithm still seems strong. In my opinion, it is the best and most secure block algorithm available to the public at this time.

The future of IDEA is not yet clear. There has been no rush to adopt it as a replacement to DES, partly because it is patented and must be licensed for commercial applications, and partly because people are still waiting to see how well the algorithm fares during the coming years of cryptanalysis. Its current claim to fame is that it is part of PGP [see Section 24.12].

## Overview of IDEA

IDEA is a block cipher, it operates on 64-bit plaintext blocks. The key is 128 bits long. The algorithm is used for both encryption and decryption.

As with all other ciphers we've seen, IDEA uses both confusion and diffusion. The design philosophy behind the algorithm is one of "mixing operations from different algebraic groups." Three algebraic groups are being mixed, and they are all easily implemented in hardware and software:

- XOR
- Addition modulo $2^{16}$
- Multiplication modulo $2^{16} + 1$. (This operation can be viewed as IDEA's S-box).

All these operations (and these are the only operations in the algorithm—there are no bit-level permutations) operate on 16-bit sub-blocks. This algorithm is efficient on 16-bit processors.

# Description of IDEA

Figure 13.9 is an overview of IDEA. The 64-bit data block is divided into four 16-bit sub-blocks: $X_1, X_2, X_3$, and $X_4$. These four sub-blocks become the input to the first round of the algorithm. There are eight rounds total. In each round the four sub-blocks are XORed, added, and multiplied with one another and with six 16-bit keys. Between rounds, the second and third sub-blocks are swapped. Finally, the four sub-blocks are combined with four subkeys in an output transformation. In each round, the sequence of events is as follows:

(1) Multiply $X_1$ and the first subkey.
(2) Add $X_2$ and the second subkey.
(3) Add $X_3$ and the third subkey.
(4) Multiply $X_4$ and the fourth subkey.
(5) XOR the results of the steps [1] and [4].
(6) XOR the results of the steps [2] and [4].
(7) Multiply the results of step [5] with the fifth subkey.
(8) Add the results of steps [6] and [7].
(9) Multiply the results of step [8] with the sixth subkey.
(10) Add the results of steps (7) and (9).

![](img/e08b4270295105438dabfbd9a81857bf_343_0.png)

**Figure 13.9** IDEA.

(11) XOR the results of steps [1] and [9).
(12) XOR the results of steps [3] and [9).
(13) XOR the results of steps [2] and [10).
(14) XOR the results of steps [4] and (10).

The output of the round is the four sub-blocks that are the results of steps [11], [12], [13], and [14]. Swap the two inner blocks (except for the last round) and that's the input to the next round.

After the eighth round, there is a final output transformation:

(1) Multiply $X_i$ and the first subkey.
(2) Add $X_2$ and the second subkey.
(3) Add $X_3$ and the third subkey.
(4) Multiply $X_4$ and the fourth subkey.

Finally, the four sub-blocks are combined with four subkeys in an output transformation.

# IDEA Encryption and Decryption Subkeys

| Round | Encryption Subkeys | Decryption Subkeys |
|---|---|---|
| 1st | $Z_1^{(1)} Z_2^{(1)} Z_3^{(1)} Z_4^{(1)}$ | $Z_9^{(9)} Z_8^{(9)} Z_7^{(9)} Z_8^{(8)}$ |
| 2nd | $Z_5^{(2)} Z_6^{(2)} Z_7^{(2)} Z_8^{(2)}$ | $Z_1^{(8)} Z_2^{(8)} Z_3^{(7)} Z_4^{(7)}$ |
| 3rd | $Z_1^{(3)} Z_2^{(3)} Z_3^{(3)} Z_4^{(3)}$ | $Z_5^{(7)} Z_6^{(7)} Z_7^{(6)} Z_8^{(6)}$ |
| 4th | $Z_5^{(4)} Z_6^{(4)} Z_7^{(4)} Z_8^{(4)}$ | $Z_1^{(6)} Z_2^{(6)} Z_3^{(5)} Z_4^{(5)}$ |
| 5th | $Z_1^{(5)} Z_2^{(5)} Z_3^{(5)} Z_4^{(5)}$ | $Z_5^{(5)} Z_6^{(5)} Z_7^{(4)} Z_8^{(4)}$ |
| 6th | $Z_5^{(6)} Z_6^{(6)} Z_7^{(6)} Z_8^{(6)}$ | $Z_1^{(4)} Z_2^{(4)} Z_3^{(4)} Z_4^{(3)}$ |
| 7th | $Z_1^{(7)} Z_2^{(7)} Z_3^{(7)} Z_4^{(7)}$ | $Z_5^{(3)} Z_6^{(3)} Z_7^{(3)} Z_8^{(2)}$ |
| 8th | $Z_1^{(8)} Z_2^{(8)} Z_3^{(8)} Z_4^{(8)}$ | $Z_1^{(2)} Z_2^{(2)} Z_3^{(1)} Z_1^{(1)}$ |
| output transformation | $Z_1^{(9)} Z_2^{(9)} Z_3^{(9)} Z_4^{(9)}$ | $Z_1^{(1)} - Z_1^{(1)} - Z_1^{(1)} - 1$ |
