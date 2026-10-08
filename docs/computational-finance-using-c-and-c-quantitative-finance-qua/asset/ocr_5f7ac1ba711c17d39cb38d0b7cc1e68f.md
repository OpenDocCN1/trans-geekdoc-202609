# Single asset American options

# Richardson extrapolation: American call

![](bbox=[0.176, 0.117, 0.856, 0.463])

**Figure 5.4** The error in the estimated value, est_val, of an American call, using a BSSR binomial lattice. The parameters used were: $T = 1.0, S = 105.0, E = 105.0, r = 0.1, q = 0.02, \sigma = 0.3$. The accurate value (acc_val) was 16.1697, and was computed using a 6000 step standard binomial lattice. The error in the estimated value was obtained as est_val - acc_val.

time step BBS lattice is $5.0869e-003$, while for an 80 time step BSSR lattice is $3.5725e-003$; in Table 5.6 the error for an 80 time step BBS lattice is $6.3858e-003$, and for a 40 time step BSSR lattice is $3.5725e-003$.

# 5.4 Grid methods for vanilla options

# 5.4.1 Introduction

In Section 5.3 we discussed the use of binomial lattice methods for valuing both European and American options. The lattice methods we have described the advantage that they are fairly easy to implement and can value simple options, such as vanilla puts and calls, reasonably accurately. The use of up and down jump probabilities at the lattice nodes is also an appealing feature, since they are directly to the stochastic process which is being modelled. However, lattice techniques have the following drawbacks:

+   - They require small time steps to ensure numerical stability