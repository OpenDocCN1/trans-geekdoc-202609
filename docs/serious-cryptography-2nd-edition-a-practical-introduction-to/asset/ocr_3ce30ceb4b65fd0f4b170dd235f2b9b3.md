**AddRoundKey** XORs a round key to the internal state.

**SubBytes** Replaces each byte (s₀, s₁ . . . , s₁₅) with another byte according to an S-box. In this example, the S-box is a lookup table of 256 elements.

**ShiftRows** Shifts the iᵗʰ row of i positions, for i ranging from 0 to 3 (see Figure 4-5).

**MixColumns** Applies the same linear transformation to each of the four columns of the state (that is, each group of cells with the same shade of gray, as on the left side of Figure 4-5).

![](bbox=[0.24, 0.34, 0.68, 0.47])

*Figure 4-5: ShiftRows rotates bytes within each row of the internal state.*

Remember that in an SPN, the S stands for substitution and the P for permutation. Here, the substitution layer is SubBytes, and the permutation layer is the combination of ShiftRows and MixColumns.

The key schedule function KeyExpansion, as Figure 4-4 shows, is the AES key schedule algorithm. This expansion creates 11 round keys (K₀, K₁, . . . , K₁₀) of 16 bytes each from the 16-byte key, using the same S-box as SubBytes and a combination of XORs. One important property of KeyExpansion is that given any round key, Kᵢ, an attacker can determine all other round keys as well as the main key, K, by reversing the algorithm. The ability to get the key from any round key reduces the cipher's resistance to side-channel attacks, where an attacker may easily recover a round key.

Without these operations, AES would be totally insecure. Each operation contributes to AES's security in a specific way:

+   - Without KeyExpansion, all rounds would use the same key, K, and AES would be vulnerable to slide attacks.
+   - Without AddRoundKey, encryption wouldn't depend on the key; hence, anyone could decrypt any ciphertext without the key.
+   - SubBytes brings nonlinear operations, which add cryptographic strength. Without it, AES would just be a large system of linear equations that can be solved using high school algebra (namely, Gaussian elimination).
+   - Without ShiftRows, changes in a given column would never affect the other columns, meaning you could break AES by building four 2³²-element codebooks for each column. (Remember that in a