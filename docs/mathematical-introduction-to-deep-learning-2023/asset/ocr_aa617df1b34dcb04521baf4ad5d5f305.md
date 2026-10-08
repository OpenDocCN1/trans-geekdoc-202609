$\bar{\mathfrak{R}}_{p} \in (0, \infty]$ the extended real number given by

$\bar{\mathfrak{R}}_{p}=\sup \left\{c \in[0, \infty):\left[\begin{array}{c}\exists \mathbb{R}-\text { Banach space }(E,\|\|\|): \\ \exists \text { probability space }(\Omega, \mathcal{F}, \mathbb{P}): \\ \exists \mathbb{P}\text {-Rademacher family }(r_{j})_{j \in \mathbb{N}}: \\ \exists k \in \mathbb{N}: \exists x_{1}, x_{2}, \ldots, x_{k} \in E \backslash\{0\}:\end{array}\right.\left.\begin{array}{l}\left(\mathbb{E}\left[\left\|\sum_{j=1}^{k} r_{j} x_{j}\right\|^{p}\right]\right)^{1 / p}=c\left(\mathbb{E}\left[\left\|\sum_{j=1}^{k} r_{j} x_{j}\right\|^{2}\right]\right)^{1 / 2}\end{array}\right.\right\}$

($cf$. Definition 13.1.2).

**Lemma 13.1.4.** It holds for all $p \in[2, \infty)$ that

$\bar{\mathfrak{R}}_{p} \leq \sqrt{p-1}<\infty$

($cf$. Definition 13.1.3).

Proof of Lemma 13.1.4. Note that (13.5) and Grohs et al. $[179$, Corollary 2.5] imply (13.6). The proof of Lemma 13.1.4 is thus complete.

**Proposition 13.1.5.** Let $d, M \in \mathbb{N}$, $p \in[2, \infty)$, let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $X_{j}: \Omega \rightarrow \mathbb{R}^{d}, j \in\{1,2, \ldots, M\}$, be independent random variables, and assume

$\max _{j \in\{1,2, \ldots, M\}} \mathbb{E}\|X_{j}\|_{2}<\infty$

($cf$. Definition 3.3.4). Then

$\left(\mathbb{E}\left[\left\|\sum_{j=1}^{M} X_{j}\right\|_{2}^{p}\right]\right)^{1 / p} \leq 2 \bar{\mathfrak{R}}_{p} \sum_{j=1}^{M}\left(\mathbb{E}\left[\|X_{j}-\mathbb{E}[X_{j}]\|_{2}^{2}\right]\right)^{2 / p}\right]^{1 / 2}$

($cf$. Definition 13.1.3 and Lemma 13.1.4).

Proof of Proposition 13.1.5. Observe that (13.5) and Cox et al. $[86$, Corollary 5.11] ensure (13.6). The proof of Proposition 13.1.5 is thus complete.

**Corollary 13.1.6.** Let $d, M \in \mathbb{N}$, $p \in[2, \infty)$, let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $X_{j}: \Omega \rightarrow \mathbb{R}^{d}, j \in\{1,2, \ldots, M\}$, be independent random variables, and assume

$\max _{j \in\{1,2, \ldots, M\}} \mathbb{E}\|X_{j}\|_{2}<\infty$

($cf$. Definition 3.3.4). Then

$\left(\mathbb{E}\left[\left\|\frac{1}{M} \sum_{j=1}^{M} X_{j}\right\|_{2}^{p}\right]^{p}\right)^{1 / p} \leq \frac{2 \sqrt{p-1}}{\sqrt{M}}\left[\max _{j \in\{1,2, \ldots, M\}}\left(\mathbb{E}\left[\|X_{j}-\mathbb{E}[X_{j}]\|_{2}^{2}\right]\right)^{2 / p}\right].$