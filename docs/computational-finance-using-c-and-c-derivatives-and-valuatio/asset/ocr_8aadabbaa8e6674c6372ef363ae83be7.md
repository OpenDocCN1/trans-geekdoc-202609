# TABLE 5.5 The Pricing Errors for an American Call Option Computed by a Standard Binomial Lattice, a BBS Lattice, and also a BSSR Lattice. The Pricing Error is Defined as Estimated Value – Accurate Value, 16.1697, Was Obtained by using a 600-step Standard Binomial Lattice. The Option Parameters used were T = 1.0, S = 105.0, E = 105.0, r = 0.1, q = 0.02, and σ = 0.3

| | Standard | BBS lattice | BSSR lattice |
|---|---|---||
| 20 | -1.5075e-002 | 3.6187e-002 | 1.2754e-002 |
| 30 | -1.0057e-001 | 2.4526e-002 | 8.6771e-003 |
| 40 | -7.5382e-002 | 1.8612e-002 | 6.6361e-003 |
| 50 | -6.0244e-002 | 1.5036e-002 | 5.4109e-003 |
| 60 | -5.0141e-002 | 1.2639e-002 | 4.5939e-003 |
| 70 | -4.2919e-002 | 1.0922e-002 | 4.0103e-003 |
| 80 | -3.7499e-002 | 9.6320e-003 | 3.5725e-003 |
| 90 | -3.3282e-002 | 8.6236e-003 | 3.3230e-003 |
| 100 | -2.9908e-002 | 7.8171e-003 | 2.9596e-003 |
| 110 | -2.7146e-002 | 7.1565e-003 | 2.7367e-003 |
| 120 | -2.4844e-002 | 6.6053e-003 | 2.5509e-003 |
| 130 | -2.2896e-002 | 6.1385e-003 | 2.3938e-003 |
| 140 | -2.1226e-002 | 5.7382e-003 | 2.2590e-003 |
| 150 | -1.9778e-002 | 5.3900e-003 | 2.1423e-003 |
| 160 | -1.8511e-002 | 5.0869e-003 | 2.0401e-003 |
| 170 | -1.7393e-002 | 4.8186e-003 | 1.9500e-003 |
| 180 | -1.6399e-002 | 4.5799e-003 | 1.8698e-003 |
| 190 | -1.5510e-002 | 4.3663e-003 | 1.7981e-003 |
| 200 | -1.4710e-002 | 4.1740e-003 | 1.7336e-003 |

One method of avoiding these limitations is through the use of finite-difference grids. Although this approach no longer has the probabilistic interpretation of the binomial lattice, it has the following advantages:

+   * Fewer steps are required to ensure numerical stability.
* There is complete control over the placement of grid lines and their associated grid nodes.