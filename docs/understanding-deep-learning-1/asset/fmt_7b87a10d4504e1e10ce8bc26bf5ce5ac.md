
![Figure 4.5 Computation for the deep network in figure 4.4. a–c) The inputs to the second hidden layer (i.e., the pre-activations) are three piecewise linear functions where the “joints” between the linear regions are at the same places (see figure 3.6). d–f) Each piecewise linear function is clipped to zero by the ReLU activation function. g–i) These clipped functions are then weighted with parameters `c4-fig-5030.jpg`, `c4-fig-5031.jpg`, and `c4-fig-5032.jpg`, respectively. j) Finally, the clipped and weighted functions are summed and an offset `c4-fig-5033.jpg` that controls the overall height is added.](images/c4-fig-0005.jpg)

[Figure 4.5](#c004.xhtml#c4-fig-0005a) Computation for the deep network in [figure 4.4](#c004.xhtml#c4-fig-0004). a–c) The inputs to the second hidden layer (i.e., the pre-activations) are three piecewise linear functions where the “joints” between the linear regions are at the same places (see figure 3.6). d–f) Each piecewise linear function is clipped to zero by the ReLU activation function. g–i) These clipped functions are then weighted with parameters ![c4-fig-5030.jpg](images/c4-fig-5030.jpg), ![c4-fig-5031.jpg](images/c4-fig-5031.jpg), and ![c4-fig-5032.jpg](images/c4-fig-5032.jpg), respectively. j) Finally, the clipped and weighted functions are summed and an offset ![c4-fig-5033.jpg](images/c4-fig-5033.jpg) that controls the overall height is added.

In conclusion, we can either think of each layer as “folding” the input space or as creating new functions, which are clipped (creating new regions) and then recombined. The former view emphasizes the dependencies in the output function but not how clipping creates new joints, and the latter has the opposite emphasis. Ultimately, both descriptions provide only partial insight into how deep neural networks operate. Regardless, it's important not to lose sight of the fact that this is still merely an equation relating input `x` to output `y′`. Indeed, we can combine equations 4.7–4.9 to get one expression:

![c4-fig-5010.jpg](images/c4-fig-5010.jpg)

 (4.10)

although this is admittedly rather difficult to understand.

### 4.3.1 Hyperparameters

We can extend the deep network construction to more than two hidden layers; modern networks might have more than a hundred layers with thousands of hidden units at each layer. The number of hidden units in each layer is referred to as the *width* of the network, and the number of hidden layers as the *depth*. The total number of hidden units is a measure of the network's *capacity*.

We denote the number of layers as `K` and the number of hidden units in each layer as `D[1]`, `D[2]`, …, `D[K]`. These are examples of *hyperparameters*. They are quantities chosen before we learn the model parameters (i.e., the slope and intercept terms). For fixed hyperparameters (e.g., `K` = 2 layers with `D[k]` = 3 hidden units in each), the model describes a family of functions, and the parameters determine the particular function. Hence, when we also consider the hyperparameters, we can think of neural networks as representing a family of families of functions relating input to output.

***

Problem 4.2

***

## 4.4 Matrix notation

We have seen that a deep neural network consists of linear transformations alternating with activation functions. We could equivalently describe equations 4.7–4.9 in matrix notation as:

![c4-fig-5011.jpg](images/c4-fig-5011.jpg)

 (4.11)

![c4-fig-5012.jpg](images/c4-fig-5012.jpg)

 (4.12)

***

Appendix B.3

Matrices

***

and

![c4-fig-5013.jpg](images/c4-fig-5013.jpg)

 (4.13)

or even more compactly in matrix notation as:

![c4-fig-5014.jpg](images/c4-fig-5014.jpg)

 (4.14)

where, in each case, the function `a[•]` applies the activation function separately to every element of its vector input.

### 4.4.1 General formulation

This notation becomes cumbersome for networks with many layers. Hence, from now on, we will describe the vector of hidden units at layer `k` as `h[k]`, the vector of biases (intercepts) that contribute to hidden layer `k` + 1 as `β[k]`, and the weights (slopes) that are applied to the `k^(th)` layer and contribute to the (`k` + 1)*^(th)* layer as `Ω[k]`. A general deep network `y` = f[`x`, `ϕ`] with `K` layers can now be written as:

![c4-fig-5015.jpg](images/c4-fig-5015.jpg)

 (4.15)

The parameters `ϕ` of this model comprise all of these weight matrices and bias vectors ![c4-fig-5016.jpg](images/c4-fig-5016.jpg).

If the `k^(th)` layer has `D[k]` hidden units, then the bias vector `β[k−1]` will be of size `D[k]`. The last bias vector `β[K]` has the size `D[o]` of the output. The first weight matrix `Ω[0]` has size `D[1]` × `D[i]` where `Di` is the size of the input. The last weight matrix `Ω[K]` is `D[o]` × `D[K]`, and the remaining matrices `Ω[k]` are `D[k+1]` × `D[k]` ([figure 4.6](#c004.xhtml#c4-fig-0006)).

***

Notebook 4.3

Deep networks

***

![Figure 4.6 Matrix notation for network with Di = 3-dimensional input x, Do = 2-dimensional output y, and K = 3 hidden layers h1, h2, and h3 of dimensions D1 = 4, D2 = 2, and D3 = 3 respectively. The weights are stored in matrices Ωk that pre-multiply the activations from the preceding layer to create the pre-activations at the subsequent layer. For example, the weight matrix Ω1 that computes the pre-activations at h2 from the activations at h1 has dimension 2 × 4. It is applied to the four hidden units in layer one and creates the inputs to the two hidden units at layer two. The biases are stored in vectors βk and have the dimension of the layer into which they feed. For example, the bias vector β2 is length three because layer h3 contains three hidden units.](images/c4-fig-0006.jpg)

[Figure 4.6](#c004.xhtml#c4-fig-0006a) Matrix notation for network with `D[i]` = 3-dimensional input `x`, `D[o]` = 2-dimensional output `y`, and `K` = 3 hidden layers `h[1]`, `h[2]`, and `h[3]` of dimensions `D[1]` = 4, `D[2]` = 2, and `D[3]` = 3 respectively. The weights are stored in matrices `Ω[k]` that pre-multiply the activations from the preceding layer to create the pre-activations at the subsequent layer. For example, the weight matrix `Ω[1]` that computes the pre-activations at `h[2]` from the activations at `h[1]` has dimension 2 × 4. It is applied to the four hidden units in layer one and creates the inputs to the two hidden units at layer two. The biases are stored in vectors `β[k]` and have the dimension of the layer into which they feed. For example, the bias vector `β[2]` is length three because layer `h[3]` contains three hidden units.

We can equivalently write the network as a single function:

![c4-fig-5017.jpg](images/c4-fig-5017.jpg)

 (4.16)

***

Problems 4.3–4.6

***

## 4.5 Shallow vs. deep neural networks

Chapter 3 discussed shallow networks (with a single hidden layer), and here we have described deep networks (with multiple hidden layers). We now compare these models.

### 4.5.1 Ability to approximate different functions

In section 3.2, we argued that shallow neural networks with enough capacity (hidden units) could model any continuous function arbitrarily closely. In this chapter, we saw that a deep network with two hidden layers could represent the composition of two shallow networks. If the second of these networks computes the identity function, then this deep network replicates a single shallow network. Hence, it can also approximate any continuous function arbitrarily closely given sufficient capacity.

***

Problem 4.7

***

### 4.5.2 Number of linear regions per parameter

A shallow network with one input, one output, and `D >` 2 hidden units can create up to `D` + 1 linear regions and is defined by 3`D` + 1 parameters. A deep network with one input, one output, and `K` layers of `D >` 2 hidden units can create a function with up to (`D` + 1)^`K` linear regions using 3`D` + 1 + (`K` − 1)`D`(`D` + 1) parameters.

***
