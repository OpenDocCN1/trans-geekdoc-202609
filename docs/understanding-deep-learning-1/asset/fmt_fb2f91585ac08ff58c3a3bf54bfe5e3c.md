
## 3.4 Shallow neural networks: general case

We have described several example shallow networks to help develop intuition about how they work. We now define a general equation for a shallow neural network `y = f[x, ϕ]` that maps a multi-dimensional input `x ∈ ℝ^D_x` to a multi-dimensional output `y ∈ ℝ^D_y` using `h ∈ ℝ^D` hidden units. Each hidden unit is computed as:

```
h_i = a[θ_i^T x + ϕ_i]
```
 (3.11)

and these are combined linearly to create the output:

```
y = Θ h + b
```
 (3.12)

where `a[•]` is a nonlinear activation function. The model has parameters `ϕ = {θ[••], ϕ[••]}`. [Figure 3.11](#c003.xhtml#c3-fig-0011) shows an example with three inputs, three hidden units, and two outputs.

---

**Problems 3.14–3.17**

---

![Figure 3.11 Visualization of neural network with three inputs and two outputs. This network has twenty parameters. There are fifteen slopes (indicated by arrows) and five offsets (not shown).](images/c3-fig-0011.jpg)

[Figure 3.11](#c003.xhtml#c3-fig-0011a) Visualization of neural network with three inputs and two outputs. This network has twenty parameters. There are fifteen slopes (indicated by arrows) and five offsets (not shown).

---

The activation function permits the model to describe nonlinear relations between input and the output, and as such, it must be nonlinear itself; with no activation function, or a linear activation function, the overall mapping from input to output would be restricted to be linear. Many different activation functions have been tried (see [figure 3.13](#c003.xhtml#c3-fig-0013)), but the most common choice is the ReLU ([figure 3.1](#c003.xhtml#c3-fig-0001)), which has the merit of being easily interpretable. With ReLU activations, the network divides the input space into convex polytopes defined by the intersections of hyperplanes computed by the "joints" in the ReLU functions. Each convex polytope contains a different linear function. The polytopes are the same for each output, but the linear functions they contain can differ.

---

**Notebook 3.4**

Activation functions

---

## 3.5 Terminology

We conclude this chapter by introducing some terminology. Regrettably, neural networks have a lot of associated jargon. They are often referred to in terms of *layers*. The left of [figure 3.12](#c003.xhtml#c3-fig-0012) is the *input layer*, the center is the *hidden layer*, and to the right is the *output layer*. We would say that the network in [figure 3.12](#c003.xhtml#c3-fig-0012) has one hidden layer containing four hidden units. The hidden units themselves are sometimes referred to as *neurons*. When we pass data through the network, the values of the inputs to the hidden layer (i.e., before the ReLU functions are applied) are termed *pre-activations*. The values at the hidden layer (i.e., after the ReLU functions) are termed *activations*.

![Figure 3.12 Terminology. A shallow network consists of an input layer, a hidden layer, and an output layer. Each layer is connected to the next by forward connections (arrows). For this reason, these models are referred to as feed-forward networks. When every variable in one layer connects to every variable in the next, we call this a fully connected network. Each connection represents a slope parameter in the underlying equation, and these parameters are termed weights. The variables in the hidden layer are termed neurons or hidden units. The values feeding into the hidden units are termed pre-activations, and the values at the hidden units (i.e., after the ReLU function is applied) are termed activations.](images/c3-fig-0012.jpg)

[Figure 3.12](#c003.xhtml#c3-fig-0012a) Terminology. A shallow network consists of an input layer, a hidden layer, and an output layer. Each layer is connected to the next by forward connections (arrows). For this reason, these models are referred to as feed-forward networks. When every variable in one layer connects to every variable in the next, we call this a fully connected network. Each connection represents a slope parameter in the underlying equation, and these parameters are termed weights. The variables in the hidden layer are termed neurons or hidden units. The values feeding into the hidden units are termed pre-activations, and the values at the hidden units (i.e., after the ReLU function is applied) are termed activations.

For historical reasons, any neural network with at least one hidden layer is also called a *multi-layer perceptron*, or *MLP* for short. Networks with one hidden layer (as described in this chapter) are sometimes referred to as *shallow neural networks*. Networks with multiple hidden layers (as described in the next chapter) are referred to as *deep neural networks*. Neural networks in which the connections form an acyclic graph (i.e., a graph with no loops, as in all the examples in this chapter) are referred to as *feed-forward networks*. If every element in one layer connects to every element in the next (as in all the examples in this chapter), the network is *fully connected.* These connections represent slope parameters in the underlying equations and are referred to as *network weights*. The offset parameters (not shown in [figure 3.12](#c003.xhtml#c3-fig-0012)) are called *biases*.

## 3.6 Summary

Shallow neural networks have one hidden layer. They (i) compute several linear functions of the input, (ii) pass each result through an activation function, and then (iii) take a linear combination of these activations to form the outputs. Shallow neural networks make predictions `y` based on inputs `x` by dividing the input space into a continuous surface of piecewise linear regions. With enough hidden units (neurons), shallow neural networks can approximate any continuous function to arbitrary precision.

Chapter 4 discusses deep neural networks, which extend the models from this chapter by adding more hidden layers. Chapters 5–7 describe how to train these models.

## Notes

**"Neural" networks:** If the models in this chapter are just functions, why are they called "neural networks"? The connection is, unfortunately, tenuous. Visualizations like [figure 3.12](#c003.xhtml#c3-fig-0012) consist of nodes (inputs, hidden units, and outputs) that are densely connected to one another. This bears a superficial similarity to neurons in the mammalian brain, which also have dense connections. However, there is scant evidence that brain computation works in the same way as neural networks, and it is unhelpful to think about biology going forward.
