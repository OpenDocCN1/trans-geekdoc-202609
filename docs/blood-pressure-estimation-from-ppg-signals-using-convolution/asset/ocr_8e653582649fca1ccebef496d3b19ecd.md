order in the low SNR regime [12]. Thus, (3) is regarded as a necessary and sufficient condition for achieving the capacity for the CSIR case up to second order. A signaling scheme with achievable rate C(γ) is called second-order optimal [12] when C(γ) is equal to the corresponding capacity up to second order (O(γ^{1+α}) for α ∈ (0,1]) in the low SNR regime. By definition, the EE of second-order-optimal schemes is equal to the optimum EE C_opt(γ)/γ up to O(γ^α) as γ → 0.

# C. Generalized Spatial Modulation

In GSM, the transmitter activates \tilde{M} transmit antennas \mathcal{M}_t \subset \mathcal{M}_{all} = {1,...,M} with |\mathcal{M}_t| = \tilde{M} in symbol period t, and send data symbols only from the activated antennas \mathcal{M}_t. Thus, the sparse vector x_{\mathcal{M}_t,t} \in \mathbb{C}^M transmitted in symbol period t satisfies x_{m,t} = (x_{\mathcal{M}_t,t})_m = 0 for all m \notin \mathcal{M}_t. We assume that {\mathcal{M}_t} are sampled from all possible subsets of \mathcal{M}_{all} with cardinality \tilde{M} uniformly and randomly for all t, and that {x_{\mathcal{M}_t,t}} are independent for all t. The covariance matrix \Sigma_{\mathcal{M}_t} = \mathbb{E}[x_{\mathcal{M}_t,t} x_{\mathcal{M}_t,t}^H] satisfies the constraint Tr(\Sigma_{\mathcal{M}_t}) \le 1 to fulfill the average power constraint. Furthermore, we assume that the complex data symbols {x_{m,t}} with finite fourth moments satisfy

\mathbb{E}[x_{m1,t}] = 0, \quad \mathbb{E}[x_{m1,t} x_{m2,t}] = 0, \quad \mathbb{E}[x_{m1,t}^* x_{m2,t} x_{m3,t}] = 0, \quad \mathbb{E}[x_{m1,t} x_{m2,t} x_{m3,t}^*] = 0, \quad (4)

# III. MAIN RESULTS

# A. Perfect CSI at the Receiver

We first analyze the coherent achievable rate C_{GSM}^{CSI}(γ; H) of the GSM for a fixed known channel matrix H. In Section III-A the channel matrix H is regarded as a deterministic matrix, so that conditioning with respect to H is omitted.

C_{GSM}^{CSI}(γ; H) = \frac{1}{T} \sum_{t=1}^{T} I(\mathcal{D}_t; y_t). \quad (6)

Since the mutual information I(\mathcal{D}_t; y_t) given H is independent of t, for notational convenience, we omit the time index t from all variables in Section III-A. The following theorem is obtained by evaluating (6) in the low SNR regime.

# Theorem 1: Suppose that the modulation scheme for the non-zero elements of x_{\mathcal{M}} satisfies the assumption (4). Then, for any \tilde{M} and any realization of the channel matrix H

C_{GSM}^{CSI}(γ; H) = γ Tr(H \mathbb{E}_{\mathcal{M}}[\Sigma_{\mathcal{M}}] H^H) - \frac{γ^2}{2} Tr\{ (H \mathbb{E}_{\mathcal{M}}[\Sigma_{\mathcal{M}}] H^H)^2 \} + o(γ^2). \quad (7)

Proof: See Appendix A.

# Corollary 1: Suppose that the modulation scheme for the non-zero elements of x_{\mathcal{M}} satisfies the assumption (4), and that the non-zero elements {x_{m,t}} are independent variables with average power \mathbb{E}[|x_{m,t}|^2] = \tilde{M}^{-1}. Then, for any number \tilde{M} of simultaneously activated antennas, the ergodic achievable rate C_{GSM}^{CSI}(γ) = \mathbb{E}_H[ C_{GSM}^{CSI}(γ; H) ] is given by

C_{GSM}^{CSI}(γ) = Nγ - \frac{N(M+N)}{2M} γ^2 + o(γ^2). \quad (8)

# B. No CSI

It is known that it is wasteful to spread the transmit power over time for the no CSI case. An energy-efficient scheme is flash signaling [14], in which data transmission is performed only in a part of all fading blocks to reduce the number of fading blocks to be estimated. Flash signaling concentrates the transmit power on a part of fading blocks. Thus, it should be regarded as power allocation over time.

We propose flash GSM as an energy-efficient scheme for the no CSI case. In flash GSM, transmission is performed only in δ(γ) fraction of all fading blocks. When transmission is active in a fading block, GSM with SNR γ' = γ/δ(γ) is used to satisfy the average power constraint over all fading blocks.