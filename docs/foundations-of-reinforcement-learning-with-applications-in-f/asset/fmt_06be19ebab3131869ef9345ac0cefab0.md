
Finally, we write a method `argmax` that takes as input an Iterable of `x` values and returns the `x` value that maximizes 𝔼[*f*(*x*; *w*)]\[*y*\].

![](images/comp06_5.jpg)

The above code for `FunctionApprox` and `Gradient` is in the file `rl/function_approx.py`. `rl/function_approx.py` also contains the convenience methods `__add__` (to add two `FunctionApprox`), `__mul__` (to multiply a `FunctionApprox` with a real-valued scalar), and `__call__` (to treat a `FunctionApprox` object syntactically as a function taking an `x: X` as input, essentially a shorthand for `evaluate` on a single `x` value). `__add__` and `__mul__` are meant to perform element-wise addition and scalar-multiplication on the internal parameters `w` of the Function Approximation (see [Appendix F](#appF.xhtml#appF) on viewing Function Approximations as Vector Spaces). Likewise, it contains the methods `__add__` and `__mul__` for the `Gradient` class that simply delegates to the `__add__` and `__mul__` methods of the `FunctionApprox` within `Gradient`, and it also contains the method `zero` that returns a `Gradient` which is uniformly zero for each of the parameter values.

Now we are ready to cover a concrete but simple function approximation—the case of linear function approximation.

## 6.2 LINEAR FUNCTION APPROXIMATION

We define a sequence of feature functions

$$\\begin{array}{r} \\left. \\phi\_{j}:\\mathcal{X}\\rightarrow{\\mathbb{R}}\\text{~for~each~}j = 1,2,\\ldots,m \\right. \\\\ \\end{array}$$  

and we define `ϕ`:𝒳→ℝ^(*m*) as:

$$\\begin{array}{r} {\\phi(x) = (\\phi\_{1}(x),\\phi\_{2}(x),\\ldots,\\phi\_{m}(x))\\text{~for~all~}x \\in \\mathcal{X}} \\\\ \\end{array}$$  

We treat `ϕ`(*x*) as a column vector for all *x* ∈ 𝒳.

For linear function approximation, the internal parameters `w` are represented as a weights column-vector **w** = (*w*[1], *w*[2], …, *w*[*m*]) ∈ ℝ^(*m*). Linear function approximation is based on the assumption of a Gaussian distribution for *y*|*x* with mean

$$\\begin{array}{r} {\\mathbb{E}\_{M}\\lbrack y|x\\rbrack = {\\sum\\limits\_{j = 1}^{m}\\phi\_{j}}(x) \\cdot w\_{j} = \\phi{(x)}^{T} \\cdot \\mathbf{\\mathbf{w}}} \\\\ \\end{array}$$  

and constant variance *σ*², i.e.,

$$\\begin{array}{r} {{\\mathbb{P}}\\lbrack y|x\\rbrack = f(x;\\mathbf{\\mathbf{w}})(y) = \\frac{1}{\\sqrt{2\\pi\\sigma^{2}}} \\cdot e^{- \\frac{{(y - \\phi{(x)}^{T} \\cdot \\mathbf{\\mathbf{w}})}^{2}}{2\\sigma^{2}}}} \\\\ \\end{array}$$  

So, the cross-entropy loss function (ignoring constant terms associated with *σ*²) for a given set of data points \[*x*[*i*], *y*[*i*]|1 ≤ *i* ≤ *n*\] is defined as:

$$\\begin{array}{r} {\\mathcal{L}(\\mathbf{\\mathbf{w}}) = \\frac{1}{2n} \\cdot {\\sum\\limits\_{i = 1}^{n}{(\\phi{(x\_{i})}^{T} \\cdot \\mathbf{\\mathbf{w}} - y\_{i})}^{2}}} \\\\ \\end{array}$$  

Note that this loss function is identical to the mean-squared-error of the linear (in **w**) predictions *ϕ*(*x*[*i*])^(*T*) ⋅ **w** relative to the response values *y*[*i*] associated with the predictor values *x*[*i*], over all 1 ≤ *i* ≤ *n*.

If we include *L*² regularization (with *λ* as the regularization coefficient), then the regularized loss function is:

$$\\begin{array}{r} {\\mathcal{L}(\\mathbf{\\mathbf{w}}) = \\frac{1}{2n}({\\sum\\limits\_{i = 1}^{n}{(\\phi{(x\_{i})}^{T} \\cdot \\mathbf{\\mathbf{w}} - y\_{i})}^{2}}) + \\frac{1}{2} \\cdot \\lambda \\cdot |\\mathbf{\\mathbf{w}}|^{2}} \\\\ \\end{array}$$  

The gradient of ℒ(**w**) with respect to **w** works out to:

$$\\begin{array}{r} {\\nabla\_{\\mathbf{\\mathbf{w}}}\\mathcal{L}(\\mathbf{\\mathbf{w}}) = \\frac{1}{n} \\cdot ({\\sum\\limits\_{i = 1}^{n}\\phi}(x\_{i}) \\cdot (\\phi{(x\_{i})}^{T} \\cdot \\mathbf{\\mathbf{w}} - y\_{i})) + \\lambda \\cdot \\mathbf{\\mathbf{w}}} \\\\ \\end{array}$$  

We had said previously that for each concrete function approximation that we'd want to implement, if the Objective `Obj`(*x*[*i*], *y*[*i*]) is the cross-entropy loss function, we can identify a model-computed value `Out`(*x*[*i*]) (either the output of the model or an intermediate computation of the model) such that $\\frac{\\partial Obj(x\_{i},y\_{i})}{\\partial Out(x\_{i})}$ is equal to the prediction error 𝔼[*M*]\[*y*|*x*[*i*]\] − *y*[*i*] (for each training data point (*x*[*i*], *y*[*i*])), and we can come up with a numerical algorithm to compute ∇[*w*]`Out`(*x*[*i*]), so that by chain-rule, we have the required gradient ∇[*w*]`Obj`(*x*[*i*], *y*[*i*]) (without regularization). In the case of this linear function approximation, the model-computed value `Out`(*x*[*i*]) is simply the model prediction for predictor variable `x`[*i*], i.e.,

$$\\begin{array}{r} {Out(x\_{i}) = \\mathbb{E}\_{M}\\lbrack y|x\_{i}\\rbrack = \\phi{(x\_{i})}^{T} \\cdot \\mathbf{\\mathbf{w}}} \\\\ \\end{array}$$  

This is confirmed by noting that with `Obj`(*x*[*i*], *y*[*i*]) set to be the cross-entropy loss function ℒ(**w**) and `Out`(*x*[*i*]) set to be the model prediction *ϕ*(*x*[*i*])^(*T*) ⋅ **w** (for training data point (*x*[*i*], *y*[*i*])),

$$\\begin{array}{r} {\\frac{\\partial Obj(x\_{i},y\_{i})}{\\partial Out(x\_{i})} = \\phi{(x\_{i})}^{T} \\cdot \\mathbf{\\mathbf{w}} - y\_{i} = \\mathbb{E}\_{M}\\lbrack y|x\_{i}\\rbrack - y\_{i}} \\\\ \\end{array}$$  

$$\\begin{array}{r} {\\nabla\_{\\mathbf{\\mathbf{w}}}Out(x\_{i}) = \\nabla\_{\\mathbf{\\mathbf{w}}}(\\phi{(x\_{i})}^{T} \\cdot \\mathbf{\\mathbf{w}}) = \\phi(x\_{i})} \\\\ \\end{array}$$  

We can solve for **w**^(\*) by incremental estimation using gradient descent (change in **w** proportional to the gradient estimate of ℒ(**w**) with respect to **w**). If the (*x*[*t*], *y*[*t*]) data at time *t* is:

$$\\begin{array}{r} {\\lbrack(x\_{t,i},y\_{t,i})|1 \\leq i \\leq n\_{t}\\rbrack,} \\\\ \\end{array}$$  

then the gradient estimate 𝒢[(*x*[*t*], *y*[*t*])](**w**[*t*]) at time *t* is given by:

$$\\begin{array}{r} {\\mathcal{G}\_{(x\_{t},y\_{t})}(\\mathbf{\\mathbf{w}}\_{t}) = \\frac{1}{n} \\cdot ({\\sum\\limits\_{i = 1}^{n\_{t}}\\phi}(x\_{t,i}) \\cdot (\\phi{(x\_{t,i})}^{T} \\cdot \\mathbf{\\mathbf{w}}\_{t} - y\_{t,i})) + \\lambda \\cdot \\mathbf{\\mathbf{w}}\_{t}} \\\\ \\end{array}$$  

which can be interpreted as the mean (over the data in iteration *t*) of the feature vectors *ϕ*(*x*[*t*, *i*]) weighted by the (scalar) linear prediction errors *ϕ*(*x*[*t*, *i*])^(*T*) ⋅ **w**[*t*] − *y*[*t*, *i*] (plus regularization term *λ* ⋅ **w**[*t*]).

Then, the update to the weights vector **w** is given by:

$$\\begin{array}{r} {\\mathbf{\\mathbf{w}}\_{t + 1} = \\mathbf{\\mathbf{w}}\_{t} - \\alpha\_{t} \\cdot \\mathcal{G}\_{(x\_{t},y\_{t})}(\\mathbf{\\mathbf{w}}\_{t})} \\\\ \\end{array}$$  

where `α`[*t*] is the learning rate for the gradient descent at time *t*. To facilitate numerical convergence, we require `α`[*t*] to be an appropriate function of time *t*. There are a number of numerical algorithms to achieve the appropriate time-trajectory of `α`[*t*]. We shall go with one such numerical algorithm—ADAM ([Kingma and Ba 2015](#bib01.xhtml#refbib_35)), which we shall use not just for linear function approximation but later also for the deep neural network function approximation. Before we write code for linear function approximation, we need to write some helper code to implement the ADAM gradient descent algorithm.
