# 14.3 CAST 335

To encrypt, first divide the plaintext block into a left half and a right half. The algorithm has 8 rounds. In each round the right half is combined with some key material using function f and XORed with the left half to form the new right half. The original right half (before the round) becomes the new left half. After 8 rounds (don't switch the left and right halves after the eighth), the two halves are concatenated to form the ciphertext.

Function f is simple:

+   (1) Divide the 32-bit input into four 8-bit quarters: a, b, c, d.
(2) Divide the 16-bit subkey into two 8-bit halves: e, f.
(3) Process a through S-box 1, b through S-box 2, c through S-box 3, d through S-box 4, e through S-box 5, and f through S-box 6.
(4) XOR the six S-boxes outputs to get the 32-bit output.

Alternatively, the 32-bit input can be XORed with 32 bits of key, divided into four 8-bit quarters, processed through the S-boxes, and XORed out [7]. N rounds of this appears to be as secure as N+2 rounds of the other option.

The 16-bit subkey for each round is easily calculated from the 64-bit key. If $k_1, \dots, k_8$ are the 8 bits of key, then the subkeys for each are:

+   Round 1: $k_1, k_2$
Round 2: $k_3, k_4$
Round 3: $k_5, k_6$
Round 4: $k_7, k_8$
Round 5: $k_4, k_3$
Round 6: $k_2, k_1$
Round 7: $k_6, k_7$
Round 8: $k_8, k_5$

The strength of this algorithm lies in its S-boxes. CAST does not have fixed S-boxes, new ones are constructed for each application. Design criteria are in [10]; bent functions are the S-boxes columns, selected for a number of desirable S-box properties [see Section 14.10]. Once a set of S-boxes has been constructed for a given implementation of CAST, they are fixed for all time. The S-boxes are implementation-dependent, but not key-dependent.

It was shown in [10] that CAST is resistant to differential cryptanalysis and in [728] that CAST is resistant to linear cryptanalysis. There is no way to break CAST other than brute force.

Northern Telecom is using CAST in its Entrust security software package for Macintoshintos, PCs, and UNIX workstations. The particular S-boxes they chose are not public. The Canadian government is evaluating CAST as a new encryption standard. CAST is patent-pending.