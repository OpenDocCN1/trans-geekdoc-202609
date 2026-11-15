a) There exist positive constants \( C \) and \( \alpha \in (0, 1) \) such that the absolute difference between \( r_{s,t}^{i,j} \) and \( \theta_t^j \) is upper-bounded by \( C\varsigma^{s-t} \). Furthermore, the transpose of \( \theta_t \) is equal to the product of the transpose of \( \theta_{t+1} \) and the matrix \( R_t \).

b) Let \( \{\mu_t^i\}_{t \ge 1} \) denote the sequence derived from Eq. (6.9). Subsequently, for a pre-determined time span \( T \), it holds that the magnitude of the difference between \( \frac{\mu_{t+1}^i}{n} \) and \( \theta_{t+1}^i \) is bounded above by \( Q\lambda^{T-t-1} \). Additionally, the elements \( \mu_{t+1}^i \) are confined within the interval \( [\varpi^{-1}, \varpi] \), where \( \varpi \) and \( \omega \) are positive constants.

Prior to presenting the subsequent pivotal lemma, we define a function of the conjugate type, denoted as \( \mathcal{G}_\Omega^\varphi(u, \beta) \), which pertains to any vector \( u \in \mathbb{R}^m \) and a positive step-size parameter \( \beta \), where

\(\mathcal{H}_\Omega^\varphi(v, \alpha) = \sup_{u \in \Omega} \{ \langle v, u \rangle - \frac{1}{\alpha} \phi(u) \}.\)

Subsequently, we formulate a pivotal lemma to underpin our primary findings, the verification of which can be traced back to [47].

**Lemma 6.3.** [47] Drawing upon the definitions of \( \Pi_\Omega^\varphi(\cdot) \) and \( \mathcal{G}_\Omega^\varphi(\cdot) \), we can assert that for any \( v, u \in \mathbb{R}^m \) and a positive \( \alpha \), the following relationships hold:

+   a) \( \nabla \mathcal{H}_\Omega^\varphi(-v, \alpha) = \Pi_\Omega^\varphi(v, \alpha) \) and \( ||\nabla \mathcal{H}_\Omega^\varphi(-v, \alpha) - \nabla \mathcal{H}_\Omega^\varphi(-u, \alpha)|| = ||\Pi_\Omega^\varphi(v, \alpha) - \Pi_\Omega^\varphi(u, \alpha)|| \le \alpha ||v - u|| \).

+   b) \( \mathcal{H}_\Omega^\varphi(-v - u, \alpha) \le \mathcal{H}_\Omega^\varphi(-v, \alpha) - \langle \nabla \mathcal{H}_\Omega^\varphi(-v, \alpha), u \rangle + (\alpha/2)||u||^2 \).

# ## 6.4.2 Convergence analysis

In this subsection, we present a pivotal lemma concerning the upper limit of the consensus deviation, specifically \( \sup_{t \in \mathcal{V}} \{ \mathbb{E}[||q_t^i - \bar{q}_t||] \} \), to facilitate a more comprehensive understanding of Algorithm 1’s efficacy. Following this, we formulate the primary outcome pertaining to the upper bound of the regret, denoted as \( \bar{R}_T^i \), thereby achieving the convergence analysis for Algorithm 1.

We introduce the auxiliary vector \( \bar{q}_t \) as the sum of the products of \( \theta_t^i \) and \( q_t^i \) across all indices \( i \) from 1 to \( n \). For simplicity in our subsequent convergence analysis, we adopt the notation \( \hat{g}_t^i(x_t^i) \) as \( \hat{g}_t^i \) for all nodes \( i \) in the set \( \mathcal{V} \) and for all time steps \( t \ge 1 \). Consequently, we derive:

\(\bar{q}_{t+1} = \sum_{i=1}^n \theta_{t+1}^i \sum_{j=1}^n r_t^{ij} q_t^j + \sum_{i=1}^n \theta_{t+1}^i \sum_{j=1}^n r_t^{ij} \vartheta_t^j\)
\( + \sum_{i=1}^n \theta_{t+1}^i \frac{\hat{g}_t^i}{v_{t+1}^i} \)
\( = \bar{q}_t + \sum_{i=1}^n \theta_t^i \vartheta_t^i + \sum_{i=1}^n \theta_{t+1}^i \frac{\hat{g}_t^i}{v_{t+1}^i} ,\) (6.12)