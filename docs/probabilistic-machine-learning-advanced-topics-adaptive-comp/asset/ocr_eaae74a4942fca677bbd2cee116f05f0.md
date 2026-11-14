This convention will simplify our chain rule statement below. When \(n_1 = n_2 = m = 1\), both sub-matrices are scalar, and \(\partial g_1(x, y)\) recovers the partial derivative that might otherwise be written in named variable notation as:

\(\frac{\partial}{\partial x}g(x, y) . \quad (6.19)\)

However, the expression \(\partial g_1\) bears a meaning on its own (as a function) whereas the expression \(\frac{\partial g}{\partial x}\) may be ambiguous without further context. Again composing operators lets us write higher-order derivatives. For instance, \(\partial_2\partial_1g(x, y) \in \mathbb{R}^{m \times n_1 \times n_2}\), and if \(m = 1\), the Hessian of \(g\) at \((x, y)\) is:

\(\begin{pmatrix} \partial_1\partial_1g(x, y) & \partial_1\partial_2g(x, y) \\ \partial_2\partial_1g(x, y) & \partial_2\partial_2g(x, y) \end{pmatrix} . \quad (6.20)\)

# **Composition and fan-out.** If \(f = g \circ h\) for some \(h : \mathbb{R}^n \to \mathbb{R}^p\) and \(g : \mathbb{R}^p \to \mathbb{R}^m\), then the **chain rule of calculus** observes that:

\(\partial f(x) = \partial g(h(x)) \circ \partial h(x) \text{ for all } x \in \mathbb{R}^n \quad (6.21)\)

How does this interact with our notation for multi-argument functions? For one, it can lead us to consider expressions with **fan-out**, where several sub-expressions are functions of the same input. For instance, assume two functions \(a : \mathbb{R}^n \to \mathbb{R}^{m_1}\) and \(b : \mathbb{R}^n \to \mathbb{R}^{m_2}\), and that:

\(f(x) = g(a(x), b(x)) \quad (6.22)\)

for some function \(g\). Abbreviating \(h(x) = (a(x), b(x))\) so that \(f(x) = g(h(x))\), Equations (6.16) and (6.21) tell us that:

\(\partial f(x) = \partial g(h(x)) \circ \partial h(x) \quad (6.23)\)

\(= \partial_1g(a(x), b(x)) \circ \partial a(x) + \partial_2g(a(x), b(x)) \circ \partial b(x) \quad (6.24)\)

Note that \(+\) is meant pointwise here. It also follows from the above that if instead:

\(f(x, y) = g(a(x), b(y)) \quad (6.25)\)

in other words, if we write multiple arguments but exhibit no fan-out, then:

\(\partial_1 f(x, y) = \partial_1 g(a(x), b(y)) \circ \partial a(x) , \text{ and} \quad (6.26)\)

\(\partial_2 f(x, y) = \partial_2 g(a(x), b(y)) \circ \partial b(y) \quad (6.27)\)

Composition and fan-out rules for derivatives are what let us break down a complex derivative calculation into simpler ones. This is what automatic differentiation techniques rely on when processing the sort of elaborate numerical computations that turn up in modern machine learning and numerical programming.