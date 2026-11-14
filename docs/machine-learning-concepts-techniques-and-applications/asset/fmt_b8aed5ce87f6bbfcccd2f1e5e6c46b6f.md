
# Bayesian decision theory

`Bayesian decision theory` came long before version spaces, decision tree learning, and neural networks. It was studied in the field of statistical theory and more specifically, in the field of `pattern recognition`. `Bayesian decision theory` is at the basis of important learning schemes such as the `naïve Bayes classifier`, `Bayesian belief networks`, and the `expectation maximization (EM) algorithm`. `Bayesian decision theory` is also useful as it provides a framework within which many non-Bayesian classifiers can be studied.

## 7.2.1 Choosing Hypotheses

The `Bayes theorem` allows us to find the most probable hypothesis `h` from a set of candidate hypotheses `H` given the observed data `d`, that is, `P(h|d)`. We will discuss two common methods, namely `maximum a posteriori (MAP)` and `maximum likelihood (ML)`.

**Maximum a posteriori (MAP) hypothesis**: Choose the hypothesis with the highest a posteriori probability, given the data. In the MAP method we need to find the hypothesis `h` among the set of hypothesis `H` that maximizes the posterior probability `P(h|D)`. Now by applying the `Bayes theorem`, we need to find the hypothesis `h` that maximizes the likelihood of the data `d` for a given `h` and the prior probability of `h`. The prior probability of the data `d` does not affect the maximization for finding `h`, so that is not considered. Hence, we have the MAP hypothesis as follows (Equation 7.1):

(7.1)

$$
\begin{array}{ll}
{\mathbf{MAP}\ \textbf{Hypothesis},\mathbf{h}_{\mathbf{MAP}}} & {= \ \arg\ \mathbf{ma}\mathbf{x}_{\mathbf{h} \in \mathbf{H}}\mathbf{P}\left( \mathbf{h}\ \mid \mathbf{d} \right)} \\
& {= \ \arg\ \mathbf{ma}\mathbf{x}_{\mathbf{h} \in \mathbf{H}}\frac{\mathbf{P}\left( \mathbf{d}\ \mid \mathbf{h} \right)\mathbf{P}\left( \mathbf{h} \right)}{\mathbf{P}\left( \mathbf{d} \right)}} \\
& {= \ \arg\ \mathbf{ma}\mathbf{x}_{\mathbf{h} \in \mathbf{H}}\mathbf{P}\left( d\ \mid \mathbf{h} \right)\mathbf{P}\left( \mathbf{h} \right)}
\end{array}
$$

**Maximum likelihood estimate (ML)**: Assume that all hypotheses are equally likely a priori; then the best hypothesis is just the one that maximizes the likelihood (i.e., the probability of the data given the hypothesis). If every hypothesis in `H` is equally probable a priori, we only need to consider the likelihood of the data `D` given `h`, `P(D|h)`. This gives rise to `h[ML]` or the maximum likelihood, as follows (Equation 7.2):

(7.2)

```
h_ML = argmax_{h in H} P(D|h)
```

## 7.2.2 Bayesian Classification

Classification predicts the value of a class `c` given the value of an input feature vector `x`. From a probabilistic perspective, the goal is to find the conditional distribution `p(c|x)` using the `Bayes theorem`. Despite its conceptual simplicity, Bayes classification works well. The Bayesian classification rule states that given a set of classes and the respective posterior probabilities, it classifies an unknown feature vector according to when the posterior probability is maximum. There are two types of probabilistic models of classification, the `discriminative model` and the `generative model`.

### 7.2.2.1 Discriminative Model

The most common approach to probabilistic classification is to represent the conditional distribution using a parametric model, and then to determine the parameters using a training set consisting of pairs `<x[n], c[n]>` of input vectors along with their corresponding target output vectors. In other words, in the discriminative approach, the conditional distribution discriminates directly between the different values of `c`; that is, posterior `p(c|x)` is directly used to make predictions of `c` for new values of `x` ([Figure 7.2](#ch7.xhtml#fig7_2)). Here for example the classes can be `C[1]` = benign mole or `C[2]` = cancer, which can be modelled given the respective data points.

![Figure 7.2 Discriminative model.](images/fig7_2_B.jpg)

[Figure 7.2 Discriminative model.](#ch7.xhtml#R_fig7_2)

### 7.2.2.2 Generative Model

Generative models are used for modelling data directly; that is, modelling observations drawn from a probability density function. This approach to probabilistic classification finds the joint distribution `p(x, c)`, expressed for instance as a parametric model, and then subsequently uses this joint distribution to evaluate the conditional `p(c|x)` in order to make predictions of `c` for new values of `x` by application of the `Bayes theorem`. This is known as a generative approach since by sampling from the joint distribution it is possible to generate synthetic examples of the feature vector `x` ([Figure 7.3](#ch7.xhtml#fig7_3)). Here for the vector of random variables we learn the probability for each class `c` given the input. In practice, the generalization performance of generative models is often found to be poorer than that of discriminative models due to differences between the model and the true distribution of the data.

![Figure 7.3 Generative model.](images/fig7_3_B.jpg)

[Figure 7.3 Generative model.](#ch7.xhtml#R_fig7_3)

## 7.3 Naïve Bayes Classifier

`Naïve Bayes` is a very popular classification model and is a type of `generative model` ([Mitchell, 2017](#ch7.xhtml#ref7_17)). Here we try to determine the conditional probability `P(C|X)`, that is, the probability of a class `C` given a set of features `X` (Equation 7.3). This probability can be determined by finding the likelihood of the input features given the class and the prior probability of the class. Here the difficulty lies in learning the joint probability of the features given the class.

(7.3)

$$
P(C \mid X) \propto P(X \mid C)P(C) = P(X_1,\dots,X_n\mid C)P(C)
$$

`Naïve Bayes` is one of the most practical Bayes learning methods. The `naïve Bayes classifier` applies to learning tasks where each instance `x` is described by a conjunction of attribute values and where the target function `f(x)` can take on any value from some finite set. Some successful applications of the `naïve Bayes` method are medical diagnosis and classifying text documents.

### 7.3.1 Naïve Bayes Classifier: Assumptions

As already discussed, for the `naïve Bayes classifier` we need to determine two probabilities, that is, prior probability of the class and the likelihood of the data with respect to the class.

However, the likelihood or the joint probability of the features of the input data given the class `P(x[1], x[2], ..., x[n]|c[j])` is of the order of `O(|X|^n * |C|)` and can only be estimated if a very, very large number of training examples is available. This is where the naïveté of the naïve Bayes method comes into the picture, that is, the `conditional independence assumption` where we assume that the probability of observing the conjunction of attributes is equal to the product of the individual probabilities. In other words, we assume that the joint probability can be found by finding the individual probability of each feature given the class ([Figure 7.4](#ch7.xhtml#fig7_4)).

![Figure 7.4 Naïve Bayes assumption.](images/fig7_4_B.jpg)

[Figure 7.4 Naïve Bayes assumption.](#ch7.xhtml#R_fig7_4)

Let us first formulate Bayesian learning. Let each instance `x` of a training set `D` be a conjunction of `n` attribute values `<a[1], a[2],.., a[n]>` and let `f(x)`, the target function, be such that `f(x) ∈ V`, a finite set. According to the Bayesian approach using `MAP`, we can specify this as follows (Equation 7.4):

(7.4)
