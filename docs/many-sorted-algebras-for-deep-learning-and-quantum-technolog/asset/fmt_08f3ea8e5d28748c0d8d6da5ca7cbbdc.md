
As in the previous example, a rectangular pulse function is created using the `NN`; this time, it is illustrated in [Fig. 2.3](#Ch002_21-40_B9780443136979000266.xhtml#f0020). As mentioned, the internal structure of each node is portrayed with symbols. Nodes `N[1,1]` and `N[2,1]` are identical except that the biases are opposite in sign. Again, the activation functions in both nodes are `T(w[*j*1]x+b[*j*1])=sgn \[max (x−b[*j*1], 0)\]`. Note that in node `N[1,2]` the activation function is not utilized; thus the identity function is illustrated within the square. Also, in this node two inputs arrive. Accordingly, two distinct weights are utilized, indicative of heights `h` and `−h`. These are each enclosed within a circle. Together, these weights are entries or tuples within the row vector `w[12]=(h −h)`. Finally, as before, node `N[2,2]` is not employed in this `NN`.

![Figure 2.3 Symbolic calculations for NN square wave pulse creation. NN, Neural net.](Images/F000266f02-03-9780443136979.jpg)

[Figure 2.3](#Ch002_21-40_B9780443136979000266.xhtml#Bf0020) Symbolic calculations for `NN` square wave pulse creation. `NN`, Neural net.

## 2.6 Activation functions and cost functions for neural net

Conventional `NN`s have nodes utilizing affine functions followed by an activation function `F`, which is almost always nonlinear. Common attributes for an activation function are that when the output of the affine map is the input to `F`, then `F` often returns values in \[−1, 1\] or \[0, 1\]. In the latter situation, the output is understood as a probability value. More importantly, when backpropagation is employed `F` must have a continuous derivative. When this is not the case, a noncontinuous derivative for `F` has the property that very small changes in the input can cause drastic deviations in the value of the output derivative. See the example below.

### Example 2.4

The function `f: R→R`, where `f(x)=x² sin(1/x)` for `x` nonzero, and `f(0)=0`. This function is differentiable with `f′(x)=2x sin(1/x)−cos(1/x)` for `x` nonzero, and `f′(0)=0`. So, for instance, if `x[1]=0` and `x[2]=1/(1000π)`, then `f′{x[1])=0`, but `f′(x[2])` is one.

Activation function must often be chosen such that when used in backpropagation the gradient does not vanish or explode. When the gradient becomes too small, weights and biases more or less stay invariant. On the other hand, exploding gradients cause instability, which almost never results in learning. This is a large problem in `RNN`s due to the feedback; however, modified `RNN`s described in [Section 2.11](#Ch002_21-40_B9780443136979000266.xhtml#s0060) were created to overcome some of these problems.

Several commonly used activation functions are listed below along with their range and their derivative, when the latter exists. These functions are defined on the real line,
*   Sigmoid: `T(x)=1/(1+e^(−x))`; range: (0, 1); derivative: `T′(x)=T(x) (1−T(x))`
*   Hyperbolic Tangent: `T(x)=2 (1–e^(−2x))^(−1)–1`, for `x` not zero, and −1 at zero; range: \[−1, 1\]; derivative: `T′(x)=(1–T²(x))`
*   ReLU: `T(x)=0` for `x < 0` and `T(x)=x` otherwise; range: \[0, ∞); derivative: `T′(x)=0` for `x<0` and `T′(x)=1` for `x>0`; `T′(0)` does not exist.
*   Soft log: `T(x)=log(1+e^(x))`; range: (0, ∞); derivative: `T′(x)=1/ (1+e^(−x))`
*   ArcTan: `T(x)=tan^(−1)(x)`; range: (−1, 1); derivative: `T′(x)=(1+x²)^(−1)`.

One of the most commonly used activation-type functions for multiclass classification is `Softmax`. It is almost always employed on outputs from the final layer of a `NN`. Accordingly, from this perspective, `Softmax` can be thought to be a pseudo node. It is of the type many inputs to many outputs. Therefore, outputs from all `n` nodes in the final layer, `N[m]`, enter `Softmax`. Say that these outputs are `x[1]`, …, `x[n]`; then
`Softmax (x_i) = (e^{x_i}) / (sum_j e^{x_j})`![Equation](Images/F000266si19.png). Moreover, it is assumed that the pseudo node keeps track of the inputs sent from all final nodes, `N[i,m]`, and sends as outputs the `Softmax` calculations in order. In this case, the output from any actual final node can itself be thought to be a probability. Because, after the final node the output value enter the pseudo node, it gets calculated by `Softmax` and takes on values in \[0, 1\]. And the sum of all the final node outputs when converted by `Softmax` is one.

### Example 2.5

Say that three final nodes exist in a `NN`. Each such node sends its output to the pseudo node `Softmax`. If the actual outputs of each final node are given in order by (2, 1, 0.5), these values enter the pseudo node. The `Softmax` operation is applied three times and provides in order the actual probability type vector that approximately equals (0.6, 0.25, 0.15). From this output, the final node one results in the correct classification.

Various objective or cost functions are employed in machine learning. Most of the time, these functions are convex. In `R¹`, `f` is convex in an interval `[a, b]`, which means that for `x` and `y` in this interval, `x<y`, and any `λ` in `[0, 1]`, `f (λx+(1−λ) y)` is less than or equal to `λ f (x)+(1−λ) f (y)`. This means the chord for `f` in the interval `[x, y]` is larger or equal to the value of `f` in this interval. Convex objective functions are used since in this case local minima are also the global minima. In later chapters, nonconvex objective functions are employed making use of simulated annealing and in particular quantum annealing techniques. Annealing-type operations often enable global minimization to occur ([Laarhoven and Aarts, 1987](#Ch002_21-40_B9780443136979000266.xhtml#bib7)).

### Example 2.6

Refer to [Example 2.1](#Ch002_21-40_B9780443136979000266.xhtml#enun1), where the k-means procedure is illustrated using the one norm objective function. In this case, since data from `R¹` was employed, the one norm is `‖v‖[1]=|v|`. For `λ` in `[0, 1]` and any `x` and `y` in `R¹`, `|λ x+(1−λ)|` is less than or equal to `λ|x| + (1−λ)|y|` by the triangle inequality. So this objective function is convex.

Other important convex cost functions are quadratic, for instance, least squares and methods involving variance reduction such as square error.

## 2.7 Classification with a single-node neural net

Recall, from [Section 2.5](#Ch002_21-40_B9780443136979000266.xhtml#s0030), that nodes `N[ij]` within an `NN` have addresses exactly like entries within a matrix; the quantity `(i, j)` represents the ith row and jth column, respectively.

A circle is used, each enclosing an individual scalar-valued weight represented as a tuple within the row vector `w[ij]`. Moreover, the circle itself symbolizes a multiplication operation. Also within the node, a triangle representing addition symbolizes adding the scalar bias `b[ij]` to the sum of weighted inputs to node `N[ij]`. Finally, a square is employed in identifying the activation function, `T` or `F`, and causes the activation function to activate and provide a scalar output. [Section 2.6](#Ch002_21-40_B9780443136979000266.xhtml#s0035) provides a description of several activation functions. In this section, a single-node `NN` is employed. For this situation, subscripts won’t be used; moreover, the input value `v` will be a real number in a specified interval. It will enter the node and then enter the circle-type figure containing the specified weight. Multiplication by the weight occurs here. The output from the circle diagram is labeled `x` and enters the triangle, wherein the bias value `b` is added to `x`. The output from the triangle is `y`, and this value enters the square-type figure. Here, the activation function `F` is evaluated, and `z=F(y)` is the output value. This whole scenario is explained in [Example 2.7](#Ch002_21-40_B9780443136979000266.xhtml#enun7) and is illustrated in [Fig. 2.4](#Ch002_21-40_B9780443136979000266.xhtml#f0025).

![Figure 2.4 Classification using NN with noncontinuous activation. NN, Neural net.](Images/F000266f02-04-9780443136979.jpg)
