# CHAPTER 16 Pseudo-Random-Sequence Generators

Cascades are a cool idea: They are conceptually very simple and they can be used to generate sequences with huge periods, linear complexities, and good statistical properties. They are vulnerable to an attack lock-in [640]. This is a technique by which a cryptanalyst reconstructs the input to the last shift register in the cascade, then proceeds to break the cascade register by register. This is a serious problem in some situations and weakens the key length of the algorithm, but precautions can be taken to minimize the attack.

Further analysis has indicated that the sequence approaches random as k gets larger [637,638,642,639]. Based on recent attacks on short Gollmann cascades [1063], I recommend using a k of at least 15. You're better off using more LFSRs of shorter length than fewer LFSRs of longer length.

# Shrinking Generator

The shrinking generator [378] uses a different form of clock control than the previous generators. Use two LFSRs: LFSR-1 and LFSR-2. Clock both of them. If the output of LFSR-1 is 1, then the output of the generator is LFSR-2. If the output of LFSR-1 is 0, discard both bits, clock both LFSRs, and try again.
This is simple, reasonably efficient, and looks secure. If the feedback polynomials are sparse, the generator is vulnerable, but no other problems have been found. Even so, it's new. One implementation is that the output rate is not regular, if LFSR-1 has a long string of zeros then the generator outputs nothing. The authors suggest buffering to solve this problem [378]. Practical implementation of the shrinking generator is discussed in [901].

# Self-Shrinking Generator

The self-shrinking generator [1050] is a variant of the shrinking generator. Instead of using two LFSRs, use pairs of bits from a single LFSR. Clock a LFSR twice. If the first bit in the pair is 1, the output of the generator is the second bit. If the first bit is 0, discard both bits and try again. While the self-shrinking generator requires about half the memory space as the shrinking generator, it is also half the speed.
While the self-shrinking generator also seems secure, it has some unexplained behavior and unknown properties. This is a very new generator, give it some time.

![](bbox=[0.166, 0.773, 0.693, 0.872])

Figure 16.16 Gollmann cascade.