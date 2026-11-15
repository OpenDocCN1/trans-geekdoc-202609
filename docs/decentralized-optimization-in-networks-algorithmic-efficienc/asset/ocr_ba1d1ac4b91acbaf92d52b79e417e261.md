Given that \(\vartheta_t^j\) stems from a Laplace distribution characterized by the parameter \(b_t\), it can be deduced that the square of its expected norm, \(\mathbb{E}[||\vartheta_t^j||^2]\), is upper-bounded by the expected value of its squared norm, \(\mathbb{E}[||\vartheta_t^j||^2]\), which in turn is not greater than \(2mb_{max}^2\). Consequently, we proceed to derive:

\(\begin{aligned} \mathbb{E}[||\tau_2||] \le \mathbb{E}[\sum_{s=1}^t \sum_{j=1}^n ||r_{t+1:s}^{ij} - \theta_s^j|| ||\vartheta_s^j||] \\ \le n Q \sum_{s=1}^t \lambda^{t+1-s} \mathbb{E}[||\vartheta_s^j||] \\ \le n Q \sum_{s=1}^t \lambda^{t+1-s} \sqrt{2m} b_{max}. \end{aligned} \quad (6.17)\)

Based on Lemma 6.1(c) and Lemma 6.2, it can be derived that

\(\begin{aligned} \mathbb{E}[||\tau_3||] \le \mathbb{E}[\sum_{s=1}^{t-1} \sum_{j=1}^n ||r_{t+1:s+1}^{ij} - \theta_{s+1}^j|| ||\frac{\hat{\mathcal{G}}_s^j}{\nu_{s+1}^j}||] \\ + \mathbb{E}[\sum_{i=1}^n ||\theta_{t+1}^i - \frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i}||] + \mathbb{E}[||\frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i}||] \\ \le n Q \omega m K \sum_{s=1}^{t-1} \lambda^{t-s} + 2 \omega m K. \end{aligned} \quad (6.18)\)

Ultimately, we can deduce that

\(\mathbb{E}[||q_{t+1}^i - \bar{q}_{t+1}||] \le \mathbb{E}[||\tau_1||] + ||\tau_2|| + ||\tau_3||] \le O_1, \quad (6.19)\)

which yields the intended outcome. \(\square\)

To achieve the targeted regret bound for \(\bar{R}_T^i\), we must establish an upper limit for the anticipated optimality discrepancy, represented by \(\mathbb{E}[f_t^i(x_t^j) - f_t^i(x^*)]\). Nevertheless, the optimal point \(x^*\) might reside beyond the confines of \((1 - \xi)\Omega\), whereas \(x_t^i\) stems from projecting \(q_t^i\) onto the constrained set \((1 - \xi)\Omega\). Consequently, we cannot straightforwardly apply Assumption 6.2(b) for further scrutiny, as seen in prior decentralized dual averaging approaches [27,39,40]. This poses a novel obstacle in our analytical endeavors. To bypass this hurdle, we introduce \(\check{x}\) as \((1 - \xi)x^*\), where \(x^*\) is the minimizer of \(\sum_{t=1}^T \sum_{i=1}^n f_t^i(x)\) over \(\Omega\), and equivalently recast the discrepancy \(\mathbb{E}[f_t^i(x_t^j) - f_t^i(x^*)]\) into

\(\begin{aligned} \mathbb{E}[f_t^i(x_t^j) - f_t^i(x^*)] &= \mathbb{E}[f_t^i(x_t^j) - f_t^i(x_t^i)] + \mathbb{E}[f_t^i(x_t^i) - f_t^i(\check{x})] \\ &+ \mathbb{E}[f_t^i(\check{x}) - f_t^i(x^*)]. \end{aligned}\)