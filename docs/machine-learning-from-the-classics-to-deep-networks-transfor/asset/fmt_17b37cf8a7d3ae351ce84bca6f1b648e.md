
### 18.4.3 Beyond the gradient descent rationale

The other path to follow to improve upon the convergence rate of the gradient descent-based backpropagation algorithm, at the expense of increased complexity, is to resort to schemes that involve, in one way or another, information related to the second-order derivatives. We have already discussed such families in this book, for example, the Newton family introduced in Chapter [6](#Chp006_249-291_B9780443292385000123.xhtml). For each one of the available families, a backpropagation version can be derived to serve the needs of the neural network training. We will not delve into details, because the concept remains the same as that discussed for the gradient descent. The difference is that now second-order derivatives have, also, to be propagated backwards. For more details, the interested reader can look at [16,30,66,113,228] and the references therein.

In [8,94,106], schemes based on the conjugate gradient philosophy have been developed, and members of the Newton family have been proposed in, for example, [10,164,211]. In all these schemes, the computation of the elements of the Hessian matrix, that is,

```
∂²J / (∂θⱼₖʳ ∂θⱼ'ₖ'ʳ')
```

![Equation](images/B978044329238500024X/si260.png)

is required.
