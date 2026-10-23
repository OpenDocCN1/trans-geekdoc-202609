In Eq. (2.1), the term $p(H)$ represents what we know about possible values of $H$ before we see any data; this is called the **prior distribution**. (If $H$ has $K$ possible values, then $p(H)$ is a vector of $K$ probabilities, that sum to 1.) The term $p(Y \mid H = h)$ represents the distribution over the possible outcomes $Y$ we expect to see if $H = h$; this is called the **observation distribution**. When we evaluate this at a point corresponding to the actual observations, $y$, we get the function $p(Y = y \mid H = h)$, which is called the **likelihood**. (Note that this is a function of $h$, since $y$ is fixed, but it is not a probability distribution, since it does not sum to one.) Multiplying the prior distribution $p(H = h)$ by the likelihood function $p(Y = y \mid H = h)$ for each $h$ gives the unnormalized joint distribution $p(H = h, Y = y)$. We can convert this into a normalized distribution by dividing by $p(Y = y)$, which is known as the **marginal likelihood**, since it is computed by marginalizing over the unknown $H$:

$$p(Y = y) = \sum_{h' \in \mathcal{H}} p(H = h')p(Y = y \mid H = h') = \sum_{h' \in \mathcal{H}} p(H = h', Y = y)$$  
(2.3)

Normalizing the joint distribution by computing $p(H = h, Y = y)/p(Y = y)$ for each $h$ gives the **posterior distribution** $p(H = h \mid Y = y)$; this represents our new **belief state** about the possible values of $H$.

We can summarize Bayes rule in words as follows:

$$\text{posterior} \propto \text{prior} \times \text{likelihood}$$  
(2.4)

Here we use the symbol $\propto$ to denote “proportional to”, since we are ignoring the denominator, which is just a constant, independent of $H$. Using Bayes rule to update a distribution over unknown values of some quantity of interest, given relevant observed data, is called **Bayesian inference**, or **posterior inference**. It can also just be called **probabilistic inference**.

Below we give some simple examples of Bayesian inference in action. We will see many more interesting examples later in this book.

# ### 2.2.1  Example: testing for COVID-19

Suppose you think you may have contracted **COVID-19**, which is an infectious disease caused by the **SARS-CoV-2** virus. You decide to take a diagnostic test, and you want to use it’s result to determine if you are infected or not.

Let $H = 1$ be the event that you are infected, and $H = 0$ be the event you are not infected. Let $Y = 1$ if the test is positive, and $Y = 0$ if the test is negative. We want to compute $p(H = h \mid Y = y)$, for $h \in \{0,1\}$, where $y$ is the observed test outcome. (We will write the distribution of values, $[p(H = 0 \mid Y = y), p(H = 1 \mid Y = y)]$ as $p(H \mid y)$, for brevity.) We can think of this as a form of **binary classification**, where $H$ is the unknown class label, and $y$ is the feature vector.

First we must specify the likelihood. This quantity obviously depends on how reliable the test is. There are two key parameters. The **sensitivity** (aka **true positive rate**) is defined as $p(Y = 1 \mid H = 1)$, i.e., the probability of a positive test given that the truth is positive. The **false negative rate** is defined as one minus the sensitivity. The **specificity** (aka **true negative rate**) is defined as $p(Y = 0 \mid H = 0)$, i.e., the probability of a negative test given that the truth is negative. The **false positive rate** is defined as one minus the specificity. We summarize all these quantities in Table 2.1. (See Sec. 8.1.3.1 for more details.) Following [https://myti.ms/3lTtZgV](https://myti.ms/3lTtZgV), we set the sensitivity to 87.5% and the specificity to 97.5%.