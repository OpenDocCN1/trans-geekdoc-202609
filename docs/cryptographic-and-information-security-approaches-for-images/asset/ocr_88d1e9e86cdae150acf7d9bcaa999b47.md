# Algorithm 2 The proposed scheme

Input: A M × N binary secret image S, Original QR₁ message, Original QR₂ message... Original QRₙ message, the threshold parameters (k, n)
Output: QR code shares SC₁, SC₂,... SCₙ

Step 1: Turn left and right the secret image, then rotate it 90 degrees anticlockwise.

Step 2: S is divided into 2n regions, denoted as:
A[1]: {(i₁, j₁)} ∈ {((i₁, j₁) | 1 ≤ i₁ ≤ N; 1 ≤ j₁ ≤ ⌊M/2n⌋)}
A[2]: {(i₂, j₂)} ∈ {((i₂, j₂) | 1 ≤ i₂ ≤ N; ⌊M/2n⌋ ≤ j₂ ≤ ⌊M/n⌋)}
A[2n]: {(i₂ₙ, j₂ₙ)} ∈ {((i₂ₙ, j₂ₙ) | 1 ≤ i₂ₙ ≤ N; ⌊(2n−1)M/2n⌋ ≤ j₂ₙ ≤ M}

Step 3: Let Q₁, Q₂,... Qₙ denote the regions of QR₁.., QRₙ with the same size of S in the processing QR codes from the coordinate of (7,7) to the right down corner of QR code, and Qₓ(i,j) indicates the encoded bits corresponding to QRₓ message. In the encoding processing of QR₁ message, QR₂ message... QRₙ message for each position (i,j) ∈ {(i,j) | 1 ≤ i ≤ N; 1 ≤ j ≤ M}, repeat Steps 4–5.

Step 4: For the regions of A[x] and A[n + x], randomly select (k−1) processing QR codes from Q₁, Q₂,... Qₙ excluding Qₓ, denoted as Qᵢ₁(i,j), Qᵢ₂(i,j),..., Qᵢₖ₋₁(i,j).

Step 5: If S(i,j) ≠ Qₓ(i,j) ⊕ Qᵢ₁(i,j) ⊕ Qᵢ₂(i,j) ⊕ ... ⊕ Qᵢₖ₋₁(i,j), Qₓ(i,j) = Qₓ(i,j).

Step 6: Output the n QR code shares SC₁, SC₂,... SCₙ.

Algorithm 2 takes one secret image S and n original QR code messages as the input and outputs n QR code shares SC₁, SC₂,... SCₙ. Each QR code share is a valid QR code which will gain the original message when decoded by a QR code reader. The secret recovery of the proposed scheme can be based on stacking or XOR operation, and the secret image can be revealed in the encoding regions by any k or more QR code shares.

# 20.3.2 Performance Analyses

From the above steps, in Step 1 the data generation when encoded before data mask is stored in an array module from left to right while the pixels of image shown are from top to bottom, so that the secret image preprocessing as Step 1 can be