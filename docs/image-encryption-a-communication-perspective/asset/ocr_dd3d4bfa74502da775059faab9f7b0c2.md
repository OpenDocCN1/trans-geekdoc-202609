map produces various random keys from various orbits of the map, which guarantees the security. Based on the key, a binary sequence is generated to control the encryption algorithm. The input image of two dimensions is transformed into a 1D array and then divided into various subblocks. Then, the position permutation and value permutation are applied to each binary matrix representing a subblock. Finally, the receiver uses the same subkeys to decrypt the encrypted images. On the other hand, chaotic encryption with 2D maps like the Baker map is different, as shown in the next section.

# 2.9 The 2D Chaotic Baker Map

The Baker map stretches the image horizontally and then folds it vertically. Repeating this process, the positions of all pixels of the plainimage are changed [51,52,61]. Let B(n₁, ..., nₖ) denote the discretized map, where the vector [n₁, ..., nₖ] represents the secret key S_key. Defining N as the number of data items in one row, the secret key is chosen such that each integer nᵢ divides N, and n₁ + ... + nₖ = N.

Let Nᵢ = n₁ + ... + nᵢ. The data item at the indices (q, z) is moved to the indices:

B₍ₙ₁,...,ₙₖ₎(q,z) = ( N/nᵢ (q - Nᵢ) + z mod (N/nᵢ),  nᵢ/N (z - z mod (N/nᵢ)) + Nᵢ )  (2.18)

where Nᵢ ≤ q < Nᵢ + nᵢ, and 0 ≤ z < N.

In steps, the chaotic permutation is performed as follows:

+   1. An N × N square image is divided into k rectangles of width nᵢ and number of elements N.
+   2. The elements in each rectangle are rearranged to a row in the permuted rectangle. Rectangles are taken from left to right beginning with upper rectangles, then lower ones.
+   3. Inside each rectangle, the scan begins from the bottom left corner toward upper elements.