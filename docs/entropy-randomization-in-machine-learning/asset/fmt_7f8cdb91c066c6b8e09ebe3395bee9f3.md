
where the admissible set `Ω` is given by the normalization conditions (5.21) and the empirical balance constraints (5.24).

### 5.2.2 Estimation algorithms for RPM-Rel model

In the RPM-Rel model, the randomized parameters include the nonnegative relative parameters `u` and the measurement noises `{ \overline{\eta}^{(1)},\ldots,\overline{\eta}^{(s)} }`. According to (5.13), the observable output of the RPM-Rel model at a time instant *t*[*j*] is described by

$$
\begin{aligned} \left. \mathbf{f}(t_{j}) = \mathbf{z}\lbrack t_{j}\, \middle| \, W(\mathbf{u})\rbrack \right. & {+ \overline{\xi}_{-}^{(j)} + K_{j}\overline{\eta}^{(j)}\lbrack G_{j}(\overline{\eta}^{(j)})\rbrack,} \\ \left. \mathbf{z}\lbrack t_{j}\, \middle| \, W(\mathbf{u})\rbrack = \mathcal{D}\lbrack\mathbf{x}(t_{j},\tau), \right. & {\mathbf{a}^{-} + A\,\mathbf{u},\, W(\mathbf{u});(t_{j},\tau) \in \mathcal{T}\rbrack,} \\ & {j = \overline{1,s}.} \\ \end{aligned}
$$

(5.26)

Here, `𝒟` denotes a matrix functional of dimensions (*m* × *n*) that characterizes an existing relation between the model's output `z(t[j])` and the array composed of the input vectors `x(t[j], τ[1])`, …, `x(t[j], τ[(j − 1)])`. The RPM-Rel model output (5.2.2) depends on the randomized relative parameters `u` with a PDF `W(u)` and also on the randomized relative noise vectors `\overline{\eta}^{(j)}` with a PDF `G_{j}(\overline{\eta}^{(j)});` see (5.2.2). The available prior information about these PDFs (if any) is represented in the form of prior PDFs `W[0](u)` and `G_{j}^{0}(\overline{\eta}^{(j)})`. By assumption, the PDFs belong to the class `ℂ¹` of all continuously differentiable functions.

*For the RPM-Rel model (5.1), the entropy-robust estimation problem of the PDFs of its parameters and measurement noises* is formulated as follows:

* maximize the generalized Boltzmann information entropy functional

$$
\begin{aligned} & {\quad\mathcal{H}\lbrack W(\mathbf{u}),\overline{G}(\eta)\rbrack = - {\int_{\mathcal{U}}W}(\mathbf{u})\,\ln\frac{W(\mathbf{u})}{W_{0}(\mathbf{u})}\, d\,\mathbf{u} -} \\ & \left. - {\sum\limits_{j = 1}^{s}\,}{\int_{\mathcal{E}_{j}}G_{j}}(\overline{\eta}^{(j)})\,\ln\frac{G_{j}(\overline{\eta}^{(j)})}{G_{j}^{0}(\overline{\eta}^{(j)})}d\overline{\eta}^{(j)}\Rightarrow\min_{W,\overline{G}} \right. \\ \end{aligned}
$$

(5.27)

* subject to:

  * –the normalization conditions for the PDF, i.e.,

$$
\begin{array}{r} {{\int_{\mathcal{U}}W}(\mathbf{u})d\mathbf{u} = 1,\text{\quad\quad}{\int_{\mathcal{E}_{j}}G_{j}}(\overline{\eta}^{(j)})\, d\overline{\eta}^{(j)} = 1,\quad j = \overline{1,s},} \\ \end{array}
$$

(5.28)

and

  * –the balance constraints for the *k*-means of the output of the RPM-Rel model (5.15) and the measurements of the object's output, i.e.,

$$
\begin{array}{r} {\mathbf{n}^{(k)}\lbrack W(\mathbf{u}),G_{j}(\overline{\eta}^{(j)}),j\rbrack = \mathbf{y}(t_{j}),\text{\quad\quad}j = \overline{1,s}.} \\ \end{array}
$$

(5.29)

Due to (5.15), the vector `\mathbf{n}^{(k)}\lbrack W(\mathbf{u}),G_{j}(\overline{\eta}^{(j)}),j\rbrack` in these equality constraints has the components

$$
\begin{aligned} {n_{i}^{(k)}\lbrack j\rbrack} & {\left[\int_{\mathcal{U}}W}(\mathbf{u})z_{i}^{k}\lbrack t_{j}\, \middle| \, W(\mathbf{u})\rbrack\, d\mathbf{u} \right]^{1/k} +} \\ & {\left[\int_{\mathcal{E}_{j}}\,}{G_{j}(\overline{\eta}^{(j)})\,{\lbrack\eta_{i}^{(j)}\rbrack}^{k}\, d\eta_{i}^{(j)}} \right]^{1/k},} \\ & {\text{\quad\quad}\quad i = \overline{1,m},\, j = \overline{1,s}.} \\ \end{aligned}
$$

(5.30)

Consider the case in which the balance constraints involve the 1-mean of the RPM-Rel model output:

$$
\begin{aligned} {\left[\int_{\mathcal{U}}W}(\mathbf{u})\mathbf{z}\lbrack t_{j}\, \middle| \, W(\mathbf{u})\rbrack\, d\mathbf{u} \right] +} & {\left[\int_{\mathcal{E}_{j}}\,}{G_{j}(\overline{\eta}^{(j)})\,{\overline{\eta}}^{(j)}\, d\overline{\eta}^{(j)}} \right] = \mathbf{y}(t_{j}),} \\ & {j = \overline{1,s}.} \\ \end{aligned}
$$

(5.31)

Like in the optimization problem presented above, the functional constraints extract the subset `\Psi\lbrack W(\mathbf{u}),G(\overline{\eta})\rbrack` of all admissible functions, where `G(\overline{\eta}) = \{ G_{1}(\overline{\eta}^{(1)}),\ldots,G_{s}(\overline{\eta}^{(s)}) \}`, from the class `ℂ¹`. The problem (5.27-5.31) is also of the Lyapunov type.

*For the RPM-Rel model, the entropy-robust RML algorithm* has the form

$$
\begin{array}{r} {\left[\,W(\mathbf{u}),\overline{G}(\overline{\eta}) \right]^{*} = \arg\max_{\lbrack W(\mathbf{u}),\overline{G}(\overline{\eta})\rbrack}\left\{ \mathcal{H},\, \middle| \,\lbrack W(\mathbf{u}),G(\overline{\eta})\rbrack \in \Psi \right\},} \\ \end{array}
$$

(5.32)

where the admissible set `Ψ` is given by the normalization conditions (5.28) and the empirical balance constraints (5.31).

### 5.2.3 Estimation algorithms for RPM-F model with measurement errors of input and output

The previous sections have studied cases of measurement errors figuring in the output only. However, in many applications, there are input data collections containing errors as well. Hence, the general RML procedure should be modified accordingly.

If errors occur in the input data, the observed output of the RPM-F model takes the following form:

$$
\begin{array}{r} \left. \mathbf{v}(t_{j}) = \mathbf{y}\lbrack t_{j}\, \middle| \, F(\mathbf{a},\overline{\mu}^{(j)})\rbrack + \overline{\xi}\lbrack Q_{j}(\overline{\xi}^{(j)})\rbrack, \right. \\ \left. \mathbf{y}\lbrack t_{j}\, \middle| \, F(\mathbf{a},\overline{\mu}^{(t_{j})})\rbrack = \mathcal{B}\lbrack\mathbf{x}(t_{j},\tau) + \overline{\mu}^{(t_{j})}\rbrack. \right. \\ \end{array}
$$

(5.33)

Here `\overline{\mu}^{(j)}` denotes the vector of input noises at a time instant *t*[*j*], which are of the interval type:

$$
\begin{array}{r} {{\overline{\mu}}^{(j)} \in \mathcal{M} = \lbrack\mu^{-},\mu^{+}\rbrack\quad\text{for~all}\, t_{j}.} \\ \end{array}
$$

(5.34)

From the RPM-F model equations (5.33) it follows that the random elements are the parameters `a` and the input noise `\overline{\mu}.` Their probabilistic properties are characterized by a joint probability density function `F(a,\overline{\mu}^{(t_{j})})`. If there exists some information about this function, it is represented in the form of a prior PDF `F_{0}(a,\overline{\mu}^{(t_{j})})`.

*For the RPM-F model (5.33), the entropy-robust estimation problem of the PDFs of its parameters and input and output measurement noises* is formulated as follows:

* maximize the generalized Boltzmann information entropy functional

$$
\begin{aligned} {\mathcal{H}\lbrack F(\mathbf{a},\overline{\mu}),\overline{Q}(\overline{\xi})\rbrack} & {= - \int_{\mathcal{R}}F(\mathbf{a},\overline{\mu})\,\ln\frac{F(\mathbf{a},\overline{\mu})}{F_{0}(\mathbf{a},\overline{\mu})}\, d\,\mathbf{a}\, d\,\overline{\mu} -} \\ {- \sum_{j = 1}^{s}\,\int_{\Xi_{j}}} & \left. Q_{j}(\overline{\xi}^{(j)})\,\ln\frac{Q_{j}(\overline{\xi}^{(j)})}{Q_{j}^{0}(\overline{\xi}^{(j)})}d\overline{\xi}^{(j)}\Rightarrow\max_{F,\overline{Q}} \right. \\ \end{aligned}
$$

(5.35)

* subject to:

  * —the normalization conditions for the PDFs, i.e.,
