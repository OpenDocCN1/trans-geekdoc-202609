Furthermore, note that $(4.38)$ and the fact that for all $\mathbf{d} \in \{3, 5, 7, \dots\}$ it holds that $[\lceil \log_2(\mathbf{d} + 1) \rceil = \lceil \log_2(\mathbf{d}) \rceil$ ensure that for all $\mathbf{d} \in \{3, 5, 7, \dots\}$ with $\mathcal{H}(\mathbb{M}_{\lceil \log_2 \rceil \rceil} = \lceil \log_2(\lceil \frac{\mathbf{d}}{2} \rceil \rceil]$ it holds that

$$\begin{eqnarray} \mathcal{H}(\mathbb{M}_{\mathbf{d}}) &=& \lceil \log_2(\lceil \frac{\mathbf{d}}{2} \rceil \rceil + 1 = \lceil \log_2(\lceil \frac{\mathbf{d} + 1}{2} \rceil) \rceil + 1 \\
&=& \lceil \log_2(\mathbf{d} + 1) - 1 \rceil + 1 = \lceil \log_2(\mathbf{d} + 1) \rceil = \lceil \log_2(\mathbf{d}) \rceil.\tag{4.40} \end{eqnarray}$$

Combining this and $(4.39)$ demonstrates that for all $\mathbf{d} \in \{3, 4, 5, \dots\}$ with $\forall k \in \{2, 3, \dots, \mathbf{d} - 1\}$: $\mathcal{H}(\mathbb{M}_k) = \lceil \log_2(k) \rceil$ it holds that

$$\mathcal{H}(\mathbb{M}_{\mathbf{d}}) = \lceil \log_2(\mathbf{d}) \rceil.\tag{4.41}$$

The fact that $\mathcal{H}(\mathbb{M}_2) = 1$ and induction hence establish item (i). Observe that the fact that $\mathcal{D}(\mathbb{M}_2) = (2, 3, 1)$ assure that for all $i \in \mathbb{N}$ it holds that

$$\mathbb{D}_i(\mathbb{M}_2) \leq 3 = 3 \lceil \frac{2}{2^i} \rceil.\tag{4.42}$$

Moreover, note that Proposition 2.1.2 and Lemma 2.2.2 imply that for all $\mathbf{d} \in \{2, 3, 4, \dots\}$, $i \in \mathbb{N}$ it holds that

$$\mathbb{D}_i(\mathbb{M}_{2\mathbf{d}}) = \begin{cases} 3\mathbf{d} & : i = 1 \\
\mathbb{D}_{i-1}(\mathbb{M}_{\mathbf{d}}) & : i \geq 2 \end{cases}\tag{4.43}$$

and

$$\mathbb{D}_i(\mathbb{M}_{2\mathbf{d}-1}) = \begin{cases} 3\mathbf{d} - 1 & : i = 1 \\
\mathbb{D}_{i-1}(\mathbb{M}_{\mathbf{d}}) & : i \geq 2. \end{cases}\tag{4.44}$$

This assures that for all $\mathbf{d} \in \{2, 4, 6, \dots\}$ it holds that

$$\mathbb{D}_1(\mathbb{M}_{\mathbf{d}}) = 3(\frac{\mathbf{d}}{2}) = 3 \lceil \frac{\mathbf{d}}{2} \rceil.\tag{4.45}$$

In addition, observe that $(4.44)$ ensures that for all $\mathbf{d} \in \{3, 5, 7, \dots\}$ it holds that

$$\mathbb{D}_1(\mathbb{M}_{\mathbf{d}}) = 3 \lceil \frac{\mathbf{d}}{2} \rceil - 1 \leq 3 \lceil \frac{\mathbf{d}}{2} \rceil.\tag{4.46}$$

This and $(4.45)$ show that for all $\mathbf{d} \in \{2, 3, 4, \dots\}$ it holds that

$$\mathbb{D}_1(\mathbb{M}_{\mathbf{d}}) \leq 3 \lceil \frac{\mathbf{d}}{2} \rceil.\tag{4.47}$$

Next note that $(4.43)$ demonstrates that for all $\mathbf{d} \in \{4, 6, 8, \dots\}$, $i \in \{2, 3, 4, \dots\}$ with $\mathbb{D}_{i-1}(\mathbb{M}_{\frac{\mathbf{d}}{2}}) \leq 3 \lceil \frac{\mathbf{d}}{2} \frac{1}{2^{i-1}} \rceil$ it holds that

$$\mathbb{D}_i(\mathbb{M}_{\mathbf{d}}) = \mathbb{D}_{i-1}(\mathbb{M}_{\frac{\mathbf{d}}{2}}) \leq 3 \lceil \frac{\mathbf{d}}{2} \frac{1}{2^{i-1}} \rceil = 3 \lceil \frac{\mathbf{d}}{2^i} \rceil.\tag{4.48}$$