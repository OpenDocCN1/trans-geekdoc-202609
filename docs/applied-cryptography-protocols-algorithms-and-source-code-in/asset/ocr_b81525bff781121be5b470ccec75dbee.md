# 16.4 Stream Ciphers Using LFSRs 383

Even though this scheme is more complex than the Geffe generator, the same kind of correlation attack is possible. I don't recommend this generator.

# Jennings Generator

This scheme uses a multiplexer to combine two LFSRs [778,779,780]. The multiplexer, controlled by LFSR-1, selects 1 bit of LFSR-2 for each output bit. There is also a function that maps the output of LFSR-2 to the input of the multiplexer (see Figure 16.8).

The key is the initial state of the two LFSRs and the mapping function. Although this generator has great statistical properties, it fails to Ross Anderson's meet-in-the-middle consistency attack [39] and the linear consistency attack [1638.442]. Don't use this generator.

# Beth-Pier Stop-and-Go Generator

This generator, shown in Figure 16.9, uses the output of one LFSR to control the clock of another LFSR [151]. The clock input of LFSR-2 is controlled by the output of LFSR-1, so that LFSR-2 can change its state at time $t$ only if the output of LFSR-1 was at time $t-1$.

No one has been able to prove results about this generator's linear complexity in the general case. However, it falls to a correlation attack [1639].

# Alternating-Stop-Go Generator

This generator uses three LFSRs of different length. LFSR-2 is clocked when the output of LFSR-1 is 1, LFSR-3 is clocked when the output of LFSR-1 is 0. The output of the generator is the XOR of LFSR-2 and LFSR-3 [see Figure 16.10] [673].

This generator has a long period and large linear complexity. The authors found a correlation attack against LFSR-1, but it does not substantially weaken the generator. There have been other attempts at keystream generators along these lines [1534,1574,1477].

![](bbox=[0.147, 0.653, 0.603, 0.88])

Figure 16.7 Generalized Geffe generator.