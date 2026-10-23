# 10.4.3.4  Dealing with novel words

At test time, the model may encounter a completely novel word that it has not seen before. This is known as the **out of vocabulary** or **OOV** problem. Such novel words are bound to occur, because the set of words is an **open class**. For example, the set of proper nouns (names of people and places) is unbounded.

A standard heuristic to solve this problem is to replace all novel words with the special symbol **UNK**, which stands for “unknown”. However, this loses information. For example, if we encounter the word “athazagoraphobia”, we may guess it means “fear of something”, since phobia is a common suffix in English (derived from Greek) to mean “fear of”. (It turns out that athazagoraphobia means “fear of being forgotten about or ignored”.)

We could work at the character level, but this would require the model to learn how to group common letter combinations together into words. It is better to leverage the fact that words have substructure, and then to take as input **subword units** or **wordpieces** [SHB16; Wu+16]; these are often created using a method called **byte-pair encoding** [Gag94], which is a form of data compression that creates new symbols to represent common substrings.

# 10.5  Robust logistic regression

Sometimes we have **outliers** in our data, which are often due to labeling errors, also called **label noise**. To prevent the model from being adversely affected by such contamination, we will use **robust logistic regression**. In this section, we discuss some approaches to this problem.

# 10.5.1  Mixture model for the likelihood

One of the simplest ways to define a robust logistic regression model is to modify the likelihood so that it predicts that each output label $y$ is generated uniformly at random with probability $\pi$, and otherwise is generated using the usual conditional model. In the binary case, this becomes

$$p(y|x) = \pi\operatorname{Ber}(y|0.5) + (1-\pi)\operatorname{Ber}(y|\sigma(\mathbf{w}^{\mathsf{T}}\mathbf{x})) \tag{10.103}$$

This approach, of using a mixture model for the observation model to make it robust, can be applied to many different models (e.g., DNNs).

We can fit this model using standard methods, such as SGD or Bayesian inference methods such as HMC (Sec. 10.6.3). For example, let us create a “contaminated” version of the 1d, two-class Iris dataset that we discussed in Sec. 2.4.3. We will add add 6 examples of class 1 (versicolor) with abnormally low sepal length. In Fig. 10.11a, we show the results of fitting a standard (Bayesian) logistic regression model to this dataset. In Fig. 10.11b, we show the results of fitting the above robust model. In the latter case, we see that the decision boundary is similar to the one we inferred from non-contaminated data, as shown in Fig. 2.8b. We also see that the posterior uncertainty about the decision boundary’s location is smaller than when using a non-robust model.

# 10.5.2  Bi-tempered loss

In this section, we present an approach to robust logistic regression proposed in [Ami+19].