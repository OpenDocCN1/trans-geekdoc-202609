
# 反向传播方法

The method `backward_propagation` is the most important method of `DNNApprox`, calculating ∇`w[l]`*`Obj` for all `l = 0, 1, …, L`, for some objective function `Obj`. We had said previously that for each concrete function approximation that we'd want to implement, if the Objective `Obj(x[i], y[i])` is the cross-entropy loss function, we can identify a model-computed value `Out(x[i])` (either the output of the model or an intermediate computation of the model) such that $\\frac{\\partial Obj(x_{i},y_{i})}{\\partial Out(x_{i})}$ is equal to the prediction error 𝔼[*M*]\[*y*|*x*[*i*]] − *y*[*i*] (for each training data point (*x*[*i*], *y*[*i*])), and we can come up with a numerical algorithm to compute ∇`w`*`Out(x[i])`, so that by chain-rule, we have the required gradient ∇`w`*`Obj(x[i], y[i])` (without regularization). In the case of this DNN function approximation, the model-computed value `Out(x[i])` is `s[L]`. Thus,

$$
\\begin{array}{r} {\\frac{\\partial Obj(x\_{i},y\_{i})}{\\partial Out(x\_{i})} = \\frac{\\partial\\mathcal{L}}{\\partial s\_{L}} = P\_{L} = o\_{L} - y\_{i} = \\mathbb{E}\_{M}\\lbrack y|x\_{i}\\rbrack - y\_{i}} \\\\ \\end{array}
$$  

`backward_propagation` takes two inputs:

1.  `fwd_prop`: Sequence[`np.ndarray`] which represents the output of `forward_propagation` except for the last element (which is the final output of the neural network), i.e., a sequence of `L + 1` 2-D numpy arrays representing the inputs to layers `l = 0, 1, …L` (for each of the Iterable of `x`-values provided as input to the neural network).

2.  `obj_deriv_out`: `np.ndarray`, which represents the partial derivative of an arbitrary objective function `Obj` with respect to an arbitrary model-produced value `Out`, evaluated at each of the Iterable of (*x*, `y`) pairs that are provided as training data.

If we generalize the objective function from the cross-entropy loss function ℒ to an arbitrary objective function `Obj` and define `P[l]` to be ∇`s[l]`*`Obj` (generalized from ∇`s[l]`ℒ), then the output of `backward_propagation` would be equal to `P[l]`⋅`i[l]`^(*T*) (i.e., without the regularization term) for all `l = 0, 1, …L`.

The first step in `backward_propagation` is to set `P[L]` (variable `deriv` in the code) equal to `obj_deriv_out` (which in the case of cross-entropy loss as `Obj` and `s[L]` as `Out`, reduces to the prediction error 𝔼[*M*]\[*y*|*x*[*i*]] − *y*[*i*]). As we walk back through the layers of the DNN, the variable `deriv` represents `P[l]` = ∇`s[l]`*`Obj`, evaluated for each of the values made available by `fwd_prop` (note that `deriv` is updated in each iteration of the loop reflecting [Theorem 6.3.1](#chapter6.xhtml#theo6_3_1): `P[l]` = (**w**[`l` + **1**]^(*T*) ⋅ **P**[`l` + **1**])^∘*g*[`l`]^′(**s**[`l`])). Note also that the returned list `back_prop` is populated with the result of Equation (6.4): ∇`w[l]`*`Obj` = **P**[`l`] ⋅ **i**[`l`]^(*T*).

The method `objective_gradient` (from `FunctionApprox`) takes as input an Iterable of (*x*, `y`) pairs and the $\\frac{\\partial Obj}{\\partial Out}$ function, invokes the `forward_propagation` method (to be passed as input to `backward_propagation`), then invokes `backward_propagation`, and finally adds on the regularization term *λ* ⋅ **w**[`l`] to the output of `backward_propagation` to return the gradient ∇`w[l]`*`Obj` for all `l = 0, 1, …L`.

The method `update_with_gradient` (from `FunctionApprox`) takes as input a gradient (e.g., ∇`w[l]`*`Obj`), updates the weights `w[l]` for all `l = 0, 1, …, L` along with the ADAM cache updates (invoking the `update` method of the `Weights` class to ensure there are no in-place updates), and returns a new instance of `DNNApprox` that contains the updated weights.

Finally, the method `solve` (from `FunctionApprox`) utilizes the method `iterate_updates` (inherited from `FunctionApprox`) along with the method `within` to perform a best-fit of the weights that minimizes the cross-entropy loss function (basically, a series of incremental updates based on gradient descent).

![](images/comp06_11.jpg)![](images/comp06_11_2.jpg)![](images/comp06_11_3.jpg)

All of the above code is in the file `rl/function_approx.py`.

A comprehensive treatment of function approximations using Deep Neural Networks can be found in the Deep Learning book by Goodfellow, Bengio, Courville ([Goodfellow, Bengio, and Courville 2016](#bib01.xhtml#refbib_28)).

Let us now write some code to create function approximations with `LinearFunctionApprox` and `DNNApprox`, given a stream of data from a simple data model—one that has some noise around a linear function. Here's some code to create an Iterator of (*x*, `y`) pairs (where `x` = (`x`[1], `x`[2], `x`[3])) for the data model:

$$
\\begin{array}{r} {y = 2 + 10x\_{1} + 4x\_{2} - 6x\_{3} + \\mathcal{N}(0,0.3)} \\\\ \\end{array}
$$  

![](images/comp06_12.jpg)

Next, we wrap this in an Iterator that returns a certain number of (*x*, `y`) pairs upon each request for data points.

![](images/comp06_13.jpg)

Now let's write a function to create a `LinearFunctionApprox`.

![](images/comp06_14.jpg)

Likewise, let's write a function to create a `DNNApprox` with 1 hidden layer with 2 neurons and a little bit of regularization since this deep neural network is somewhat over-parameterized to fit the data generated from the linear data model with noise.

![](images/comp06_15.jpg)

Now let's write some code to do a `direct_solve` with the `LinearFunctionApprox` based on the data from the data model we have set up.

![](images/comp06_16.jpg)

Running the above code, we see that the Root-Mean-Squared-Error (`direct_solve_rmse`) is indeed 0.3, matching the standard deviation of the noise in the linear data model (which is used above to generate the training data as well as the test data).

Now let us perform stochastic gradient descent with instances of `LinearFunctionApprox` and `DNNApprox` and examine the Root-Mean-Squared-Errors on the two function approximations as a function of number of iterations in the gradient descent.

![](images/comp06_17.jpg)

The plot of `linear_model_rmse_seq` and `dnn_model_rmse_seq` is shown in [Figure 6.1](#chapter6.xhtml#fig6_1).

![Figure 6.1 SGD Convergence](images/fig6_1.jpg)

[Figure 6.1](#chapter6.xhtml#b6fig6_1) SGD Convergence

# 6.4 Tabular as a Form of FunctionApprox

Now we consider a simple case where we have a fixed and finite set of `x`-values 𝒳 = {`x`[1],`x`[2],…,*x*[*n*]}, and any data set of (*x*, `y`) pairs made available to us needs to have its `x`-values from within this finite set 𝒳. The prediction 𝔼[`y`|`x`] for each `x` ∈ 𝒳 needs to be calculated only from the `y`-values associated with this `x` within the data set of (*x*, `y`) pairs. In other words, the `y`-values in the data associated with other `x` should not influence the prediction for `x`. Since we'd like the prediction for `x` to be 𝔼[`y`|`x`], it would make sense for the prediction for a given `x` to be *some sort of average* of all the `y`-values associated with `x` within the data set of (*x*, `y`) pairs seen so far. This simple case is referred to as *Tabular* because we can store all `x` ∈ 𝒳 together with their corresponding predictions 𝔼[`y`|`x`] in a finite data structure (loosely referred to as a “table”).

So the calculations for Tabular prediction of 𝔼[`y`|`x`] is particularly straightforward. What is interesting though is the fact that Tabular prediction actually fits the interface of `FunctionApprox` in terms of the following three methods that we have emphasized as the essence of `FunctionApprox`:

*   the `solve` method, that would simply take the average of all the `y`-values associated with each `x` in the given data set, and store those averages in a dictionary data structure.
