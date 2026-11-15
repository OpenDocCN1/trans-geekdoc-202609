
- a) There exist positive constants \( C \) and \( \alpha \in (0, 1) \) such that the absolute difference between \( r_{s,t}^{i,j} \) and \( \theta_t^j \) is upper-bounded by \( C\varsigma^{s-t} \). Furthermore, the transpose of \( \theta_t \) is equal to the product of the transpose of \( \theta_{t+1} \) and the matrix \( R_t \).

- b) Let \( \{\mu_t^i\}_{t \ge 1} \) denote the sequence derived from Eq. (6.9). Subsequently, for a pre-determined time span \( T \), it holds that the magnitude of the difference between \( \frac{\mu_{t+1}^i}{n} \) and \( \theta_{t+1}^i \) is bounded above by \( Q\lambda^{T-t-1} \). Additionally, the elements \( \mu_{t+1}^i \) are confined within the interval \( [\varpi^{-1}, \varpi] \), where \( \varpi \) and \( \omega \) are positive constants.

Prior to presenting the subsequent pivotal lemma, we define a function of the conjugate type, denoted as \( \mathcal{G}_\Omega^\varphi(u, \beta) \), which pertains to any vector \( u \in \mathbb{R}^m \) and a positive step-size parameter \( \beta \), where

\(\mathcal{H}_\Omega^\varphi(v, \alpha) = \sup_{u \in \Omega} \{ \langle v, u \rangle - \frac{1}{\alpha} \phi(u) \}.\)

Subsequently, we formulate a pivotal lemma to underpin our primary findings, the verification of which can be traced back to [47].

**Lemma 6.3.** [47] Drawing upon the definitions of \( \Pi_\Omega^\varphi(\cdot) \) and \( \mathcal{G}_\Omega^\varphi(\cdot) \), we can assert that for any \( v, u \in \mathbb{R}^m \) and a positive \( \alpha \), the following relationships hold:

- a) \( \nabla \mathcal{H}_\Omega^\varphi(-v, \alpha) = \Pi_\Omega^\varphi(v, \alpha) \) and \( ||\nabla \mathcal{H}_\Omega^\varphi(-v, \alpha) - \nabla \mathcal{H}_\Omega^\varphi(-u, \alpha)|| = ||\Pi_\Omega^\varphi(v, \alpha) - \Pi_\Omega^\varphi(u, \alpha)|| \le \alpha ||v - u|| \).

- b) \( \mathcal{H}_\Omega^\varphi(-v - u, \alpha) \le \mathcal{H}_\Omega^\varphi(-v, \alpha) - \langle \nabla \mathcal{H}_\Omega^\varphi(-v, \alpha), u \rangle + (\alpha/2)||u||^2 \).

## 6.4.2 Convergence analysis

In this subsection, we present a pivotal lemma concerning the upper limit of the consensus deviation, specifically \( \sup_{t \in \mathcal{V}} \{ \mathbb{E}[||q_t^i - \bar{q}_t||] \} \), to facilitate a more comprehensive understanding of Algorithm 1’s efficacy. Following this, we formulate the primary outcome pertaining to the upper bound of the regret, denoted as \( \bar{R}_T^i \), thereby achieving the convergence analysis for Algorithm 1.

We introduce the auxiliary vector \( \bar{q}_t \) as the sum of the products of \( \theta_t^i \) and \( q_t^i \) across all indices \( i \) from 1 to \( n \). For simplicity in our subsequent convergence analysis, we adopt the notation \( \hat{g}_t^i(x_t^i) \) as \( \hat{g}_t^i \) for all nodes \( i \) in the set \( \mathcal{V} \) and for all time steps \( t \ge 1 \). Consequently, we derive:

\(\bar{q}_{t+1} = \sum_{i=1}^n \theta_{t+1}^i \sum_{j=1}^n r_t^{ij} q_t^j + \sum_{i=1}^n \theta_{t+1}^i \sum_{j=1}^n r_t^{ij} \vartheta_t^j\)
\( + \sum_{i=1}^n \theta_{t+1}^i \frac{\hat{g}_t^i}{v_{t+1}^i} \)
\( = \bar{q}_t + \sum_{i=1}^n \theta_t^i \vartheta_t^i + \sum_{i=1}^n \theta_{t+1}^i \frac{\hat{g}_t^i}{v_{t+1}^i} ,\) (6.12)

which is derived from Lemma 6.2 regarding a sequence of normalized vectors. By aggregating both sides of Eq. (6.12) across all values of \( t \) and subsequently reorganizing the ensuing equality, it follows that:

\(\bar{q}_{t+1} = \bar{q}_1 + \sum_{s=1}^t \sum_{i=1}^n \theta_s^i \vartheta_s^i + \sum_{s=1}^t \sum_{i=1}^n \theta_{s+1}^i \frac{\hat{g}_s^i}{v_{s+1}^i}.\) (6.13)

Furthermore, we introduce the notation \( b_{\max} \) to represent the maximum value of \( b_t \) over the range \( t \in \{1, \dots, T\} \). Subsequently, the following lemma is presented.

**Lemma 6.4.** Taking into account that the sequences \(\{q_t^i\}_{t=1}^T\) and \(\{v_t^i\}_{t=1}^T\) are iteratively updated according to Algorithm 1, and under the premises of Assumptions 6.1 and 6.2, we derive that \(\max_{i \in \mathcal{V}} \{\mathbb{E}[||q_t^i - \bar{q}_t||]\} \le O_1\) for all \( t = 1, \cdots, T \), where

\(O_1 = \frac{n Q(\sqrt{2m}b_{\max} + \omega m K)}{1 - \lambda} + Q \sum_{i=1}^n ||q_1^i|| + 2\omega m K.\)

Proof. As a consequence of Eqs. (6.8) and (6.12), we deduce that

\(q_{t+1}^i = \sum_{j=1}^n r_{t+1:1}^{ij} q_1^j + \sum_{s=1}^t \sum_{j=1}^n r_{t+1:s}^{ij} \vartheta_s^j\)
\(+ \sum_{s=1}^{t-1} \sum_{j=1}^n r_{t+1:s+1}^{ij} \frac{\hat{g}_s^j}{v_{s+1}^j} + \frac{\hat{g}_t^i}{v_{t+1}^i}.\) (6.14)

Subsequently, we derive the following from Eqs. (6.13) and (6.14):

\(q_{t+1}^i - \bar{q}_{t+1} = \tau_1 + \tau_2 + \tau_3,\) (6.15)

where

\(\tau_1 = \sum_{j=1}^n r_{t+1:1}^{ij} q_1^j - \sum_{j=1}^n \theta_1^j q_1^j,\)
\(\tau_2 = \sum_{s=1}^t \sum_{j=1}^n r_{t+1:s}^{ij} \vartheta_s^j - \sum_{s=1}^t \sum_{j=1}^n \theta_s^j \vartheta_s^j,\)
\(\tau_3 = \sum_{s=1}^{t-1} \sum_{j=1}^n r_{t+1:s+1}^{ij} \frac{\hat{g}_s^j}{v_{s+1}^j} - \sum_{s=1}^t \sum_{j=1}^n \theta_{s+1}^j \frac{\hat{g}_s^j}{v_{s+1}^j} + \frac{\hat{g}_t^i}{v_{t+1}^i}.\)

Utilizing Lemma 6.2 as a foundation, we infer from the parameter \(\tau_1\) that

\(\mathbb{E}[||\tau_1||] \le \mathbb{E}[\sum_{j=1}^n ||r_{t+1:1}^{ij} - \theta_1^j|| ||q_1^j||] \le Q \lambda^t \sum_{i=1}^n ||q_1^i||.\) (6.16)

Given that \(\vartheta_t^j\) stems from a Laplace distribution characterized by the parameter \(b_t\), it can be deduced that the square of its expected norm, \(\mathbb{E}[||\vartheta_t^j||^2]\), is upper-bounded by the expected value of its squared norm, \(\mathbb{E}[||\vartheta_t^j||^2]\), which in turn is not greater than \(2mb_{max}^2\). Consequently, we proceed to derive:

\(\begin{aligned} \mathbb{E}[||\tau_2||] \le \mathbb{E}[\sum_{s=1}^t \sum_{j=1}^n ||r_{t+1:s}^{ij} - \theta_s^j|| ||\vartheta_s^j||] \\ \le n Q \sum_{s=1}^t \lambda^{t+1-s} \mathbb{E}[||\vartheta_s^j||] \\ \le n Q \sum_{s=1}^t \lambda^{t+1-s} \sqrt{2m} b_{max}. \end{aligned} \quad (6.17)\)

Based on Lemma 6.1(c) and Lemma 6.2, it can be derived that

\(\begin{aligned} \mathbb{E}[||\tau_3||] \le \mathbb{E}[\sum_{s=1}^{t-1} \sum_{j=1}^n ||r_{t+1:s+1}^{ij} - \theta_{s+1}^j|| ||\frac{\hat{g}_s^j}{v_{s+1}^j}||] \\ + \mathbb{E}[\sum_{i=1}^n ||\theta_{t+1}^i - \frac{\hat{g}_t^i}{v_{t+1}^i}||] + \mathbb{E}[||\frac{\hat{g}_t^i}{v_{t+1}^i}||] \\ \le n Q \omega m K \sum_{s=1}^{t-1} \lambda^{t-s} + 2 \omega m K. \end{aligned} \quad (6.18)\)

Ultimately, we can deduce that

\(\mathbb{E}[||q_{t+1}^i - \bar{q}_{t+1}||] \le \mathbb{E}[||\tau_1||] + \mathbb{E}[||\tau_2||] + \mathbb{E}[||\tau_3||] \le O_1,\) (6.19)

which yields the intended outcome. \(\square\)

To achieve the targeted regret bound for \(\bar{R}_T^i\), we must establish an upper limit for the anticipated optimality discrepancy, represented by \(\mathbb{E}[f_t^i(x_t^j) - f_t^i(x^*)]\). Nevertheless, the optimal point \(x^*\) might reside beyond the confines of \((1 - \xi)\Omega\), whereas \(x_t^i\) stems from projecting \(q_t^i\) onto the constrained set \((1 - \xi)\Omega\). Consequently, we cannot straightforwardly apply Assumption 6.2(b) for further scrutiny, as seen in prior decentralized dual averaging approaches [27,39,40]. This poses a novel obstacle in our analytical endeavors. To bypass this hurdle, we introduce \(\check{x}\) as \((1 - \xi)x^*\), where \(x^*\) is the minimizer of \(\sum_{t=1}^T \sum_{i=1}^n f_t^i(x)\) over \(\Omega\), and equivalently recast the discrepancy \(\mathbb{E}[f_t^i(x_t^j) - f_t^i(x^*)]\) into

\(\begin{aligned} \mathbb{E}[f_t^i(x_t^j) - f_t^i(x^*)] &= \mathbb{E}[f_t^i(x_t^j) - f_t^i(x_t^i)] + \mathbb{E}[f_t^i(x_t^i) - f_t^i(\check{x})] \\ &+ \mathbb{E}[f_t^i(\check{x}) - f_t^i(x^*)]. \end{aligned}\)

Given that \(x_t^j\) belongs to \((1-\xi)\Omega\), and both \(\check{x}\) and \(x^*\) lie within \(\Omega\) with \(\check{x}\) specifically residing in \((1-\xi)\Omega\), we can leverage the Lipschitz continuity of the functions \(f_t^j\) to establish bounds for each component in the aforementioned equality. Subsequently, this enables us to attain the sought-after regret bound for \(\bar{R}_T^j\). For clarity, let us define \(\bar{x}_t\) as the projection of \(\bar{q}_t\) onto \((1-\xi)\Omega\) using the mapping function \(\phi\) with a step-size \(\alpha_{t-1}\). Considering a predetermined time span \(T\), we assign \(\delta = \frac{d}{\sqrt{T}}\) and \(\xi = \frac{1}{\sqrt{T}}\), after which we present the subsequent theorem.

**Theorem 6.1.** *Taking into account that the sequence* \(\{x_t^i\}_{t=1}^T\) *is iteratively refined by Algorithm 1, employing a step-size of* \(\alpha_t = \frac{\alpha_0}{\sqrt{t+1}}\) *with* \(\alpha_0 > 0\). *Given the validity of Assumptions 6.1 and 6.2, there exist positive, finite values denoted by* \(\Delta_1\) *and* \(\Delta_2\)*, respectively, that satisfy the following conditions:*

\(\bar{R}_T^j \le \Delta_1 \sqrt{T} + \Delta_2,\)

*for all* \(j \in \mathcal{V}\), *where*

\(\Delta_1 = (4+m)\alpha_0 n K O_1 + \frac{2n\phi(\check{x})}{\alpha_0} + 2\alpha_0 n^2 m^2 K^2 \omega^2\)
\(+ 4\alpha_0 n^2 m b_{\max}^2 + n K (d+D),\)
\(\Delta_2 = \frac{n^2 \omega m K D Q}{1 - \lambda} + n \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_1, \alpha_0) + n \langle \bar{q}_1, \check{x} \rangle.\)

**Proof.** Recall that for all \(i\), \(x_t^i\) lies within the set \((1-\xi)\Omega\), and similarly, \(\check{x}\) also belongs to this constrained set. The purpose of introducing the notation \(\check{x}\) is to indirectly facilitate the derivation of the upper limit for the expectation \(\mathbb{E}[f_t^i(x_t^i) - f_t^i(x^*)]\), as previously elaborated. In light of Assumptions 6.1 and 6.2, we can deduce that

\(\bar{R}_T^j = \mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n f_t^i(x_t^j) - \sum_{t=1}^T \sum_{i=1}^n f_t^i(x^*)]\)
\(=\mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n f_t^i(x_t^j) - \sum_{t=1}^T \sum_{i=1}^n f_t^i(x_t^i)]\)
\(+ \mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n f_t^i(\check{x}) - \sum_{t=1}^T \sum_{i=1}^n f_t^i(x^*)]\)
\(+ \mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n f_t^i(x_t^i) - \sum_{t=1}^T \sum_{i=1}^n f_t^i(\check{x})].\) (6.20)

Subsequently, we delve into the individual components of Eq. (6.20). Leveraging the convex nature of \(f_t^i\), we can infer from Assumption 6.2 that

\(\mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n f_t^i(x_t^j) - \sum_{t=1}^T \sum_{i=1}^n f_t^i(x_t^i)]\)
