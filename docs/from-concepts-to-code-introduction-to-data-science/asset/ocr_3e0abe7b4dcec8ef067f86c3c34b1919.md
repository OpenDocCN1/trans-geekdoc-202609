It is completely valid for a function to map two or more inputs to the same output. Figure 8.1 shows the graph of the function $f(x) = x^2$. Both $-x$ and $x$ will map to the same value $f(-x) = f(x)$ for all $x$. For example, $f(-2) = f(2) = 4$.

![](bbox=[0.315, 0.255, 0.679, 0.42])

FIGURE 8.1: The function $f(x) = x^2$

# Function Composition

**Function composition** is an operation $\circ$ that takes two functions $f$ and $g$ and produces a new function $h = g \circ f$ such that $h(x) = g(f(x))$. The function $f$ is applied, followed by the function $g$. For cases where two functions are composed, say $k \circ g \circ f$, we apply the functions from right to left, taking them two at a time. For example, $k \circ g \circ f = k(g(f(x))) = k(h(x))$, by applying the equation $h(x) = g(f(x))$. The evaluation of this nested composition is supported by the associative property of function composition.

Consider an example with two functions $f(x) = x+1$ and $g(x) = \sqrt{x}$, each defined for the set $x \ge 0$. We form the function composition $h(x) = g(f(x)) = \sqrt{x+1}$. We can compute $h(3)$ and $h(-2)$. The first case is possible, with $h(3) = \sqrt{3+1} = 2$. The second case is undefined, since $h(-2) = \sqrt{-2+1} = \sqrt{-1}$. Hence, composition will only work where the domain of $h$ is defined. In this case, the domain $x \ge -1$.

Function composition is particularly important in data science because machine learning models apply a sequence of functions to data. In computer vision, image pixels can be arranged in layers and aggregated averaged many times to infer whether an object of interest can be found.