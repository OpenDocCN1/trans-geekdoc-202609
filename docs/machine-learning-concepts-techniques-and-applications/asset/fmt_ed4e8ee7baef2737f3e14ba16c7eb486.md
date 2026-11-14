
## 10.4 Markov Models

In the simplest form, a Markov model assumes that observations are completely independent, that is, like a graph without edges between them as shown in [Figure 10.7](#ch10.xhtml#fig10_7).

![Figure 10.7 Markov model with independent observations.](images/fig10_7_B.jpg)

[Figure 10.7 Markov model with independent observations.](#ch10.xhtml#R_fig10_7)

The simplest form can be understood with the following example: To predict whether it rains tomorrow is only based on relative frequency of rainy days. The simplest form ignores the influence of whether it rained the previous day.

The general Markov model for an observation `x[n]` can be expressed by the product rule which gives the joint distribution of sequence of observations `x[1], x[2], …..x[n−1]` as given in Equation (10.2):

(10.2)

$$
\mathbf{P}\left( \mathbf{x}_{1},..\mathbf{x}_{\mathbf{N}} \right) = \prod\limits_{\mathbf{n} = 1}^{\mathbf{N}}\mathbf{p}\left( \mathbf{x}_{\mathbf{n}}\mid \mathbf{x}_{1},..\mathbf{x}_{\mathbf{n} - 1} \right)
$$

### 10.4.1 Types of Markov Models

Markov models can be broadly classified based on two characteristics of the system, namely whether all states of the system are observable or not and whether the system is autonomous or controlled by external actions that can affect the outcomes. Based on these characteristics, the four types of Markov models are given in [Table 10.1](#ch10.xhtml#table10_1).

[Table 10.1 Four Commonly Used Markov Models](#ch10.xhtml#R_table10_1)

| | System State Is Fully Observable | System State Is Partially Observable |
|---|---|---|
| System is autonomous | `Markov chain`—show all possible states, and the transition probability of moving from one state to another at a point in time. | `Hidden Markov model`—has some unobservable states. They show states and transition rates and in addition also represent observations and observation likelihoods for each state. |
| System is controlled | `Markov decision process`—shows all possible states but is controlled by an agent who makes decisions based on reliable information. | `Partially observable Markov decision process`—similar to Markov decision process; however, the agent does not always have reliable information. |

### 10.4.2 Markov Chain Model

The Markov chain model is the simplest model of the Markov family. When modelling the state of a system, the Markov model employs a random variable that changes with time. It implies that distribution of a variable is completely dependent on its preceding state distribution.

The `first-order Markov model` is a chain of observations `x[n]` with a joint distribution for a sequence of `n` variables as given in [Figure 10.8](#ch10.xhtml#fig10_8). It is called the `first-order` Markov model because the next state in a sequence depends only on one state—the current state (Equation 10.3).

![Figure 10.8 Markov model with chain of observations.](images/fig10_8_B.jpg)

[Figure 10.8 Markov model with chain of observations.](#ch10.xhtml#R_fig10_8)

(10.3)

$$
\mathbf{p}\left( \mathbf{x}_{1},..\mathbf{x}_{\mathbf{N}} \right) = \mathbf{p}\left( \mathbf{x}_{1} \right)\prod\limits_{\mathbf{n} = 2}^{\mathbf{N}}\mathbf{p}\left( \mathbf{x}_{\mathbf{n}}\mid \mathbf{x}_{\mathbf{n} - 1} \right)
$$

This can be written as in Equation (10.4):

(10.4)

**p**(**x**[**n**]∣**x**[1]…**x**[**n** − 1]) = **p**(**x**[**n**]∣**x**[**n** − 1])

If the model is used to predict the next observation, the distribution of predictions will only depend on preceding observation and be independent of earlier observations. Stationarity implies conditional distributions `p(x[n]|x[n-1])` are all equal.

Example: A Markov chain with three states representing the dinner of the day (sandwich, pizza, burger) is given. A transition table with transition probabilities representing the dinner of the next day given the dinner of the current day is also given ([Figure 10.9](#ch10.xhtml#fig10_9)).

![Figure 10.9 Markov chain with three states.](images/fig10_9_B.jpg)

[Figure 10.9 Markov chain with three states.](#ch10.xhtml#R_fig10_9)

From the previous example, let us find out the probability of dinner for the next seven days if it will be “B-B-S-S-B-P-B.”

If the given model is `O` = {`S3`, `S3`, `S3`, `S1`, `S1`, `S3`, `S2`, `S3`}

Then, the probability of the given model `O` is as follows:

$$
\begin{array}{ll} {P\left( O \mid \text{Model} \right)} & {= P\left( S3,S3,S3,S1,S1,S3,S2,S3\mid \textit{Model} \right)} \\ & {= P\left( S3 \right) \cdot P\left( S3\mid S3 \right) \cdot P\left( S3\mid S3 \right) \cdot P\left( S1\mid S3 \right) \cdot P\left( S1\mid S1 \right) \cdot P\left( S3\mid S1 \right) \cdot P\left( S2\mid S3 \right) \cdot P\left( S3\mid S2 \right)} \\ & {= \pi_{3} \cdot a_{33} \cdot a_{33} \cdot a_{31} \cdot a_{11} \cdot a_{13} \cdot a_{32} \cdot a_{23}} \\ & {= 1 \cdot \left( 0.8 \right) \cdot \left( 0.8 \right) \cdot \left( 0.1 \right) \cdot \left( 0.4 \right) \cdot \left( 0.3 \right) \cdot \left( 0.1 \right) \cdot \left( 0.2 \right)} \\ & {= 1.536 \times 10^{- 4}} \\ \end{array}
$$

Let us consider another example, where we shall apply a Markov model for spoken word production. If the states /k/ /a/ /c/ /h/ represents phonemes, the Markov model for the production of the word “catch” is as shown in [Figure 10.10](#ch10.xhtml#fig10_10).

![Figure 10.10 Markov model for spoken word production.](images/fig10_10_B.jpg)

[Figure 10.10 Markov model for spoken word production.](#ch10.xhtml#R_fig10_10)

The transitions are from /k/ to /a/, /a/ to /c/, /c/ to /h/, and /h/ to a silent state. Although only correct “cat” sound is represented by the model, perhaps other transitions can be introduced, for example /k/ followed by /h/.

In the `second-order Markov model`, each observation is influenced by the previous two observations (Equation 10.5). The conditional distribution of observation `x[n]` depends on the values of two previous observations, `x[n−1]` and `x[n−2]`, as shown in [Figure 10.11](#ch10.xhtml#fig10_11).

![Figure 10.11 Second-order Markov model.](images/fig10_11_B.jpg)

[Figure 10.11 Second-order Markov model.](#ch10.xhtml#R_fig10_11)

(10.5)

$$
\mathbf{p}\left( \mathbf{x}_{1},\ldots\mathbf{x}_{\mathbf{n}} \right) = \mathbf{p}\left( \mathbf{x}_{1} \right)\mathbf{p}\left( \mathbf{x}_{2} \mid \mathbf{x}_{1} \right)\prod\limits_{\mathbf{n} = 3}^{\mathbf{N}}\mathbf{p}\left( \mathbf{x}_{\mathbf{n}} \mid \mathbf{x}_{\mathbf{n} - 1},\mathbf{x}_{\mathbf{n} - 2} \right)
$$

Similarly for the `Mth-order` Markov source, the conditional distribution for a particular variable depends on the previous `M` variables. The discrete variable with `K` states in its first order is `p(x[n]|x[n−1])`, which needs `K − 1` parameters for each value of `x[n−1]` for each of `K` states of `x[n]`, giving `K(K−1)` parameters. The `M`th order will need `K^(M−1)(K−1)` parameters.
