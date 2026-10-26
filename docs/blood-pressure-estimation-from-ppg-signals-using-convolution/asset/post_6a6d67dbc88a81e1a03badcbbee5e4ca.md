
order in the low SNR regime [12]. Thus, (3) is regarded as a necessary and sufficient condition for achieving the capacity for the CSIR case up to second order. A signaling scheme with achievable rate $C(\gamma)$ is called second-order optimal [12] when $C(\gamma)$ is equal to the corresponding capacity up to second order ($O(\gamma^{1+\alpha})$ for $\alpha \in (0,1]$) in the low SNR regime. By definition, the EE of second-order-optimal schemes is equal to the optimum EE $C_{\mathrm{opt}}(\gamma)/\gamma$ up to $O(\gamma^\alpha)$ as $\gamma \to 0$.

### C. Generalized Spatial Modulation

In GSM, the transmitter activates $\tilde{M}$ transmit antennas $\mathcal{M}_t \subset \mathcal{M}_{\mathrm{all}} = \{1,\ldots,M\}$ with $|\mathcal{M}_t| = \tilde{M}$ in symbol period $t$, and send data symbols only from the activated antennas $\mathcal{M}_t$. Thus, the sparse vector $x_{\mathcal{M}_t,t} \in \mathbb{C}^M$ transmitted in symbol period $t$ satisfies $x_{m,t} = (x_{\mathcal{M}_t,t})_m = 0$ for all $m \notin \mathcal{M}_t$. We assume that $\mathcal{M}_t$ are sampled from all possible subsets of $\mathcal{M}_{\mathrm{all}}$ with cardinality $\tilde{M}$ uniformly and randomly for all $t$, and that $x_{\mathcal{M}_t,t}$ are independent for all $t$. The covariance matrix $\Sigma_{\mathcal{M}_t} = \mathbb{E}[x_{\mathcal{M}_t,t} x_{\mathcal{M}_t,t}^H]$ satisfies the constraint $\operatorname{Tr}(\Sigma_{\mathcal{M}_t}) \le 1$ to fulfill the average power constraint. Furthermore, we assume that the complex data symbols $x_{m,t}$ with finite fourth moments satisfy

$$
\mathbb{E}[x_{m_1,t}] = 0, \quad \mathbb{E}[x_{m_1,t} x_{m_2,t}] = 0, \quad \mathbb{E}[x_{m_1,t}^* x_{m_2,t} x_{m_3,t}] = 0, \quad \mathbb{E}[x_{m_1,t} x_{m_2,t} x_{m_3,t}^*] = 0, \tag{4}
$$

## III. MAIN RESULTS

### A. Perfect CSI at the Receiver

We first analyze the coherent achievable rate $C_{GSM}^{CSI}(\gamma; H)$ of the GSM for a fixed known channel matrix $H$. In Section III-A the channel matrix $H$ is regarded as a deterministic matrix, so that conditioning with respect to $H$ is omitted.

$$
C_{GSM}^{CSI}(\gamma; H) = \frac{1}{T} \sum_{t=1}^{T} I(\mathcal{D}_t; y_t). \tag{6}
$$

Since the mutual information $I(\mathcal{D}_t; y_t)$ given $H$ is independent of $t$, for notational convenience, we omit the time index $t$ from all variables in Section III-A. The following theorem is obtained by evaluating (6) in the low SNR regime.

**Theorem 1:** Suppose that the modulation scheme for the non-zero elements of $x_{\mathcal{M}}$ satisfies the assumption (4). Then, for any $\tilde{M}$ and any realization of the channel matrix $H$,

$$
C_{GSM}^{CSI}(\gamma; H) = \gamma \operatorname{Tr}\left(H \mathbb{E}_{\mathcal{M}}[\Sigma_{\mathcal{M}}] H^H\right) - \frac{\gamma^2}{2} \operatorname{Tr}\left\{ \left(H \mathbb{E}_{\mathcal{M}}[\Sigma_{\mathcal{M}}] H^H\right)^2 \right\} + o(\gamma^2). \tag{7}
$$

*Proof:* See Appendix A.

**Corollary 1:** Suppose that the modulation scheme for the non-zero elements of $x_{\mathcal{M}}$ satisfies the assumption (4), and that the non-zero elements $x_{m,t}$ are independent variables with average power $\mathbb{E}[|x_{m,t}|^2] = \tilde{M}^{-1}$. Then, for any number $\tilde{M}$ of simultaneously activated antennas, the ergodic achievable rate $C_{GSM}^{CSI}(\gamma) = \mathbb{E}_H[ C_{GSM}^{CSI}(\gamma; H) ]$ is given by

$$
C_{GSM}^{CSI}(\gamma) = N\gamma - \frac{N(M+N)}{2M} \gamma^2 + o(\gamma^2). \tag{8}
$$

### B. No CSI

It is known that it is wasteful to spread the transmit power over time for the no CSI case. An energy-efficient scheme is flash signaling [14], in which data transmission is performed only in a part of all fading blocks to reduce the number of fading blocks to be estimated. Flash signaling concentrates the transmit power on a part of fading blocks. Thus, it should be regarded as power allocation over time.

We propose flash GSM as an energy-efficient scheme for the no CSI case. In flash GSM, transmission is performed only in $\delta(\gamma)$ fraction of all fading blocks. When transmission is active in a fading block, GSM with SNR $\gamma' = \gamma/\delta(\gamma)$ is used to satisfy the average power constraint over all fading blocks.

In Section III-B averaging over the channel matrix $\boldsymbol{H}$ is considered, whereas $\boldsymbol{H}$ was fixed in Section III-A. Note that conditioning with respect to $\boldsymbol{H}$ is not omitted in Section III-B.

We define the achievable rate $C_{\mathrm{FGSM}}(\gamma)$ of the flash GSM for the MIMO channel (1) with no CSI as

$$
C_{\mathrm{FGSM}}(\gamma)=\frac{\delta(\gamma)}{T}I\left(\mathcal{D}_t:\text{ all }t;\boldsymbol{Y}\right). \tag{9}
$$

**Theorem 2:** Suppose that $\boldsymbol{x}_{\mathcal{M},t}$ satisfies all assumptions in Corollary 1. For any $\alpha\in(0,1]$, the achievable rate $C_{\mathrm{FGSM}}(\gamma)$ of the flash GSM with $\delta(\gamma)=\gamma^{-\alpha}$ for no CSI is given by

$$
C_{\mathrm{FGSM}}(\gamma)=N\gamma-\frac{N(M+N)}{2M}\gamma^{1+\alpha}+o(\gamma^{1+\alpha}), \tag{10}
$$

if there is some $\epsilon>0$ such that $T$ satisfies (3).

*Proof:* See Appendix B.

Comparing (2) and (10) implies that the flash GSM is second-order optimal for the MIMO channel (1) with no CSI.

## IV. NUMERICAL RESULTS

In order to verify Corollary 1, numerical results are presented for QPSK GSM. Fig. 1 shows the ergodic achievable rates $C_{\mathrm{GSM}}^{\mathrm{CSIR}}(\gamma)\triangleq\mathbb{E}_{\boldsymbol{H}}[C_{\mathrm{GSM}}^{\mathrm{CSI}}(\gamma;\boldsymbol{H})]$ of the GSM for the CSIR case—estimated by Monte Carlo integration of (6)—as well as its low SNR approximation (8). For comparison, the channel capacity is also plotted.

![](img/917df36c69e658161399bf08d818da1c_2_0.png)

Fig. 1. Ergodic achievable rate versus SNR $\gamma$ for QPSK GSM over the i.i.d. Rayleigh fading MIMO channel with CSIR. $M=8$, $N=2$, and $T=1$.

The low SNR approximation (8) is accurate for $\gamma<-5$ dB. In the same low SNR regime, the achievable rates of the GSM are indistinguishable from the capacity for all $\tilde{M}$, as predicted in Corollary 1. As the maximum transmission rate $R=2\tilde{M}+\log_2\binom{M}{\tilde{M}}$ in bits increases, the achievable rates get closer to the capacity in the moderate SNR regime, while they are limited to below $R$ in the high SNR regime.

## V. CONCLUSION

The main results of this letter are twofold: One is that QPSK GSM is second-order optimal for the i.i.d. Rayleigh block-fading MIMO channel with CSIR, regardless of the number of simultaneously activated transmit antennas. The other is that, under a condition for coherence time, flash GSM with QPSK is second-order optimal for the no CSI case. The conclusion of this letter is that single-RF MIMO systems with QPSK are practically the best option in terms of the information-theoretical EE under rich scattering environment.

An interesting future work is to construct precoded GSM for correlated MIMO channels with CSIR or for MIMO channels with full CSI. The low SNR approximation of the achievable rate in Theorem 1 can be used as an objective function for designing energy-efficient precoders in the low SNR regime. The maximization of the objective function over the input covariance matrices is concave, so that the precoder-design problem may be solved efficiently.

## APPENDIX A

### PROOF OF THEOREM 1

We shall evaluate $I(\boldsymbol{D};\boldsymbol{y})=h(\boldsymbol{y})-h(\boldsymbol{y}|\boldsymbol{D})$ in nats. From (5), $h(\boldsymbol{y}|\boldsymbol{D})$ given $\boldsymbol{H}$ is equal to the differential entropy of the AWGN vector $\gamma^{-1/2}\boldsymbol{w}$ [15], i.e. $h(\boldsymbol{y}|\boldsymbol{D})=N\ln(\pi e\gamma^{-1})$.

The differential entropy $h(\boldsymbol{y})$ given $\boldsymbol{H}$ is defined as

$$
h(\boldsymbol{y})=-\int p(\boldsymbol{y}|\boldsymbol{H})\ln p(\boldsymbol{y}|\boldsymbol{H})\,d\boldsymbol{y}, \tag{11}
$$

with

$$
p(\boldsymbol{y}|\boldsymbol{H})=\mathbb{E}_{\mathcal{D}}\left[p(\boldsymbol{y}|\boldsymbol{H},\mathcal{D})\right], \tag{12}
$$

where $p(\boldsymbol{y}|\boldsymbol{H},\mathcal{D})$ represents the MIMO channel (1) with the GSM in a symbol period,

$$
p(\boldsymbol{y}|\boldsymbol{H},\mathcal{D})=\frac{1}{(\pi\gamma^{-1})^N}e^{-\gamma\|\boldsymbol{y}-\boldsymbol{H}\boldsymbol{x}_{\mathcal{M}}\|^2}. \tag{13}
$$

Extracting a $\mathcal{D}$-independent factor from (13) yields

$$
p(\boldsymbol{y}|\boldsymbol{H})=\frac{1}{(\pi\gamma^{-1})^N}e^{-\gamma\|\boldsymbol{y}\|^2}G(\sqrt{\gamma}\boldsymbol{y};\gamma), \tag{14}
$$

with

$$
G(\boldsymbol{u};\gamma)=\mathbb{E}_{\mathcal{D}}\left[\exp\left\{2\sqrt{\gamma}\,\Re\left[(\boldsymbol{H}\boldsymbol{x}_{\mathcal{M}})^H\boldsymbol{u}\right]-\gamma\|\boldsymbol{H}\boldsymbol{x}_{\mathcal{M}}\|^2\right\}\right]. \tag{15}
$$

Substituting (14) into (11) and using the change of variables $\boldsymbol{u}=\sqrt{\gamma}\boldsymbol{y}$, we obtain

$$
h(\boldsymbol{y})=N\ln(\pi e\gamma^{-1})+\gamma\mathbb{E}_{\mathcal{D}}\left[\|\boldsymbol{H}\boldsymbol{x}_{\mathcal{M}}\|^2\right]+H(\gamma), \tag{16}
$$

with

$$
H(\gamma)=-\mathbb{E}_{\boldsymbol{u}}\left[G(\boldsymbol{u};\gamma)\ln G(\boldsymbol{u};\gamma)\right], \tag{17}
$$

where $\boldsymbol{u}\sim\mathcal{CN}(\boldsymbol{0},I_N)$ is regarded as a standard complex Gaussian random vector.

The first term on the RHS of (16) is equal to the differential entropy $h(\boldsymbol{y}|\mathcal{D})$. Furthermore, the second term reduces to the first term on the RHS of (7). Thus, it is sufficient to prove

$$
H(\gamma)=-\frac{\gamma^2}{2}\operatorname{Tr}\left\{\left(\boldsymbol{H}\mathbb{E}_{\mathcal{M}}[\boldsymbol{\Sigma}_{\mathcal{M}}]\boldsymbol{H}^H\right)^2\right\}+o(\gamma^2). \tag{18}
$$

We follow [4] to expand (17) with respect to $\sqrt{\gamma}$ up to fourth order in the low SNR limit $\gamma\to0$. Although the derivation is omitted, as a natural generalization of [4], under the assumption (4) we arrive at

$$
H(\gamma)=-\gamma\mathbb{E}_{\boldsymbol{u}}[a_1(\boldsymbol{u})]-\gamma^2\mathbb{E}_{\boldsymbol{u}}\left[a_2(\boldsymbol{u})+\frac{a_1(\boldsymbol{u})^2}{2}\right]+o(\gamma^2). \tag{19}
$$
