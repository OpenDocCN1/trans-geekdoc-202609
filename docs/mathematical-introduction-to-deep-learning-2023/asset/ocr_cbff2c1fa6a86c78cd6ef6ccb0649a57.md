# 6.3. GD optimization with classical momentum

In addition, observe that the assumption that $\Theta_{-1} = \Theta_0 = \xi$ and (6.263) ensure that

$$\mathbf{m}_0 = -\sqrt{\bar{K} \kappa} \left( \Theta_0 - \Theta_{-1} \right) = 0. \tag{6.271}$$

Combining this and the assumption that $\Theta_0 = \xi$ with (6.269) and (6.270) proves item (i). It thus remains to prove item (ii). For this observe that (6.259) implies that for all $\theta = (\theta_1, \theta_2, \dots, \theta_{\mathfrak{d}}) \in \mathbb{R}^{\mathfrak{d}}$, $i \in \{1, 2, \dots, \mathfrak{d}\}$ it holds that

$$\left( \frac{\partial f}{\partial \theta_i} \right) (\theta) = \lambda_i \langle \theta_i - v_i \rangle. \tag{6.272}$$

This, (6.260), and (6.264) imply that for all $n \in \mathbb{N}$, $i \in \{1, 2, \dots, \mathfrak{d}\}$ it holds that

$\Theta_n^{(i)} - v_i = \Theta_{n-1}^{(i)} - \varrho \left( \frac{\partial f}{\partial \theta_i} \right) \left( \Theta_{n-1} \right) + \alpha ( \Theta_{n-1}^{(i)} - \Theta_{n-2}^{(i)} ) - v_i$
$$= \langle \Theta_{n-1}^{(i)} - v_i \rangle - \varrho \lambda_i ( \Theta_{n-1}^{(i)} - v_i ) + \alpha ( \langle \Theta_{n-1}^{(i)} - v_i \rangle - \langle \Theta_{n-2}^{(i)} - v_i \rangle ) \tag{6.273}$$
$$= ( 1 - \varrho \lambda_i + \alpha ) \langle \Theta_{n-1}^{(i)} - v_i \rangle - \alpha \langle \Theta_{n-2}^{(i)} - v_i \rangle.$$

Combining this with (6.265) demonstrates that for all $n \in \mathbb{N}$ it holds that

$\mathbb{R}^{\mathfrak{d}} \ni \left( \Theta_n - v \right) = M ( \Theta_{n-1} - v ) - \alpha ( \Theta_{n-2} - v )$
$$= \begin{pmatrix} M & (-\alpha \, \mathrm{I}_{\mathfrak{d}}) \\ & 0 \end{pmatrix}_{\in \mathbb{R}^{\mathfrak{d}} \times \mathfrak{d}} \underbrace{ \begin{pmatrix} \Theta_{n-1} - v \\ \Theta_{n-2} - v \end{pmatrix} }_{\in \mathbb{R}^{2\mathfrak{d}}}. \tag{6.274}$$

This and (6.266) assure that for all $n \in \mathbb{N}$ it holds that

$\mathbb{R}^{2\mathfrak{d}} \ni \begin{pmatrix} \Theta_n - v \\ \Theta_{n-1} - v \end{pmatrix} = \begin{pmatrix} M & (-\alpha \, \mathrm{I}_{\mathfrak{d}}) \\ \mathrm{I}_{\mathfrak{d}} & 0 \end{pmatrix} \begin{pmatrix} \Theta_{n-1} - v \\ \Theta_{n-2} - v \end{pmatrix} = A \begin{pmatrix} \Theta_{n-1} - v \\ \Theta_{n-2} - v \end{pmatrix}. \tag{6.275}$$

Induction hence proves that for all $n \in \mathbb{N}_0$ it holds that

$\mathbb{R}^{2\mathfrak{d}} \ni \begin{pmatrix} \Theta_n - v \\ \Theta_{n-1} - v \end{pmatrix} = A^n \begin{pmatrix} \Theta_0 - v \\ \Theta_{-1} - v \end{pmatrix} = A^n \begin{pmatrix} \xi - v \\ \xi - v \end{pmatrix}. \tag{6.276}$$

This implies that for all $n \in \mathbb{N}_0$ it holds that

$\left\| \Theta_n - v \right\|_2 \leq \sqrt{\left\| \Theta_n - v \right\|_2^2 + \left\| \Theta_{n-1} - v \right\|_2^2}$
$$= \left\| \begin{pmatrix} \Theta_n - v \\ \Theta_{n-1} - v \end{pmatrix} \right\|_2$
$$= \left\| A^n \begin{pmatrix} \xi - v \\ \xi - v \end{pmatrix} \right\|_2$
$$\leq \left\| A^n \right\| \left\| \begin{pmatrix} \xi - v \\ \xi - v \end{pmatrix} \right\|_2$
$$= \left\| A^n \right\| \sqrt{\left\| \xi - v \right\|_2^2 + \left\| \xi - v \right\|_2^2} \tag{6.277}$$
$$= \left\| A^n \right\| \sqrt{2} \left\| \xi - v \right\|_2.$$