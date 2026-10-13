
#### 8.2.2 Optimized near-isometric embedding

The easiest way to construct a matrix with RIP is to generate a random matrix. The work [292] proves that random matrix is of a very high possibility to satisfy RIP, yet not deterministic. Different from the random Bernoulli sampling matrix that the RIP is probabilistic, a data-driven sampling matrix can ensure the RIP of a finite given data points. One recent work in [289] proposed the **NuMax** framework to construct a near-isometric embedding matrix with deterministic RIP. Given a data set `X`, the NuMax produces an optimized continuous-valued embedding matrix `Φ` so that every pairwise distance vector `x_i - x_j` for `x_i, x_j ∈ X` can preserve its norm after embedding up to a given distortion tolerance `ε`.

Once the optimized NuMax sampling matrix `Φ_opt` is obtained, the signal acquisition `y = Φx` can be performed by multiplying the embedding matrix `Φ` with signal vector `x`. The conventional CMOS circuit-based data acquisition front end that performs real-valued embedding is shown in [Figure 8.3](#Chapter8.html#c08_fig3). The sampling circuit has two major components, the static random access memory (SRAM) memory that stores the embedding matrix and the multiplier-accumulators (MACs) that perform multiplication and addition. For an embedding matrix `Φ ∈ R^{M×N}` (`M < N`), in each cycle, `M` MACs multiply one element of input vector `x` with one column of `Φ`, and then add with previously accumulated results. Therefore, it requires `N` cycles to obtain the embedded signal `y`.

![image](images/PBPC0390-08-f03.jpg)

Figure 8.3 The embedding circuit by CMOS matrix--vector multiplier

As NuMax produces real-valued `Φ`, the precision of `Φ` substantially determines the hardware complexity. For example, a multiplier in MAC with 4-bit resolution, shown in [Figure 8.4](#Chapter8.html#c08_fig4)(a), requires 16 full adders. In fact, the number of full adders required generally quadratically depends on the precision of both `Φ` and `x`. For the typical precision of real-valued elements in sampling matrix, 16-bit ([Figure 8.1](#Chapter8.html#c08_fig1)) resolution may lead to as many as hundreds of full adders for each MAC, which makes the real-valued NuMax embedding less appealing for signal acquisition hardware mapping.

![image](images/PBPC0390-08-f04.jpg)

Figure 8.4 The implementation of (a) MAC with multiplier in 4-bit resolution for real-valued embedding matrix; (b) MAC for `{+1, -1}` embedding matrix; (c) MAC for `{+1, 0, -1}` embedding matrix with power optimization

### 8.3 Boolean embedding for signal acquisition front end

#### 8.3.1 CMOS-based Boolean embedding circuit

The mapping of a Boolean embedding matrix can eliminate the usage of multipliers. For a `{0, 1}` Boolean embedding matrix, the MAC only accumulates signal data when Boolean multiplicand is `1`. For a more general `{+1, -1}` Boolean matrix, the Boolean multiplicand indicates addition or subtraction for the signal data. That is to say, the required resources of full adders are only linearly depending on the precision of signal `x`. As such, the hardware resource can be significantly reduced.

Specifically for the `{+1, -1}` embedding matrix mapping, the multiplication by `-1` requires the calculation of 2's complement. The intuitive approach is illustrated in [Figure 8.4](#Chapter8.html#c08_fig4)(b). The `x` signal is `x` for multiplying `+1` and `~x` for multiplying `-1`. To obtain the 2's complement, the XOR logic is used to get the complement of each bit and the `C_in = 1` (carry 0) is applied as well. However, the 2's complement calculation close to input will incur substantial dynamic power for the combinational logic. Instead, the circuit diagram in [Figure 8.4](#Chapter8.html#c08_fig4)(c) first accumulates all data to be multiplied by `+1` and `-1` separately, and the subtraction is performed at the very last cycle. Therefore, the 2's complement circuit is only active every `N` cycles, which can greatly improve the power efficiency.

To be compatible with optimized sampling matrices such as Reed--Muller code [287, 288] and NuMax [289], SRAM block is required to store the matrix and provide reconfigurability. For non-optimized sampling matrices such as random Gaussian and Bernoulli, apart from storing the matrix in SRAM, the matrix can also be generated at runtime, which can improve hardware efficiency. In practice, the pseudo-random number generator (PRNG) is used [286, 290], which avoids the power-consuming SRAM arrays. As PRNG produces 0/1 sequences with a predetermined pattern, one of the issues for PRNG is the self-coherence. For example, an 8-bit per cycle PRNG has a period of 256 `N`, and when filling a `M×N` sampling matrix by rows with such 0/1 sequences, all rows of the matrix will be identical. This can be overcome by increasing the number of bits the PRNG produces per cycle at a cost of higher hardware complexity. With limited hardware resources, the pseudo-random numbers generated by PRNG usually lead to performance degradation of signal acquisition compared to stored random sampling matrix.

#### 8.3.2 ReRAM crossbar-based Boolean embedding circuit
