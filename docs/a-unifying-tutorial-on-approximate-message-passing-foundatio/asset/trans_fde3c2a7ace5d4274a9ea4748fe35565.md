

\( B \in \mathcal{G} \). 如果 \( Y : (\Omega, \mathcal{F}, \mathsf{P}) \to \mathbb{R} \) 是一个满足 \( \mathsf{E}(|Y|) < \infty \) 的随机变量，则存在一个 \( \mathcal{G} \)-可测随机变量 \( Z = \mathsf{E}(Y | \mathcal{G}) \)，使得对所有 \( E \in \mathcal{G} \) 都有 \( \mathsf{E}(Z \mathbb{1}_E) = \mathsf{E}(Y \mathbb{1}_E) \)（Dudley, 2002, Chapter 10.1）。我们称 \( Z \) 为 *给定* \( \mathcal{G} \) *下 Y 的条件期望*，并注意它在 \( \mathsf{P}|_\mathcal{G} \)-几乎必然意义下是唯一的。对于 \( F \in \mathcal{F} \)，我们还记 \( \mathsf{P}(F | \mathcal{G}) := \mathsf{E}(\mathbb{1}_F | \mathcal{G}) \)。

如果 \( X \) 是从 \( (\Omega, \mathcal{F}, \mathsf{P}) \) 到可测空间 \( (\mathcal{X}, \mathcal{A}) \) 的可测函数，我们称 \( P_{X|\mathcal{G}} : \Omega \times \mathcal{A} \to [0, 1] \) 为 *给定* \( \mathcal{G} \) *下 X 的（正则）条件分布*，如果

- (i) 对每个 \( \omega \in \Omega \)，集合函数 \( P_{X|\mathcal{G}}(\omega, \cdot) \) 是 \( \mathcal{A} \) 上的概率测度；
- (ii) 对每个 \( A \in \mathcal{A} \)，映射 \( P_{X|\mathcal{G}}(\cdot, A) \) 是 \( \mathcal{G} \)-可测的，且对 \( \mathsf{P}|_\mathcal{G} \)-几乎每个 \( \omega \in \Omega \) 都有 \( P_{X|\mathcal{G}}(\omega, A) = \mathsf{P}(X^{-1}(A) | \mathcal{G})(\omega) \)，因此对所有 \( E \in \mathcal{G} \) 都有 \( \mathsf{P}(X^{-1}(A) \cap E) = \int_E P_{X|\mathcal{G}}(\omega, A) \, d\mathsf{P}(\omega) \)。

我们称 \( (\mathcal{X}, \mathcal{A}) \) 为 *Borel 空间*，如果存在一个 Borel 子集 \( S \subseteq [0, 1] \)（配备在 \( [0, 1] \) 上的 Borel \( \sigma \)-代数对 \( S \) 的限制 \( \mathcal{B}_S \）以及一个双射 \( f : (\mathcal{X}, \mathcal{A}) \to (S, \mathcal{B}_S) \)，使得 \( f \) 和 \( f^{-1} \) 都是可测的。Borel 空间 \( (\mathcal{X}, \mathcal{A}) \) 的例子包括 *Polish 空间*（即可分、完全可度化的拓扑空间）\( \mathcal{X} \)，配备其 Borel \( \sigma \)-代数 \( \mathcal{A} \)（Kallenberg, 1997, Theorem A1.6）。

每当 \( (\mathcal{X}, \mathcal{A}) \) 是 Borel 空间时，就存在条件分布 \( P_{X|\mathcal{G}} \)，而且，如果 \( P' \) 是另一个这样的条件分布，则对 \( \mathsf{P}|_\mathcal{G} \)-几乎每个 \( \omega \in \Omega \) 都有 \( P'(\omega, \cdot) = P_{X|\mathcal{G}}(\omega, \cdot) \)；参见 Kallenberg (1997, Theorem 5.3) 和 Dudley (2002, Theorem 10.2.2)。为简洁起见，我们将写作 ‘\( X \) 在事件 \( \Omega_0 \in \mathcal{G} \) 上给定 \( \mathcal{G} \) 具有条件分布 \( P \equiv P_\omega \)’ 来表示存在条件分布 \( P_{X|\mathcal{G}} \)，并且我们可以对 \( \mathsf{P}|_\mathcal{G} \)-几乎每个 \( \omega \in \Omega_0 \) 取 \( P_{X|\mathcal{G}}(\omega, \cdot) = P_\omega(\cdot) \)。当我们省略短语 ‘on an event \( \Omega_0 \in \mathcal{G} \)’ 时，我们的意思是该声明对 \( \mathsf{P}|_\mathcal{G} \)-几乎每个 \( \omega \in \Omega \) 成立。

对于可测的 \( X, X' : (\Omega, \mathcal{F}, \mathsf{P}) \to (\mathcal{X}, \mathcal{A}) \)，如果存在分别对 \( X, X' \) 的条件分布 \( P_{X|\mathcal{G}} \) 和 \( P'_{X'|\mathcal{G}} \)，且对 \( \mathsf{P}|_\mathcal{G} \)-几乎每个 \( \omega \in \Omega \) 都有 \( P_\omega(\cdot) \equiv P_{X|\mathcal{G}}(\omega, \cdot) = P'_{X'|\mathcal{G}}(\omega, \cdot) \equiv P'_\omega(\cdot) \)，则我们称 \( X, X' \) 在给定 \( \mathcal{G} \) 下 *同分布*，并记作 \( X \stackrel{d}{=}_{\mathcal{G}} X' \)。

### Remark B.4.

例如，$X$ 在 \( (\mathcal{X}, \mathcal{A}) \) 上服从分布 \( Q \) 且与 \( \mathcal{G} \) 独立，当且仅当对所有 \( \omega \in \Omega \) 都有 \( X \) 的条件分布 \( P_\omega = Q \)。

### Remark B.5.

令 \(X: (\Omega, \mathcal{F}, \mathbb{P}) \to (\mathcal{X}, \mathcal{A})\) 如上文所述，并考虑重要的特殊情况，其中 \(\mathcal{G} = \sigma(Y)\) 对某些从 \((\Omega, \mathcal{F}, \mathbb{P})\) 到可测空间 \((\mathcal{Y}, \mathcal{B})\) 的可测映射 \(Y\)。用 \(P\) 表示 \((X, Y)\) 的联合分布：\((\Omega, \mathcal{F}, \mathbb{P}) \to (\mathcal{X} \times \mathcal{Y}, \mathcal{A} \otimes \mathcal{B})\)，并用 \(P^Y\) 表示 \(Y\) 在 \((\mathcal{Y}, \mathcal{B})\) 上的（边缘）分布。我们在此注意，随机变量 \(Z: (\Omega, \mathcal{F}, \mathbb{P}) \to \mathbb{R}\) 是 \(\sigma(Y)\)-可测的，当且仅当存在可测函数 \(g: (\mathcal{Y}, \mathcal{B}) \to \mathbb{R}\) 使得 \(Z = g \circ Y\)（即 \(Z(\omega)\) 仅通过 \(Y(\omega)\) 依赖于 \(\omega\)）；参见例如 Dudley (2002, Theorem 4.2.8)。利用这一事实和上述定义性质 (ii)，可以验证（如 Dudley, 2002, Theorem 10.2.1 所示），存在正则条件分布 \(P_{X|\sigma(Y)}: \Omega \times \mathcal{A} \to [0, 1]\)，当且仅当存在一族在 \( (\mathcal{X}, \mathcal{A}) \) 上的概率分布 \((Q_y)_{y \in \mathcal{Y}}\)，使得对每个 \( A \in \mathcal{A} \) 以下条件成立：

- (i) \(y \mapsto Q_y(A)\) 是从 \( (\mathcal{Y}, \mathcal{B}) \) 到 \( \mathbb{R} \) 的可测函数；
- (ii) \(P(A \times B) = \mathbb{P}(X^{-1}(A) \cap Y^{-1}(B)) = \int_B Q_y(A) \, dP^Y(y)\) 对所有 \( B \in \mathcal{B} \) 成立。

在此情形下，对于 \(\mathbb{P}|_{\sigma(Y)}\)-几乎每个 \( \omega \in \Omega \)，我们有对所有 \( A \in \mathcal{A} \) 都成立 \( P_{X|\sigma(Y)}(\omega, A) = Q_{Y(\omega)}(A) \)。注意，\((Q_y)_{y \in \mathcal{Y}}\) 仅在 \( P^Y \)-几乎必然意义下是唯一的，意思是如果 \((Q'_y)_{y \in \mathcal{Y}}\) 满足 (I) 且 \( Q_y = Q'_y \) 对 \( P^Y \)-几乎每个 \( y \in \mathcal{Y} \) 成立，则 \((Q'_y)_{y \in \mathcal{Y}}\) 也满足 (II)。鑒于 (I)，映射 \( (y, A) \mapsto Q_y(A) \) 被称为概率核。(II) 的一个解释是，它将 \((X, Y)\) 的联合分布 \( P \) 分解为 \( Y \) 的边缘分布 \( P^Y \) 和分布 \((Q_y)_{y \in \mathcal{Y}}\) 的概念表述得更为精确，即（对 \( P^Y \)-几乎每个 \( y \in \mathcal{Y} \)）我们可以将 \( Q_y \) 视为 "X 给定 \( Y = y \) 的条件分布"。确实，通过与常规乘积测度构造和 Fubini 定理的类比（例如 Dudley, 2002, Chapter 4.4），可以证明如果 \( \phi: (\mathcal{X} \times \mathcal{Y}, \mathcal{A} \otimes \mathcal{B}) \to \mathbb{R} \) 是 \( P \)-可积的（即 \( \phi \) 可测且 \( \mathbb{E}(|\phi(X, Y)|) < \infty \)），则

- (iii) 对所有 \( y \in \mathcal{Y} \)，\( x \mapsto \phi(x, y) \) 是 \(\mathcal{A}\)-可测的，且对 \( P^Y \)-几乎每个 \( y \in \mathcal{Y} \) 是 \( Q_y \)-可积的；
- (iv) \( y \mapsto \int_{\mathcal{X}} \phi(x, y) \, dQ_y(x) \) 是 \(\mathcal{B}\)-可测的且 \( P^Y \)-可积的；
- (v) \( \int_{\mathcal{X} \times \mathcal{Y}} \phi(x, y) \, dP(x, y) = \int_{\mathcal{Y}} \left( \int_{\mathcal{X}} \phi(x, y) \, dQ_y(x) \right) dP^Y(y) \)。

Fubini 定理的这一推广有时被称为 *分解定理*，它通过单调类论证从 (II) 推导而得；参见 Dudley (2002, Theorem 10.2.1(II)) 和 Kallenberg (1997, Theorem 5.4)。

### Lemma B.6.

令 \( (\mathcal{X}, \mathcal{A}), (\mathcal{Y}, \mathcal{B}) \) 为可测空间，令 \( (\mathcal{Z}, \mathcal{C}) \) 为 Borel 空间。令 \( \phi: (\mathcal{X} \times \mathcal{Y}, \mathcal{A} \otimes \mathcal{B}) \to (\mathcal{Z}, \mathcal{C}) \) 为可测函数，并令 \( \mathcal{G} \subseteq \mathcal{F} \) 为一个 \( \sigma \)-代数。

- (a) 如果 \( E \in \mathcal{G} \) 且 \( X_1, X_2: (\Omega, \mathcal{F}, \mathbb{P}) \to (\mathcal{X}, \mathcal{A}) \) 是分别给定 \( \mathcal{G} \) 且具有条件分布 \( P \equiv P_\omega \) 和 \( Q \equiv Q_\omega \) 的可测函数，则可测函数 \( X: (\Omega, \mathcal{F}, \mathbb{P}) \to (\mathcal{X}, \mathcal{A}) \)（在 \( E \) 上满足 \( X = X_1 \)，在 \( E^c \) 上满足 \( X = X_2 \)）给定 \( \mathcal{G} \) 具有条件分布 \( R(\cdot) \equiv R_\omega(\cdot) := P_\omega(\cdot)\mathbb{1}_{\{\omega \in E\}} + Q_\omega(\cdot)\mathbb{1}_{\{\omega \in E^c\}} \)。

- (b) 对于 \( D \in \mathcal{A} \otimes \mathcal{B} \) 和 \( y \in \mathcal{Y} \)，令 \( D^y := \{x \in \mathcal{X} : (x, y) \in D\} = \iota_y^{-1}(D) \)，其中 \( \iota_y: \mathcal{X} \to \mathcal{X} \times \mathcal{Y} \) 表示映射 \( x \mapsto (x, y) \)。固定 \( \Omega_0 \in \mathcal{G} \)。假设 \( X: (\Omega, \mathcal{F}, \mathbb{P}) \to (\mathcal{X}, \mathcal{A}) \) 在 \( \Omega_0 \) 上给定 \( \mathcal{G} \) 具有条件分布 \( P \equiv P_\omega \)，且 \( Y: (\Omega, \mathcal{F}, \mathbb{P}) \to (\mathcal{Y}, \mathcal{B}) \) 是 \( \mathcal{G} \)-可测的。如果 \( Z: (\Omega, \mathcal{F}, \mathbb{P}) \to (\mathcal{Z}, \mathcal{C}) \) 是在 \( \Omega_0 \) 上与 \( \phi(X, Y) \) 一致的可测映射，则 \( Z \) 在 \( \Omega_0 \) 上给定 \( \mathcal{G} \) 具有条件分布 \( \tilde{P} \equiv \tilde{P}_\omega = P_\omega \circ (\phi \circ \iota_{Y(\omega)})^{-1} \)，因此对所有 \( C \in \mathcal{C} \) 和 \( \omega \in \Omega_0 \) 都有 \( \tilde{P}_\omega(C) = P_\omega(\phi^{-1}(C)^{Y(\omega)}) \)。

- (c) 假设 \( X, X': (\Omega, \mathcal{F}, \mathbb{P}) \to (\mathcal{X}, \mathcal{A}) \) 是满足 \( X \stackrel{d}{=}|_\mathcal{G} X' \) 的可测函数，且 \( Y: (\Omega, \mathcal{F}, \mathbb{P}) \to (\mathcal{Y}, \mathcal{B}) \) 是 \( \mathcal{G} \)-可测的。则 \( \phi(X, Y) \stackrel{d}{=}|_\mathcal{G} \phi(X', Y) \)。

(b) 中的结果有一个直观解释。为简单起见，假设 \( \Omega_0 = \Omega \)，并固定 \( \omega \in \Omega \)。令 \( \mu := P_\omega \) 取自 \( X \) 给定 \( \mathcal{G} \) 的条件分布，并假设 \( Y \) 是 \( \mathcal{G} \)-可测的。

