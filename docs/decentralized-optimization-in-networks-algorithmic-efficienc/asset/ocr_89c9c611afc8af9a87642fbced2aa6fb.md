+ 2\mathbb{E}[(\bar{x}_t - x^*, -\alpha_t(\frac{1}{N}\mathbf{1}_N^T \otimes I_d)(y'_t - \frac{1}{N} \otimes \nabla f(\bar{x}_t) + \xi_t))]
+ 2\mathbb{E}[(\frac{\alpha_t}{N}\nabla f(\bar{x}_t), \alpha_t(\frac{1}{N}\mathbf{1}_N^T \otimes I_d)(y'_t - \frac{1}{N} \otimes \nabla f(\bar{x}_t) + \xi_t))]. \tag{4.26}

Drawing upon the Lipschitz continuity property of the gradient function \(\nabla f^i(\cdot)\), (4.13) and the fact stated in Lemma 10 of [26],\(^1\) it follows that

[[\bar{x}_t - x^* - \frac{\alpha_t}{N}\nabla f(\bar{x}_t)||^2] \le (1 - \frac{\mu\alpha_t}{N})^2 ||\bar{x}_t - x^*||^2],

subsequently, it fulfills

\(\mathbb{E}[||\bar{x}_{t+1} - x^*||^2]
\le (1 - \frac{\mu\alpha_t}{N})^2 \mathbb{E}[||\bar{x}_t - x^*||^2] + \frac{3\alpha_t^2 L^2}{N} \mathbb{E}[||x_t - 1_N \otimes \bar{x}_t||^2]
+ \frac{3\alpha_t^2}{N} \mathbb{E}[||y'_t - 1_N \otimes \bar{y}'_t||^2] + \frac{6c_w \alpha_t^2}{(1 - \tau_w)^2} (\frac{C\pi^2}{6} + U_1)
+ \frac{\alpha_t^2 L^2}{N} \mathbb{E}[||\bar{x}_t - x^*||^2] + \frac{3\alpha_t^2 L^2}{N^2} \mathbb{E}[||x_t - 1_N \otimes \bar{x}_t||^2]
+ \frac{3\alpha_t^2}{N^2} \mathbb{E}[||y'_t - 1_N \otimes \bar{y}'_t||^2] + \frac{6\alpha_t^2 c_w}{N(1 - \tau_w)^2} (\frac{C\pi^2}{6} + U_1)
+ 2\mathbb{E}[(\bar{x}_t - x^*, -\alpha_t(\frac{1}{N}\mathbf{1}_N^T \otimes I_d)(y'_t - \frac{1}{N} \otimes \nabla f(\bar{x}_t) + \xi_t))]. \tag{4.27}\)

where \(c_w\) is defined as \(\max\{1, ||\hat{W} - I_{Nd}||^2/\tau_w^2\}\) and \(\tau_w\) is specified in (4.10). Evidently, for the final component of (4.27), it follows that

\(\mathbb{E}[(\bar{x}_t - x^*, -\alpha_t(\frac{1}{N}\mathbf{1}_N^T \otimes I_d)(y'_t - \frac{1}{N} \otimes \nabla f(\bar{x}_t) + \xi_t))]
= \mathbb{E}[(\bar{x}_t - x^*, -\alpha_t(\frac{1}{N}\mathbf{1}_N^T \otimes I_d)(y'_t - \frac{1}{N} \otimes \nabla f(\bar{x}_t)))]
- \alpha_t \mathbb{E}[(\bar{x}_t - x^*, (\frac{1}{N}\mathbf{1}_N^T \otimes I_d) \sum_{l=0}^{t-1} \hat{W}(t, l)e_l^y)]
- \alpha_t \mathbb{E}[(\bar{x}_t - x^*, (\frac{1}{N}\mathbf{1}_N^T \otimes I_d) \sum_{l=0}^t \hat{W}(t, l)e_l)]. \tag{4.28}\)

Regarding the initial term on the right-hand side of (4.28), we have