*Proof of Lemma 12.2.22.* Throughout this proof, let \( \Phi: V \to V \) satisfy for all \( v \in V \) that \( \Phi(v) = rv \). Observe that Exercise 12.2.3 shows that

\begin{align} r\mathcal{C}_{(X, d), n} &= r \left[ \inf_{x_1, x_2, \ldots, x_n \in X} \sup_{v \in X} \min_{i \in \{1, 2, \ldots, n\}} d(x_i, v) \right] \\ &= \inf_{x_1, x_2, \ldots, x_n \in X} \sup_{v \in X} \min_{i \in \{1, 2, \ldots, n\}} \|rx_i - rv\| \\ &= \inf_{x_1, x_2, \ldots, x_n \in X} \sup_{v \in X} \min_{i \in \{1, 2, \ldots, n\}} \|\Phi(x_i) - \Phi(v)\| \\ &= \inf_{x_1, x_2, \ldots, x_n \in X} \sup_{v \in X} \min_{i \in \{1, 2, \ldots, n\}} d\bigl(\Phi(x_i), \Phi(v)\bigr) \\ &= \inf_{x_1, x_2, \ldots, x_n \in X} \sup_{v \in X} \min_{i \in \{1, 2, \ldots, n\}} d\bigl(\Phi(x_i), v\bigr) \\ &= \inf_{x_1, x_2, \ldots, x_n \in X} \sup_{v \in X} \min_{i \in \{1, 2, \ldots, n\}} d(x_i, v) = \mathcal{C}_{(\Phi(X), d(\Phi(x_i), v))}, n \end{align} \tag{12.126}

(cf. Definition 12.2.1). This establishes (12.125). The proof of Lemma 12.2.22 is thus complete.

# 12.2.4.7 Upper bounds for covering numbers

*Proposition 12.2.23.* *Let* $ (V, \| \cdot \|) $ *be a normed vector space with* dim(V) < ∞, *let* $ r, R \in (0, \infty), $ *$ X = \{ v \in V : \|v\| \leq R \} $, *and let* $ d : X \times X \to [0, \infty) $ *satisfy for all* $ v, w \in X $ *that* $ d(v, w) = \|v - w\| $. *Then*

\begin{equation} \mathcal{C}_{(X, d), r} \leq \begin{cases} 1 & : r \geq R \\ \left[ \frac{4R}{r} \right]^{\dim(V)} & : r < R \end{cases} \tag{12.127} \end{equation}

(cf. Definition 4.3.2).

*Proof of Proposition 12.2.23.* Throughout this proof, assume without loss of generality that dim(V) > 0, assume without loss of generality that $ r < R $, let $ N \in \mathbb{N} $ satisfy $ N = \dim(V) $, let $ n \in \mathbb{N} $ satisfy

\begin{equation} n = \left[ \left\lceil \frac{4R}{r} \right\rceil^N - 1 \right], \tag{12.128} \end{equation}

let $ \mathfrak{X} = \{ v \in V : \|v\| \leq 1 \} $, and let $ \mathfrak{d} : \mathfrak{X} \times \mathfrak{X} \to [0, \infty) $ satisfy for all $ v, w \in \mathfrak{X} $ that

\begin{equation} \mathfrak{d}(v, w) = \|v - w\| \tag{12.129} \end{equation}

(cf. Definition 4.2.6). Observe that Corollary 12.2.19 proves that

\begin{equation} \mathcal{C}_{(\mathfrak{X}, \mathfrak{d}), n} \leq 4(n + 1)^{-1/N} \tag{12.130} \end{equation}

(cf. Definition 12.2.1). The fact that

\begin{equation} n + 1 = \left[ \left\lceil \frac{4R}{r} \right\rceil^N - 1 \right] + 1 \geq \left[ \left\lceil \frac{4R}{r} \right\rceil^N - 1 \right] + 1 = \left[ \frac{4R}{r} \right]^N \tag{12.131} \end{equation}