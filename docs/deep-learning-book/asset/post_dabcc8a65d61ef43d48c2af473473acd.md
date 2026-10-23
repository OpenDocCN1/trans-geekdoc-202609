
assumptions imply that the same axioms must control both kinds of probability, see Ramsey (1926).

Probability can be seen as the extension of logic to deal with uncertainty. Logic provides a set of formal rules for determining what propositions are implied to be true or false given the assumption that some other set of propositions is true or false. Probability theory provides a set of formal rules for determining the likelihood of a proposition being true given the likelihood of other propositions.

## 3.2 Random Variables

A **random variable** is a variable that can take on different values randomly. We typically denote the random variable itself with a lowercase letter in plain typeface, and the values it can take on with lowercase script letters. For example, $x_1$ and $x_2$ are both possible values that the random variable $x$ can take on. For vector-valued variables, we would write the random variable as $\mathbf{x}$ and one of its values as $\boldsymbol{x}$. On its own, a random variable is just a description of the states that are possible; it must be coupled with a probability distribution that specifies how likely each of these states are.

Random variables may be discrete or continuous. A discrete random variable is one that has a finite or countably infinite number of states. Note that these states are not necessarily the integers; they can also just be named states that are not considered to have any numerical value. A continuous random variable is associated with a real value.

## 3.3 Probability Distributions

A **probability distribution** is a description of how likely a random variable or set of random variables is to take on each of its possible states. The way we describe probability distributions depends on whether the variables are discrete or continuous.

### 3.3.1 Discrete Variables and Probability Mass Functions

A probability distribution over discrete variables may be described using a **probability mass function** (PMF). We typically denote probability mass functions with a capital $P$. Often we associate each random variable with a different probability mass function and the reader must infer which PMF to use based on the identity of the random variable, rather than on the name of the function; $P(\mathbf{x})$ is usually not the same as $P(x)$.

The probability mass function maps from a state of a random variable to the probability of that random variable taking on that state. The probability that $\mathbf{x}=x$ is denoted as $P(x)$, with a probability of 1 indicating that $\mathbf{x}=x$ is certain and a probability of 0 indicating that $\mathbf{x}=x$ is impossible. Sometimes to disambiguate which PMF to use, we write the name of the random variable explicitly: $P(\mathbf{x}=x)$. Sometimes we define a variable first, then use $\sim$ notation to specify which distribution it follows later: $\mathbf{x} \sim P(\mathbf{x})$.

Probability mass functions can act on many variables at the same time. Such a probability distribution over many variables is known as a **joint probability distribution**. $P(\mathbf{x}=x, \mathbf{y}=y)$ denotes the probability that $\mathbf{x}=x$ and $\mathbf{y}=y$ simultaneously. We may also write $P(x, y)$ for brevity.

To be a PMF on a random variable $\mathbf{x}$, a function $P$ must satisfy the following properties:

- The domain of $P$ must be the set of all possible states of $\mathbf{x}$.
- $\forall x \in \mathbf{x}, 0 \leq P(x) \leq 1$. An impossible event has probability 0, and no state can be less probable than that. Likewise, an event that is guaranteed to happen has probability 1, and no state can have a greater chance of occurring.
- $\sum_{x \in \mathbf{x}} P(x) = 1$. We refer to this property as being **normalized**. Without this property, we could obtain probabilities greater than one by computing the probability of one of many events occurring.

For example, consider a single discrete random variable $\mathbf{x}$ with $k$ different states. We can place a **uniform distribution** on $\mathbf{x}$—that is, make each of its states equally likely—by setting its PMF to

$$
P(\mathbf{x}=x_i) = \frac{1}{k} \tag{3.1}
$$

for all $i$. We can see that this fits the requirements for a probability mass function. The value $\frac{1}{k}$ is positive because $k$ is a positive integer. We also see that

$$
\sum_i P(\mathbf{x}=x_i) = \sum_i \frac{1}{k} = \frac{k}{k} = 1, \tag{3.2}
$$

so the distribution is properly normalized.

### 3.3.2 Continuous Variables and Probability Density Functions

When working with continuous random variables, we describe probability distributions using a **probability density function** (PDF) rather than a probability mass function. To be a probability density function, a function $p$ must satisfy the following properties:

- The domain of $p$ must be the set of all possible states of $\mathbf{x}$.
- $\forall x \in \mathbf{x}, p(x) \geq 0$. Note that we do not require $p(x) \leq 1$.
- $\int p(x)dx = 1$.

A probability density function $p(x)$ does not give the probability of a specific state directly; instead the probability of landing inside an infinitesimal region with volume $\delta x$ is given by $p(x)\delta x$.

We can integrate the density function to find the actual probability mass of a set of points. Specifically, the probability that $\mathbf{x}$ lies in some set $\mathbb{S}$ is given by the integral of $p(x)$ over that set. In the univariate example, the probability that $\mathbf{x}$ lies in the interval $[a, b]$ is given by $\int_{[a,b]} p(x)dx$.

For an example of a PDF corresponding to a specific probability density over a continuous random variable, consider a uniform distribution on an interval of the real numbers. We can do this with a function $u(x; a, b)$, where $a$ and $b$ are the endpoints of the interval, with $b > a$. The “;” notation means “parametrized by”; we consider $x$ to be the argument of the function, while $a$ and $b$ are parameters that define the function. To ensure that there is no probability mass outside the interval, we say $u(x; a, b) = 0$ for all $x \notin [a, b]$. Within $[a, b]$, $u(x; a, b) = \frac{1}{b-a}$. We can see that this is non-negative everywhere. Additionally, it integrates to 1. We often denote that $\mathbf{x}$ follows the uniform distribution on $[a, b]$ by writing $\mathbf{x} \sim U(a, b)$.

## 3.4 Marginal Probability

Sometimes we know the probability distribution over a set of variables and we want to know the probability distribution over just a subset of them. The probability distribution over the subset is known as the **marginal probability distribution**.

For example, suppose we have discrete random variables $\mathbf{x}$ and $\mathbf{y}$, and we know $P(\mathbf{x}, \mathbf{y})$. We can find $P(\mathbf{x})$ with the **sum rule**:

$$
\forall x \in \mathbf{x}, P(\mathbf{x}=x) = \sum_y P(\mathbf{x}=x, \mathbf{y}=y). \tag{3.3}
$$

The name “marginal probability” comes from the process of computing marginal probabilities on paper. When the values of $P(\mathbf{x}, \mathbf{y})$ are written in a grid with different values of $\mathbf{x}$ in rows and different values of $\mathbf{y}$ in columns, it is natural to sum across a row of the grid, then write $P(\mathbf{x})$ in the margin of the paper just to the right of the row.

For continuous variables, we need to use integration instead of summation:

$$
p(x) = \int p(x,y) dy. \tag{3.4}
$$

## 3.5 Conditional Probability

In many cases, we are interested in the probability of some event, given that some other event has happened. This is called a **conditional probability**. We denote the conditional probability that $\mathbf{y}=y$ given $\mathbf{x}=x$ as $P(\mathbf{y}=y \mid \mathbf{x}=x)$. This conditional probability can be computed with the formula

$$
P(\mathbf{y}=y \mid \mathbf{x}=x) = \frac{P(\mathbf{y}=y, \mathbf{x}=x)}{P(\mathbf{x}=x)}. \tag{3.5}
$$

The conditional probability is only defined when $P(\mathbf{x}=x) > 0$. We cannot compute the conditional probability conditioned on an event that never happens.

It is important not to confuse conditional probability with computing what would happen if some action were undertaken. The conditional probability that a person is from Germany given that they speak German is quite high, but if a randomly selected person is taught to speak German, their country of origin does not change. Computing the consequences of an action is called making an **intervention query**. Intervention queries are the domain of **causal modeling**, which we do not explore in this book.

## 3.6 The Chain Rule of Conditional Probabilities

Any joint probability distribution over many random variables may be decomposed into conditional distributions over only one variable:

$$
P(\mathbf{x}^{(1)}, \ldots, \mathbf{x}^{(n)}) = P(\mathbf{x}^{(1)}) \prod_{i=2}^{n} P(\mathbf{x}^{(i)} \mid \mathbf{x}^{(1)}, \ldots, \mathbf{x}^{(i-1)}). \tag{3.6}
$$

This observation is known as the **chain rule**, or **product rule**, of probability. It follows immediately from the definition of conditional probability in equation 3.5.
