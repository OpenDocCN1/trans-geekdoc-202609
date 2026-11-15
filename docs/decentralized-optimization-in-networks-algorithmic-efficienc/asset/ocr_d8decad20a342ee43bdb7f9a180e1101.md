**Lemma 5.2.** [49] Considering the definition of $\Pi_{\Omega}^h(\cdot)$ given in Eq. (5.4), for arbitrary vectors $v, u \in \mathbb{R}^m$ and a positive step-size $\alpha$, the following holds true:

$$
\|\Pi_{\Omega}^h(v, \alpha) - \Pi_{\Omega}^h(u, \alpha)\| \le \alpha \|v - u\|.
$$


Define $\mathcal{H}_{\Omega}^h(v, \alpha)$ as a conjugate-type function applicable to any vector $v$ belonging to $\mathbb{R}^m$ and a positive step-size $\alpha > 0$, in which

$$
\mathcal{H}_{\Omega}^h(v, \alpha) = \sup_{u \in \Omega} \left\{ \langle v, u \rangle - \frac{1}{\alpha} h(u) \right\}.
$$


Based on the aforementioned definition, we move forward to establish a crucial lemma that will validate our primary results.

**Lemma 5.3.** [54,55] Bearing in mind the definitions of $\Pi_{\Omega}^h(\cdot)$ and $\mathcal{H}_{\Omega}^h(\cdot)$, for any vectors $v$ and $u$ contained in $\mathbb{R}^m$ and step-size $\alpha > 0$, the following apply:
a) $\nabla \mathcal{H}_{\Omega}^h(-v, \alpha) = \Pi_{\Omega}^h(v, \alpha)$ and $\|\nabla \mathcal{H}_{\Omega}^h(-v, \alpha) - \nabla \mathcal{H}_{\Omega}^h(-u, \alpha)\| = \|\Pi_{\Omega}^h(v, \alpha) - \Pi_{\Omega}^h(u, \alpha)\| \le \alpha \|v - u\|$;
b) $\mathcal{H}_{\Omega}^h(-v - u, \alpha) \le \mathcal{H}_{\Omega}^h(-v, \alpha) - \langle \nabla \mathcal{H}_{\Omega}^h(-v, \alpha), u \rangle + (\alpha/2)\|u\|^2$.

**Remark 5.4.** Based on the findings presented in [56], it can be deduced that the dual of the Euclidean norm remains the Euclidean norm itself. During our research, we intended to use both the specified norm and its dual for theoretical validations. However, for the sake of simplicity, we consistently applied the Euclidean norm in our subsequent theoretical explorations. Nevertheless, similar validations can be obtained for various other norms. Furthermore, numerous studies [28,29,44,55] have adopted the Euclidean norm for theoretical examinations. Despite the fact that utilizing a general norm and its dual would have been more suitable, this variation did not alter the ultimate theoretical results.

# ## 5.4.2 Main results

In this subsection, to effectively demonstrate the performance of Algorithm 1, we initially present a vital lemma regarding the maximum limit of the consensus error $\mathbb{E}[\max_{i \in \mathcal{V}} \|z_{i,k} - \bar{z}_k\|]$, which plays a substantial role in shaping our primary findings. Subsequently, we establish our main outcome by determining the upper bound of regret.

By employing the additional vector $\bar{z}_k = \sum_{i=1}^n \pi_i z_{i,k}$, one obtains

$$
\bar{z}_{k+1} = \sum_{i=1}^n \pi_i z_{i,k+1} = \sum_{i=1}^n \pi_i (\sum_{j=1}^n A_{ij} (z_{j,k} + y_{j,k}) + \frac{g_{i,k}}{y_{ii,k}})
= \bar{z}_k + \sum_{i=1}^n \pi_i y_{i,k} + \sum_{i=1}^n \pi_i \frac{g_{i,k}}{y_{ii,k}},
\tag{5.10}
$$