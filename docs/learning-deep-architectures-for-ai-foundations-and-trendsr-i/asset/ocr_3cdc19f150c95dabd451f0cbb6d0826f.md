# Local vs Non-Local Generalization

The local generalization issue is directly connected to the literature on the curse of dimensionality, but the results we cite show what matters for generalization is not dimensionality, but instead the number of “variations” of the function we wish to obtain after learning. For example, if the function represented by the model is piecewise-constant (e.g., decision trees), then the question is the number of pieces required to approximate properly the target function. There are connections between the number of variations and the input dimension: one can readily design families of target functions for which the number of variations is exponential in the input dimension, such as the parity function with d inputs.

Architectures based on matching templates can be thought of having two levels. The first level is a set of templates which can be matched to the input. A template unit will output a value that indicates the degree of matching. The second level combines these values, typically with a simple linear combination (an OR-like operation), in order to estimate the desired output. One can think of this linear combination as performing a kind of interpolation in order to produce an answer in the region of input space that is between the templates.

The prototypical example of architectures based on matching templates is the kernel machine [66]

```
$f(x) = b + \sum \alpha_i K(x, x_i),
```

$b$ and $\alpha_i$ form the second level, while on the first level, the kernel function $K(x,x_i)$ matches the input $\mathbf{x}$ to the training example $\mathbf{x}_i$, which sums over all of the input patterns in the training set). In the above equation, $f(x)$ could be for example, the discriminant of a classifier, or the output of a regression predictor.

A kernel is local when $K(\mathbf{x},\mathbf{x}_i) > \rho$ is true for $\mathbf{x}$ in some connected region around $\mathbf{x}_i$ (for some threshold $ho$). The size of that region can usually be controlled by a hyper-parameter of the kernel function. An example of local kernel is the Gaussian kernel $K(\mathbf{x},\mathbf{x}_i) = e^{-|\mathbf{x}-\mathbf{x}_i||^2/sigma^2}$, where $\sigma$ controls the size of the region around $\mathbf{x}_i$. We can see the Gaussian kernel as computing a soft conjunction, because