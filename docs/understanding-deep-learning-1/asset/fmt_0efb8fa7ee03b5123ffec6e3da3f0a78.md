
[Figure 4.9](#c004.xhtml#c4-fig-0009a) Hidden unit activations for problem 4.8. a) First hidden unit has a joint at position `x = 1/6` and a slope of one in the active region. b) Second hidden unit has a joint at position `x = 2/6` and a slope of one in the active region. c) Third hidden unit has a joint at position `x = 4/6` and a slope of minus one in the active region.

**Problem 4.9\*** Following problem 4.8, is it possible to create a function with three linear regions that oscillates back and forth between output values of zero and one using a shallow network with two hidden units? Is it possible to create a function with five linear regions that oscillates in the same way using a shallow network with four hidden units?

**Problem 4.10** Consider a deep neural network with a single input, a single output, and `K` hidden layers, each of which contains `D` hidden units. Show that this network will have a total of `3*D + 1 + (K − 1)*D*(D + 1)` parameters.

**Problem 4.11\*** Consider two neural networks that map a scalar input `x` to a scalar output `y`. The first network is shallow and has `D = 95` hidden units. The second is deep and has `K = 10` layers, each containing `D = 5` hidden units. How many parameters does each network have? How many linear regions can each network make? Which would run faster?

# Chapter 5 Loss functions

The last three chapters described linear regression, shallow neural networks, and deep neural networks. Each represents a family of functions that map input to output, where the particular member of the family is determined by the model parameters `ϕ`. When we train these models, we seek the parameters that produce the best possible mapping from input to output for the task we are considering. This chapter defines what is meant by the “best possible” mapping.

That definition requires a training dataset `{x[i], y[i]}` of input/output pairs. A *loss function* or *cost function* `L[ϕ]` returns a single number that describes the mismatch between the model predictions `f[x[i], ϕ]` and their corresponding ground-truth outputs `y[i]`. During training, we seek parameter values `ϕ` that minimize the loss and hence map the training inputs to the outputs as closely as possible. We saw one example of a loss function in chapter 2; the least squares loss function is suitable for univariate regression problems for which the target is a real number `y ∈ ℝ`. It computes the sum of the squares of the deviations between the model predictions `f[x[i], ϕ]` and the true values `y[i]`.

* * *

Appendix A

Number sets

* * *

This chapter provides a framework that both justifies the choice of the least squares criterion for real-valued outputs and allows us to build loss functions for other prediction types. We consider *binary classification*, where the prediction `y ∈ {0, 1}` is one of two categories, *multiclass classification*, where the prediction `y ∈ {1, 2, …, K}` is one of `K` categories, and more complex cases. In the following two chapters, we address model training, where the goal is to find the parameter values that minimize these loss functions.

## 5.1 Maximum likelihood

In this section, we develop a recipe for constructing loss functions. Consider a model `f[x, ϕ]` with parameters `ϕ` that computes an output from input `x`. Until now, we have implied that the model directly computes a prediction `y`. We now shift perspective and consider the model as computing a conditional probability distribution `Pr(y|x)` over possible outputs `y` given input `x`. The loss encourages each training output `y[i]` to have a high probability under the distribution `Pr(y[i]|x[i])` computed from the corresponding input `x[i]` ([figure 5.1](#c005.xhtml#c5-fig-0001)).

Appendix C.1.3

Conditional probability

* * *

![Figure 5.1 Predicting distributions over outputs. a) Regression task, where the goal is to predict a real-valued output y from the input x based on training data {xi, yi} (orange points). For each input value x, the machine learning model predicts a distribution Pr(y∣x) over the output y ∈ ℝ (cyan curves show distributions for x = 2.0 and x = 7.0). The loss function aims to maximize the probability of the observed training outputs yi under the distribution predicted from the corresponding inputs xi. b) To predict discrete classes y ∈{1, 2, 3, 4} in a classification task, we use a discrete probability distribution, so the model predicts a different histogram over the four possible values of yi for each value of xi. c) To predict counts y ∈ {0, 1, 2,…} and d) direction y ∈ (−π, π], we use distributions defined over positive integers and circular domains, respectively.](images/c5-fig-0001.jpg)

[Figure 5.1](#c005.xhtml#c5-fig-0001a) Predicting distributions over outputs. a) Regression task, where the goal is to predict a real-valued output `y` from the input `x` based on training data `{x[i], y[i]}` (orange points). For each input value `x`, the machine learning model predicts a distribution `Pr(y|x)` over the output `y ∈ ℝ` (cyan curves show distributions for `x = 2.0` and `x = 7.0`). The loss function aims to maximize the probability of the observed training outputs `y[i]` under the distribution predicted from the corresponding inputs `x[i]`. b) To predict discrete classes `y ∈{1, 2, 3, 4}` in a classification task, we use a discrete probability distribution, so the model predicts a different histogram over the four possible values of `y[i]` for each value of `x[i]`. c) To predict counts `y ∈ {0, 1, 2,…}` and d) direction `y ∈ (−π, π]`, we use distributions defined over positive integers and circular domains, respectively.

* * *

### 5.1.1 Computing a distribution over outputs

This raises the question of exactly how a model `f[x, ϕ]` can be adapted to compute a probability distribution. The solution is simple. First, we choose a parametric distribution `Pr(y|θ)` defined on the output domain `y`. Then we use the network to compute one or more of the parameters `θ` of this distribution.

For example, suppose the prediction domain is the set of real numbers, so `y ∈ ℝ`. Here, we might choose the univariate normal distribution, which is defined on ℝ. This distribution is defined by the mean `μ` and variance `σ²`, so `θ = {μ, σ²}`. The machine learning model might predict the mean `μ`, and the variance `σ²` could be treated as an unknown constant.

### 5.1.2 Maximum likelihood criterion

The model now computes different distribution parameters `θ[i] = f[x[i], ϕ]` for each training input `x[i]`. Each observed training output `y[i]` should have high probability under its corresponding distribution `Pr(y[i]|θ[i])`. Hence, we choose the model parameters `ϕ` so that they maximize the combined probability across all `I` training examples:

![c5-fig-5001.jpg](images/c5-fig-5001.jpg)

 (5.1)

The combined probability term is the *likelihood* of the parameters, and hence equation 5.1 is known as the *maximum likelihood* criterion.[¹](#c005.xhtml#c5-fn-0001)

Here we are implicitly making two assumptions. First, we assume that the data are identically distributed (the form of the probability distribution over the outputs `y[i]` is the same for each data point). Second, we assume that the conditional distributions `Pr(y[i]|x[i])` of the output given the input are independent, so the total likelihood of the training data decomposes as:

![c5-fig-5002.jpg](images/c5-fig-5002.jpg)

 (5.2)

* * *

Appendix C.1.5

Independence

* * *

In other words, we assume the data are *independent and identically distributed* (*i.i.d.*).

### 5.1.3 Maximizing log-likelihood
