
## Step 1 and 2

Every agent $\mathcal{A}^{(k)}$ samples $B[t]$ trajectories $\{\tau[t, i]^{(k)}\}_{i=1}^{B[t]}$ using the policy $\boldsymbol{\theta}_0^{(t)}$, computes a gradient estimate $\mu_t^{(k)} \triangleq 1/B_t \sum_{i=1}^{B_t} g(\tau_{t,i}^{(k)} | \boldsymbol{\theta}_0^t)$ following equation [(14.4)](#Chp014_257-279_B9780443190377000235.xhtml#deq5) – step 3 – and sends $\mu_t^{(k)}$ back to the server – step 4.

## Steps 5 and 6

The server computes the batch gradient $\mu_t$ by averaging the received gradient estimates – step 7 – and updates the policy parameters $\boldsymbol{\theta}_0^{(t)}$ via the following semi-stochastic gradient – step 8 – according to SCSG optimization [\[41\]](#Chp014_257-279_B9780443190377000235.xhtml#br0205):

$$v_n^t \triangleq \frac{1}{b_t} \sum_{j=1}^{b_t} \left[ g(\tau_{n,j}^t | \boldsymbol{\theta}_n^t) - g(\tau_{n,j}^t | \boldsymbol{\theta}_0^t) \right] + \mu_t$$

in which $b_t$ trajectories are sampled *independently* by the server on a separate copy of the MDP $M$ and the number $N_t$ of optimization steps is sampled from a geometric distribution with the parameter $\frac{B_t}{B_t + b_t}$. The server then stores a new snapshot of the updated parameter, and the algorithm is repeated.

## The BR filter

[Fig. 14.3](#Chp014_257-279_B9780443190377000235.xhtml#f0020)(b) demonstrates the complete FedPG-BR framework, which is obtained by incorporating the Byzantine resilience filter ([Fig. 14.3](#Chp014_257-279_B9780443190377000235.xhtml#f0020)(c)) into the FedPG algorithm described above. After receiving all the gradients, the server applies the BR filter (step 7), which is designed based on the following assumptions: firstly, at any given iteration $t$, there are less than $K/2$ Byzantine agents; secondly, the gradient estimates sent by the good (non-Byzantine) agents should concentrate in a region containing the true analytical gradient defined in [(14.3)](#Chp014_257-279_B9780443190377000235.xhtml#deq4). In particular, the work of [\[26\]](#Chp014_257-279_B9780443190377000235.xhtml#br0130) has assumed that there exists a constant $\sigma$ such that $\|g(\tau | \boldsymbol{\theta}) - \nabla J(\boldsymbol{\theta})\| \le \sigma$ for any $\tau \sim p(\cdot | \boldsymbol{\theta})$ and any policy $\pi_{\boldsymbol{\theta}}$, which implies that the discrepancy between any two gradient estimates is at most $2\sigma$ in the Euclidean space. Therefore, the BR filter computes the pair-wise Euclidean distances of all gradients.

### 14.3.5 Theoretical and empirical results for FRL

The work of [\[26\]](#Chp014_257-279_B9780443190377000235.xhtml#br0130) has provided theoretical guarantees on the convergence of FedPG-BR:

**Theorem 14.2 (Informal)**

*The output of FedPG-BR*, $\widetilde{\boldsymbol{\theta}}$, *satisfies*

$$\mathbb{E}\left[ \|\nabla J(\widetilde{\boldsymbol{\theta}}_a)\|^2 \right] \le \frac{2\Psi\left[ J(\widetilde{\boldsymbol{\theta}}^*) - J(\widetilde{\boldsymbol{\theta}}_0) \right]}{T B^{1/3}} + \frac{8\sigma^2}{(1 - \alpha)^2 K B} + \frac{96\alpha^2 \sigma^2 V}{(1 - \alpha)^2 B}$$

*where $\alpha$ denotes the ratio of Byzantine agents such that $0 \le \alpha < 0.5$ and $\widetilde{\boldsymbol{\theta}}^*$ is a global maximizer of $J$; $\Psi$ is a smoothness constant and $V$ is another constant used to refine the concentration bound of the BR filter. For brevity, readers are referred to* [\[26\]](#Chp014_257-279_B9780443190377000235.xhtml#br0130) *for the detailed definitions of $\Psi$ and $V$.*

This theorem leads to many interesting insights, such as the sample complexity (of each agent in FedPG-BR) to reach an $\epsilon$-stationary point which is summarized in [Table 14.1](#Chp014_257-279_B9780443190377000235.xhtml#t0010). The table reveals that the sample complexity of FedPG-BR in the single-agent setting matches that of SVRPG derived by [\[77\]](#Chp014_257-279_B9780443190377000235.xhtml#br0385). In addition, when $K > 1$, $\alpha = 0$, [Table 14.1](#Chp014_257-279_B9780443190377000235.xhtml#t0010) shows that the total number of trajectories required by each agent is upper-bounded by $O(1/(\epsilon^{5/3} K^{2/3}))$. This result gives us the theoretical grounds to encourage more agents to participate in the federation since the number of trajectories each agent needs to sample decays at a rate of $O(1/K^{2/3})$. Furthermore, for a more realistic system where an $\alpha$-fraction ($\alpha > 0$) of the agents are Byzantine agents, the results in [Table 14.1](#Chp014_257-279_B9780443190377000235.xhtml#t0010) assure us that the total number of trajectories required by each agent will be increased by *only an additive term of* $O(\alpha^{4/3} / \epsilon^{5/3})$, the impact of which vanishes when $\alpha \to 0$.

**Table 14.1** Sample complexities of relevant works to achieve $\mathbb{E}\|\nabla J(\boldsymbol{\theta})\|^2 \le \epsilon$.

| Settings | Methods | Complexity |
| :--- | :--- | :--- |
| $K = 1$ | REINFORCE [\[74\]](#Chp014_257-279_B9780443190377000235.xhtml#br0370) | $O(1/\epsilon^2)$ |
| | GPOMDP [\[6\]](#Chp014_257-279_B9780443190377000235.xhtml#br0030) | $O(1/\epsilon^2)$ |
| | SVRPG [\[58\]](#Chp014_257-279_B9780443190377000235.xhtml#br0290) | $O(1/\epsilon^2)$ |
| | SVRPG [\[77\]](#Chp014_257-279_B9780443190377000235.xhtml#br0385) | $O(1/\epsilon^{5/3})$ |
| | **FedPG-BR** | $O(1/\epsilon^{5/3})$ |
| $K > 1, \alpha = 0$ | **FedPG-BR** | $O(\frac{1}{\epsilon^{5/3} K^{2/3}})$ |
| $K > 1, \alpha > 0$ | **FedPG-BR** | $O(\frac{1}{\epsilon^{5/3} K^{2/3}} + \frac{\alpha^{4/3}}{\epsilon^{5/3}})$ |
