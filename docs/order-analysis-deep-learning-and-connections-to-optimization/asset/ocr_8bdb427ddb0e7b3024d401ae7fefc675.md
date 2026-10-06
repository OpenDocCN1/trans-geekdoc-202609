# 6.6 Gradient Methods

111

![](bbox=[0.163, 0.091, 0.836, 0.439])

**Fig. 6.9** Level lines of the Rosenbrock function $f: \mathbb{R}^2 	o \mathbb{R}$ with $f(x_1, x_2) := 100(x_2 - x_1^2)^2 + (1 - x_1)^2$ for all $(x_1, x_2) \in \mathbb{R}^2$

(b) The gradient descent method basically determines a zero of the gradient of the objective function. The condition $
abla f(x)=0$ is a necessary optimality condition for a global as well as for a local minimal or maximal point. Since the method belongs to the class of descent methods, i.e., the function values of the iteration points are decreased from step to step (see Lemma 6.1), the gradient descent method runs to a local minimal point in the “valley” where it starts. To find a (global) minimal point, it is recommended to start the procedure repeatedly with different starting points and to select the one with the smallest objective value among all approximate solutions. An example of this is the Himmelblau function [60] $f: \mathbb{R}^2 	o \mathbb{R}$

$f(x_1, x_2) := (x_1^2 + x_2 - 11)^2 + (x_1 + x_2^2 - 7)^2$ for all $(x_1, x_2) \in \mathbb{R}^2$.

The Himmelblau function is illustrated by level lines in Fig. 6.10. It has four (global) minimal points (located approximately at $(3.58, -1.85)$, $(-3.78, -3.28)$, $(-2.81, 3.13)$, and $(3, 2))$ with $0$ as the value of the objective function, one local maximal point (located approximately at $(-0.27, -0.92)$), and four saddle points (located approximately at $(3.39, 0.07)$, $(-3.07, -0.08)$, $(-0.09, 2.88)$, and $(-0.13, -1.95))$ where $
abla f$ also vanishes.