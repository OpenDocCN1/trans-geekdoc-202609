![](bbox=[0.22, 0.12, 0.48, 0.28])

![](bbox=[0.6, 0.12, 0.85, 0.28])

Figure B.2: (a) A function that has a jump discontinuity at the marked point. From https://en.wikipedia.org/wiki/Derivative. Used with kind permission of Wikipedia author Jacj. (b) The absolute value function is continuous, but is not differentiable at x = 0. From https://en.wikipedia.org/wiki/Derivative. Used with kind permission of Wikipedia author Qef.

![](bbox=[0.38, 0.4, 0.6, 0.62])

Figure B.3: For a Lipschitz continuous function f, there exists a double cone (white) whose origin can be moved along the graph of f so that the whole graph always stays outside the double cone. From https://en.wikipedia.org/wiki/lipschitz_continuity. Used with kind permission of Wikipedia author Taschee.

# B.2.1.4 Linear and affine functions

A function $f : \mathbb{R}^n \to \mathbb{R}$ is called a **linear function** if

$f(c_1\mathbf{x} + c_2\mathbf{y}) = c_1 f(\mathbf{x}) + c_2 f(\mathbf{y})$ (B.3)

for all scalars $c_1$, $c_2$ and vectors $\mathbf{x}$, $\mathbf{y}$. Note that this implies $f(c_1\mathbf{x}) = c_1 f(\mathbf{x})$. A function is called **affine** if it is the sum of a linear function plus a constant offset. (Sometimes we use the word “linear” to include an offset term as well.)

The importance of linear functions is that we can predict the output of a linear function in terms of its response to simple inputs. To see this, note that we can represent any vector $\mathbf{x} \in \mathbb{R}^n$ as a sum of $n$ unit vectors $\mathbf{e}_i = (0,\dots,0,1,0,\dots,0)$

$\mathbf{x} = \sum_{i=1}^{n} x_i \mathbf{e}_i$ (B.4)

(See Sec. C.1.2 for details.) Hence we can predict the output of $f(\mathbf{x})$ as a sum of **impulse responses**