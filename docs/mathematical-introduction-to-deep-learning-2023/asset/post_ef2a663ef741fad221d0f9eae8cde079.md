
Furthermore, note that $(4.38)$ and the fact that for all $\mathbf{d} \in \{3, 5, 7, \dots\}$ it holds that $\lceil \log_2(\mathbf{d} + 1) \rceil = \lceil \log_2(\mathbf{d}) \rceil$ ensure that for all $\mathbf{d} \in \{3, 5, 7, \dots\}$ with $\mathcal{H}(\mathbb{M}_{\lceil \log_2 \rceil \rceil} = \lceil \log_2(\lceil \frac{\mathbf{d}}{2} \rceil \rceil]$ it holds that

$$
\begin{eqnarray}
\mathcal{H}(\mathbb{M}_{\mathbf{d}}) &=& \lceil \log_2(\lceil \frac{\mathbf{d}}{2} \rceil \rceil + 1 = \lceil \log_2(\lceil \frac{\mathbf{d} + 1}{2} \rceil) \rceil + 1 \\
&=& \lceil \log_2(\mathbf{d} + 1) - 1 \rceil + 1 = \lceil \log_2(\mathbf{d} + 1) \rceil = \lceil \log_2(\mathbf{d}) \rceil.\tag{4.40}
\end{eqnarray}
$$

Combining this and $(4.39)$ demonstrates that for all $\mathbf{d} \in \{3, 4, 5, \dots\}$ with $\forall k \in \{2, 3, \dots, \mathbf{d} - 1\}$: $\mathcal{H}(\mathbb{M}_k) = \lceil \log_2(k) \rceil$ it holds that

$$
\mathcal{H}(\mathbb{M}_{\mathbf{d}}) = \lceil \log_2(\mathbf{d}) \rceil.\tag{4.41}
$$

The fact that $\mathcal{H}(\mathbb{M}_2) = 1$ and induction hence establish item (i). Observe that the fact that $\mathcal{D}(\mathbb{M}_2) = (2, 3, 1)$ assure that for all $i \in \mathbb{N}$ it holds that

$$
\mathbb{D}_i(\mathbb{M}_2) \leq 3 = 3 \lceil \frac{2}{2^i} \rceil.\tag{4.42}
$$

Moreover, note that Proposition 2.1.2 and Lemma 2.2.2 imply that for all $\mathbf{d} \in \{2, 3, 4, \dots\}$, $i \in \mathbb{N}$ it holds that

$$
\mathbb{D}_i(\mathbb{M}_{2\mathbf{d}}) = \begin{cases} 3\mathbf{d} & : i = 1 \\
\mathbb{D}_{i-1}(\mathbb{M}_{\mathbf{d}}) & : i \geq 2 \end{cases}\tag{4.43}
$$

and

$$
\mathbb{D}_i(\mathbb{M}_{2\mathbf{d}-1}) = \begin{cases} 3\mathbf{d} - 1 & : i = 1 \\
\mathbb{D}_{i-1}(\mathbb{M}_{\mathbf{d}}) & : i \geq 2. \end{cases}\tag{4.44}
$$

This assures that for all $\mathbf{d} \in \{2, 4, 6, \dots\}$ it holds that

$$
\mathbb{D}_1(\mathbb{M}_{\mathbf{d}}) = 3(\frac{\mathbf{d}}{2}) = 3 \lceil \frac{\mathbf{d}}{2} \rceil.\tag{4.45}
$$

In addition, observe that $(4.44)$ ensures that for all $\mathbf{d} \in \{3, 5, 7, \dots\}$ it holds that

$$
\mathbb{D}_1(\mathbb{M}_{\mathbf{d}}) = 3 \lceil \frac{\mathbf{d}}{2} \rceil - 1 \leq 3 \lceil \frac{\mathbf{d}}{2} \rceil.\tag{4.46}
$$

This and $(4.45)$ show that for all $\mathbf{d} \in \{2, 3, 4, \dots\}$ it holds that

$$
\mathbb{D}_1(\mathbb{M}_{\mathbf{d}}) \leq 3 \lceil \frac{\mathbf{d}}{2} \rceil.\tag{4.47}
$$

Next note that $(4.43)$ demonstrates that for all $\mathbf{d} \in \{4, 6, 8, \dots\}$, $i \in \{2, 3, 4, \dots\}$ with $\mathbb{D}_{i-1}(\mathbb{M}_{\frac{\mathbf{d}}{2}}) \leq 3 \lceil \frac{\mathbf{d}}{2} \frac{1}{2^{i-1}} \rceil$ it holds that

$$
\mathbb{D}_i(\mathbb{M}_{\mathbf{d}}) = \mathbb{D}_{i-1}(\mathbb{M}_{\frac{\mathbf{d}}{2}}) \leq 3 \lceil \frac{\mathbf{d}}{2} \frac{1}{2^{i-1}} \rceil = 3 \lceil \frac{\mathbf{d}}{2^i} \rceil.\tag{4.48}
$$

Furthermore, observe that (4.44) and the fact that for all $\mathfrak{d} \in \{3, 5, 7, \ldots\}$, $i \in \mathbb{N}$ it holds that $\left\lceil\frac{\mathfrak{d}+1}{2^{i}}\right\rceil = \left\lceil\frac{\mathfrak{d}}{2^{i}}\right\rceil$ assume that for all $\mathfrak{d} \in \{3, 5, 7, \ldots\}$, $i \in \{2, 3, 4, \ldots\}$ with $\mathbb{D}_{i-1}(\mathbb{M}^{[\lceil \eta/2 \rceil]}) \leq 3\lceil\lceil\frac{\eta}{2}\rceil\frac{1}{2^{i-1}}\rceil$ it holds that

$$
\mathbb{D}_{i}(\mathbb{M}_{\mathfrak{d}}) = \mathbb{D}_{i-1}(\mathbb{M}_{\lceil \frac{\mathfrak{d}}{2} \rceil}) \leq 3\lceil\lceil\frac{\mathfrak{d}}{2}\rceil\frac{1}{2^{i-1}}\rceil = 3\lceil\frac{\mathfrak{d}+1}{2^{i}}\rceil = 3\lceil\frac{\mathfrak{d}}{2^{i}}\rceil.\tag{4.49}
$$

This and (4.48) ensure that for all $\mathfrak{d} \in \{3, 4, 5, \ldots\}$, $i \in \{2, 3, 4, \ldots\}$ with $\forall k \in \{2, 3, \ldots, \mathfrak{d} - 1\}, j \in \{1, 2, \ldots, i-1\}$ : $\mathbb{D}_{j}(\mathbb{M}_{k}) \leq 3\lceil\frac{k}{2^{j}}\rceil$ it holds that

$$
\mathbb{D}_{i}(\mathbb{M}_{\mathfrak{d}}) \leq 3\lceil\frac{\mathfrak{d}}{2^{i}}\rceil.\tag{4.50}
$$

Combining this, (4.42), and (4.47) with induction establishes item **(ii)**. Note that (4.34) ensures that for all $x = (x_{1}, x_{2}) \in \mathbb{R}^{2}$ it holds that

$$
\left(\mathcal{R}_{\mathfrak{c}}^{\mathbf{N}}(\mathbb{M}_{\mathfrak{d}}^{2})\right)(x) = \max\{x_{1} - x_{2}, 0\} + \max\{x_{2}, 0\} - \max\{-x_{2}, 0\}
$$

$$
= \max\{x_{1} - x_{2}, 0\} + x_{2} = \max\{x_{1}, x_{2}\}.\tag{4.51}
$$

(cf. Definitions **1.2.4** and **1.3.4**). Proposition **2.2.3**, Proposition **2.1.2**, Lemma **2.2.7**, and induction hence imply that for all $\mathfrak{d} \in \{2, 3, 4, \ldots\}$, $x = (x_{1}, x_{2}, \ldots, x_{\mathfrak{d}}) \in \mathbb{R}^{\mathfrak{d}}$ it holds that

$$
\mathcal{R}_{\mathfrak{c}}^{\mathbf{N}}(\mathbb{M}_{\mathfrak{d}}) \in C(\mathbb{R}^{\mathfrak{d}}, \mathbb{R})\quad\text{and}\quad\left(\mathcal{R}_{\mathfrak{c}}^{\mathbf{N}}(\mathbb{M}_{\mathfrak{d}}^{2})\right)(x) = \max\{x_{1}, x_{2}, \ldots, x_{\mathfrak{d}}\}.\tag{4.52}
$$

This establishes items **(iii)** and **(iv)**. The proof of Proposition **4.2.7** is thus complete.

### Lemma 4.2.8.

Let $d \in \mathbb{N}$, $i \in \{1, 2, \ldots\}$, $\mathcal{L}(\mathbb{M}_{\mathfrak{d}})$ (cf. Definitions **1.3.1** and **4.2.5**). Then

-   (i) it holds that $\mathcal{B}_{i, \mathbb{M}_{\mathfrak{d}}} = 0 \in \mathbb{R}^{\mathbb{D}_{i}(\mathbb{M}_{\mathfrak{d}})}$,
-   (ii) it holds that $\mathcal{W}_{i, \mathbb{M}_{\mathfrak{d}}} \in \{-1, 0, 1\}^{\mathbb{D}_{i}(\mathbb{M}_{\mathfrak{d}}) \times \mathbb{D}_{i-1}(\mathbb{M}_{\mathfrak{d}})}$, and
-   (iii) it holds for all $x \in \mathbb{R}^{d}$ that $||\mathcal{W}_{i, \mathbb{M}_{\mathfrak{d}}} x||_{\infty} \leq 2||x||_{\infty}$

(cf. Definition **3.3.4**).

*Proof of Lemma **4.2.8**.* Throughout this proof, assume without loss of generality that $d > 2$ (cf. items **(iii)** and **(iv)** in Definition **4.2.5**) and let $A_{1} \in \mathbb{R}^{3 \times 2}$, $A_{2} \in \mathbb{R}^{1 \times 3}$, $C_{1} \in \mathbb{R}^{2 \times 1}$, $C_{2} \in \mathbb{R}^{1 \times 2}$ satisfy

$$
A_{1} = \left(\begin{matrix}1 & -1\\0 & 1\\0 & -1\end{matrix}\right) \quad A_{2} = \left(\begin{matrix}1 & 1 & -1\end{matrix}\right), \quad C_{1} = \left(\begin{matrix}1\\-1\end{matrix}\right), \text{and} \quad C_{2} = \left(\begin{matrix}1 & -1\end{matrix}\right).\tag{4.53}
$$

Note that items (iv), (v), and (vi) in Definition 4.2.5 assure that for all $\mathfrak{d} \in \{2, 3, 4, \dots\}$ it holds that

$$
\mathcal{W}_{1, \mathbb{M}_{2\mathfrak{d}-1}} = \begin{pmatrix} A_{1} & 0 & \cdots & 0 & 0 \\ 0 & A_{1} & \cdots & 0 & 0 \\ \vdots & \vdots & \ddots & \vdots & \vdots \\ 0 & 0 & \cdots & A_{1} & 0 \\ 0 & 0 & \cdots & 0 & C_{1} \end{pmatrix}_{\in \mathbb{R}^{(3\mathfrak{d}-1) \times (2\mathfrak{d}-1)}}, \quad \mathcal{W}_{1, \mathbb{M}_{2\mathfrak{d}}} = \begin{pmatrix} A_{1} & 0 & \cdots & 0 \\ 0 & A_{1} & \cdots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \cdots & A_{1} \end{pmatrix}_{\in \mathbb{R}^{(3\mathfrak{d}) \times (2\mathfrak{d})}},\tag{4.54}
$$

$$
\mathcal{B}_{1, \mathbb{M}_{2\mathfrak{d}-1}} = \mathbf{0} \in \mathbb{R}^{3\mathfrak{d}-1}, \quad \text{and} \quad \mathcal{B}_{1, \mathbb{M}_{2\mathfrak{d}}} = \mathbf{0} \in \mathbb{R}^{3\mathfrak{d}}.
$$

This and (4.53) proves item (iii). Furthermore, note that (4.54) and item (iv) in Definition 4.2.5 imply that for all $\mathfrak{d} \in \{2, 3, 4, \dots\}$ it holds that $\mathcal{B}_{1, \mathbb{M}_{\mathfrak{d}}} = \mathbf{0}$. Items (iv), (v), and (vi) in Definition 4.2.5 hence assure that for all $\mathfrak{d} \in \{2, 3, 4, \dots\}$ it holds that

$$
\mathcal{W}_{2, \mathbb{M}_{2\mathfrak{d}-1}} = \mathcal{W}_{1, \mathbb{M}_{\mathfrak{d}}} \begin{pmatrix} A_{2} & 0 & \cdots & 0 & 0 \\ 0 & A_{2} & \cdots & 0 & 0 \\ \vdots & \vdots & \ddots & \vdots & \vdots \\ 0 & 0 & \cdots & A_{2} & 0 \\ 0 & 0 & \cdots & 0 & C_{2} \end{pmatrix}_{\in \mathbb{R}^{\mathfrak{d} \times (3\mathfrak{d}-1)}}, \quad \mathcal{W}_{2, \mathbb{M}_{2\mathfrak{d}}} = \mathcal{W}_{1, \mathbb{M}_{\mathfrak{d}}} \begin{pmatrix} A_{2} & 0 & \cdots & 0 \\ 0 & A_{2} & \cdots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \cdots & A_{2} \end{pmatrix}_{\in \mathbb{R}^{\mathfrak{d} \times (3\mathfrak{d})}},
$$

$$
\mathcal{B}_{2, \mathbb{M}_{2\mathfrak{d}-1}} = \mathcal{B}_{1, \mathbb{M}_{\mathfrak{d}}} = \mathbf{0}, \quad \text{and} \quad \mathcal{B}_{2, \mathbb{M}_{2\mathfrak{d}}} = \mathcal{B}_{1, \mathbb{M}_{\mathfrak{d}}} = \mathbf{0}.\tag{4.55}
$$

Combining this and item (iv) in Definition 4.2.5 shows that for all $\mathfrak{d} \in \{2, 3, 4, \dots\}$ it holds that $\mathcal{B}_{2, \mathbb{M}_{\mathfrak{d}}} = \mathbf{0}$. Moreover, note that (2.2) demonstrates that for all $\mathfrak{d} \in \{2, 3, 4, \dots\}$, $i \in \{3, 4, \dots, \mathcal{L}(\mathbb{M}_{\mathfrak{d}}) + 1\}$ it holds that

$$
\mathcal{W}_{i, \mathbb{M}_{2\mathfrak{d}-1}} = \mathcal{W}_{i, \mathbb{M}_{2\mathfrak{d}}} = \mathcal{W}_{i-1, \mathbb{M}_{\mathfrak{d}}} \quad \text{and} \quad \mathcal{B}_{i, \mathbb{M}_{2\mathfrak{d}-1}} = \mathcal{B}_{i, \mathbb{M}_{2\mathfrak{d}}} = \mathcal{B}_{i-1, \mathbb{M}_{\mathfrak{d}}}.\tag{4.56}
$$

This, (4.53), (4.54), (4.55), the fact that for all $\mathfrak{d} \in \{2, 3, 4, \dots\}$ it holds that $\mathcal{B}_{2, \mathbb{M}_{\mathfrak{d}}} = \mathbf{0}$, and induction establish items (i) and (ii). The proof of Lemma 4.2.8 is thus complete. $\square$

### 4.2.3 AN N representations for maximum convolutions

**Lemma 4.2.9.** Let $d, K \in \mathbb{N}$, $L \in [0, \infty)$, $\mathfrak{f}_{1}, \mathfrak{f}_{2}, \dots, \mathfrak{f}_{K} \in \mathbb{R}^{d}$, $\mathfrak{\eta} = (\mathfrak{\eta}_{1}, \mathfrak{\eta}_{2}, \dots, \mathfrak{\eta}_{K}) \in \mathbb{R}^{K}$, $\Phi \in \mathbb{N}$ satisfy

$$
\Phi = \mathbb{M}_{K} \bullet \mathbf{A}_{-L, \mathbb{I}_{K}} \bullet \mathbf{P}_{K}(\mathbb{I}_{\iota d} \bullet \mathbf{A}_{\mathfrak{f}_{\iota_{1}-\mathfrak{f}_{1}}} \| \mathbb{I}_{\iota d} \bullet \mathbf{A}_{\mathfrak{f}_{\iota_{2}-\mathfrak{f}_{2}}}, \dots, \mathbb{I}_{\iota d} \bullet \mathbf{A}_{\mathfrak{f}_{\iota_{K}-\mathfrak{f}_{K}}}) \bullet \mathbb{T}_{d, K}\tag{4.57}
$$

(cf. Definitions 1.3.1, 1.5.5, 2.1.1, 2.2.1, 2.3.1, 2.4.6, 4.2.1, and 4.2.5). Then
