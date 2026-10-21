we get a description of the Itô process in terms of the original random variable S(t, w) rather than infinitesimal differences (differential form), as in equation (27.6). Suppose that a stochastic process is given by equation (27.6) and that a new process Y(t, w) is formed by letting Y(t, w) = u[t, S(t, w)]. Because stochastic calculus studies random changes in continuous time, the question arises: what is dY(t, w)? This question is important for both mathematical analysis and finance. The answer is given in Itô's lemma.

# Itô's Lemma.

Consider the non-random continuous function u(t, S) : [0, ∞) × R → R and suppose that it has continuous partial derivatives u_t, u_S, and u_SS.

Let

Y(t, w) = u[t, S(t, w)]  (27.13)

with

dS(t, w) = μ[t, S(t, w)] dt + σ[t, S(t, w)] dZ(t, w).  (27.14)

Then the process Y(t, w) has a differential given by

dY(t, w) = {u_t[t, S(t, w)] + u_S[t, S(t, w)] μ[t, S(t, w)] + ½ u_SS[t, S(t, w)] σ²[t, S(t, w)]} dt + u_S[t, S(t, w)] σ[t, S(t, w)] dZ(t, w).  (27.15)

The proof is presented in Gikhman and Skorokhod (1969: 387–389), and extensions of this lemma may be found in Arnold (1974: 90–99). Also, a heuristic derivation of the lemma can be found in Baxter and Rennie (1996) and Wilmott (2001). Here, the analysis is limited to three remarks.

+   1. Itô's lemma is a useful result because it allows the computation of stochastic differentials of arbitrary functions having as an argument a stochastic process that itself is assumed to possess a stochastic differential. In this respect, Itô's formula is as useful as the chain rule of ordinary calculus.
+   2. Given a stochastic process S(t, w) with respect to a given Wiener process Z(t, w), and letting Y(t, w) = u[t, S(t, w)] be a new process, Itô's formula gives the stochastic differential of Y(t, w), where dY(t, w) is given with respect to the same Wiener process, that is, both processes have the same source of uncertainty.
+   3. An inspection of the proof of Itô's lemma reveals that it consists of an application of Taylor's theorem of advanced calculus and several probabilistic arguments to establish the convergence of certain quantities