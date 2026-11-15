# 1.4.1 Auxiliary results

It is noteworthy that the matrix sequence $\{W^t\}$ is both independent and identically distributed in accordance with Assumption 1.2. Then, the subsequent lemma is presented as follows.

**Lemma 1.1.** [32] Given that Assumption 1.2 is valid, we can deduce the following: (i) For each $W^t$ where $t \ge 1$, it possesses row-stochastic properties. Additionally, the corresponding expected matrix denoted as $\tilde{W} = E[W^t] = [\tilde{W}_{ij}] \in \mathbb{R}^{n \times n}$, exhibits row-stochastic characteristics. (ii) There exists a positive constant $\bar{\tau}$ such that $\forall i, j \in \mathcal{V}$, if $\tilde{W}_{ij} > 0$, then $\tilde{W}_{ij} > \bar{\tau}$. (iii) There exists a vector $\pi = [\pi_1, \dots, \pi_n]^T \in \mathbb{R}^n (\pi_i > 0, \forall i \in \mathcal{V})$ of $\tilde{W}$ satisfying that $\lim_{t \to \infty} (\tilde{W})^t = 1_n \pi^T, \pi^T \tilde{W} = \pi^T, \pi^T 1_n = 1$.

Let $E_i^t = \{i \in \{i^t, j^t\}\}$ denote the event that node $i$ performs an update at time $t$. We introduce the notation $\eta_i$ to represent the likelihood of event $E_i^t$, and it is given by $\eta_i = (1/n) + (1/n) \sum_{j \in \mathcal{N}_i^{in}} \kappa_{ij}, \forall i \in \mathcal{V}$. Here, $0 < \kappa_{ij} < 1$ signifies the probability that node $i$ is chosen by its incoming neighbor $j$ for communication. Then, we derive the following conclusions regarding the step-size $\alpha_i^t$, for all $t \ge 1$ and $i$ belonging to the set $V$.

**Lemma 1.2.** [30] Let the scalar $\varepsilon$ satisfy $0 < \varepsilon < 1/2$. Consequently, there exists a sufficiently large $\hat{t} = \hat{t}(\varepsilon, n)$ that ensures that a.s. for all $t \ge \hat{t}$ and $i \in \mathcal{V}$,

$\alpha_i^t \leq \frac{\alpha_1}{t}, (\alpha_i^t)^2 \leq \frac{\alpha_2}{t^2}, \text{and } |\alpha_i^t - \frac{1}{t\eta_i}| \leq \frac{\alpha_3}{t^{3/2-\epsilon}},$

where $\alpha_1, \alpha_2, \alpha_3$ are three distinct positive constants that are related to $n$ and the probability $\kappa_{ij}$.

Define $\mathcal{F}^t$ to be the $\sigma$-algebra that captures the entire historical record of the algorithm up until time $t, \forall t \ge 1$,

$\mathcal{F}^t = \{p_i^0: i \in \mathcal{V}\} \cup \{i^\ell, j^\ell: i \in \{i^\ell, j^\ell\}, 1 \le \ell \le t\},$

with $\mathcal{F}^0 = \{p_i^0: i \in \mathcal{V}\}$. Assuming $\{\Omega, \mathcal{F}, \mathcal{P}\}$ constitutes a probability space, and $\mathcal{F}^0 \subset \mathcal{F}^1 \subset \cdots$ denotes a sequence of $\sigma$-algebra of $\mathcal{F}$, we proceed to present the following convergence results pertaining to supermartingales with respect to these random variables.

**Lemma 1.3.** [40] For each $t \ge 0$, consider the sequences $\{v^t\}, \{u^t\}, \{q^t\}, \text{and } \{c^t\}$ of non-negative random variables. These variables are all measurable with respect to $\mathcal{F}^t$, adhering to the following conditions:

$\mathbb{E}[v^{t+1} | \mathcal{F}^t] \le (1+q^t)v^t - u^t + c^t \text{ a.s.},$

where $\mathcal{F}^t$ is the collection of $v^0, \dots, v^t, u^0, \dots, u^t, q^0, \dots, q^t, \text{and } c^0, \dots, c^t$. Given that $\sum_{t=0}^\infty q^t < \infty \text{ and } \sum_{t=0}^\infty c^t < \infty \text{ a.s., then we have } \lim_{t \to \infty} v^t = v \text{ for a random variable } v \ge 0 \text{ a.s., and } \sum_{t=0}^\infty u^t < \infty \text{ a.s.}$