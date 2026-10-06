# C Representing Functionals

Proposition 2.15 ([74, Proposition 3.9]) Let $C$ be a convex cone of a real normed space $(Y, \|\cdot\|)$, and let $\psi$ be a $-C$ representing convex functional with the property that $y \in Y$ we have

$y \in -C \iff \psi(y) = 0.$

Then it holds

$0^* \in \partial\psi(0Y).$

**Proof** every $y \in Y$, we have

$\psi(y) \geq \psi(0Y) + 0Y^*(y)$$
$$\begin{array}{r} ==0 \\ ==0 \end{array}$$

implying $0^* \in \partial\psi(0Y).$

Finally, we give an additional relation between the dual cone and the subdifferential.

**Theorem 2.3** ([74, Theorem 3.2]) Let $C$ be a convex cone of a real normed space $(Y, \|\cdot\|)$, and let $\psi$ be a $-C$ representing convex functional with the property that for $y \in Y$ we have

$y \in -C \iff \psi(y) = 0.$

Let $\psi'(0Y)$ denote the directional derivative of $\psi$ at $0Y$. Under the additional assumption

$\ell \in C^* \exists \alpha_{\ell} > 0 : \alpha_{\ell}(y) \leq \psi'(0Y)(y)$ for all $y \in Y.$

it then holds

$C^* \subseteq cone (\partial\psi(0Y)).$

**Proof** Let $\ell \in C^*$ be arbitrarily chosen. By assumption (2.15), there exists $\alpha_{\ell} > 0$ so that

$\alpha_{\ell}(y) \leq \psi'(0Y)(y)$ for all $y \in Y.$

With Theorem 1.3 (a), we obtain $\alpha_{\ell} \in \partial\psi(0Y)$ implying $\ell \in \frac{1}{\alpha_{\ell}}\partial\psi(0Y)$. Consequently, we have $\ell \in cone (\partial\psi(0Y)).$

Figure 2.7 illustrates assumption (2.15) of Theorem 2.3. This assumption is stronger than the condition $0^* \in \partial\psi(0Y)$ shown in Proposition 2.15. Although the equivalence $y \in -C \iff \psi(y) = 0$ is not explicitly used in the proof