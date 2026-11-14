![](bbox=[0.32, 0.09, 0.69, 0.32])

Figure 29.20: The BATnet DBN. The transient nodes are only shown for the second slice, to minimize clutter. The dotted lines are used to group related variables. Used with kind permission of Daphne Koller.

fixed), rather it is a network representation of a dynamical system.) A DBN can be considered as a natural generalization of an HMM. An example is shown in Figure 29.20, which is a DBN designed to monitor the state of a simulated autonomous car known as the “Bayesian automated taxi”, or “BATmobile” [For+95]. To define the model, you just need to specify the structure of the first time-slice, the structure between two time-slices, and the form of the CPDs. For details, see [KF09a].

# 29.5.6 Changepoint detection

In this section, we discuss changepoint detection, which is the task of detecting when there are “abrupt” changes in the distribution of the observed values in a time series. We focus on the online case. (For a review of offline methods to this problem, see e.g., [AC17; TOV18]. (See also [BW20] for a recent empirical evaluation of various methods, focused on the 1d time series case.) The methods we discuss can (in principle) be used for high-dimensional time series segmentation. Our starting point is the hidden semi-Markov models (HSMM) discussed in Section 29.5.1. This is like an HMM in which we explicitly model the duration spent in each state. This is done by augmenting the latent state z_t with a duration variable d_t which is initialized according to a duration distribution, d_t ~ D_z_t(.), and which then counts down to 1. An alternative approach is to add a variable r_t{0, 1, ...} which encodes the run length for the current state; this starts at 0 whenever a new segment is created, and then counts up by one at each step. The transition dynamics is specified by

```
$$p(r_t|r_{t-1}) = \begin{cases} H(r_{t-1} + 1) & \text{if } r_t = 0 \\ 1 - H(r_{t-1} + 1) & \text{if } r_t = r_{t-1} + 1 \\ 0 & \text{otherwise} \end{cases} \quad (29.63)$$
```