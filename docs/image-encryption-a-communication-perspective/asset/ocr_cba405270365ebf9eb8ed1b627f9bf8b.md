![](bbox=[0.12, 0.08, 0.95, 0.42])

Figure 6.4 Operation of the SPN.

![](bbox=[0.25, 0.55, 0.9, 0.78])

Figure 6.5 The bit permutation in the SPN.

the plaintext will affect at least one bit in each block of the input to the encryption algorithm, and the diffusion mechanism in the encryption algorithm will propagate this change through each block.

From Figure 6.6, we can see that if a change takes place in an SPN block (S_j), all the network blocks from Q'_{L-i+1} to Q'_L will be affected, where L is the number of network blocks. The output odd-number