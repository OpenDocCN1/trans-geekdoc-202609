# Geffe Generator

This keystream generator uses three LFSRs, combined in a nonlinear manner (sec Figure 16.6) [606]. Two of the LFSRs are inputs to a multiplexer, and the third LFSR controls the output of the multiplexer. If $a_1, a_2$ and $a_3$ are the outputs of the three LFSRs, the output of the Geffe generator can be described by:

```
b = (a_1 \wedge a_2) \oplus (\neg a_1 \wedge a_3)
```

If the LFSRs have lengths $n_1, n_2$ and $n_3$, respectively, then the linear complexity of the generator is

```
|n_1 + 1|n_2 + n_3
```

The period of the generator is the least common multiple of the periods of the three generators. Assuming the degrees of the three primitive feedback polynomials are relatively prime, the period of this generator is the product of the periods of the three LFSRs.

Although this generator looks good on paper, it is cryptographically weak and falls to a correlation attack [829,1638]. The output of the generator equals the output of LFSR-2 75 percent of the time. If the feedback taps are known, you can guess the number of times the output of the LFSR-2 agrees with the output of the generator. If you guessed wrong, the two sequences will agree about 50 percent of the time; if you guessed right, the two sequences will agree about 75 percent of the time.

Similarly, the output of the generator equals the output of LFSR-3 about 75 percent of the time. With those correlations, the keystream generator can be easily cracked. For example, if the primitive polynomials only have three terms each, and the largest LFSR is of length $n$, it only takes a segment of the output sequence $5n$-bits to reconstruct the internal states of all three LFSRs [1639].

# Generalized Geffe Generator

Instead of choosing between two LFSRs, this scheme chooses between $k$ LFSRs, as long as $k$ is a power of 2. There are $k+1$ LFSRs total (see Figure 16.7). LFSR-1 must be clocked $k$ times faster than the other $k$ LFSRs.

![](bbox=[0.176, 0.712, 0.545, 0.88])

Figure 16.6 Geffe generator.