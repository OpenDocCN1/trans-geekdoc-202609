Chapter 3 : part 5

# # Naive Bayes

Bayes Theorem, Naive Bayes Algorithm

# ## 3.5.1 Bayes Theorem

**Bayes' Theorem:** Bayes' theorem is also known as Bayes' Rule or Bayes' law, which is used to determine the *probability of a hypothesis with prior knowledge*. It depends on the *conditional probability*. The formula for Bayes' theorem is as:

```
P(A|B) = \frac{P(B|A)P(A)}{P(B)}
```

Probability that *A* occurs given *B* **P(A|B)**. The Bayes Theorem is a method of finding what the *probability of something occurring (A)* given that something *else has just occurred (B)*).

+   * **P(A|B) is Posterior:** Probability of hypothesis A on the observed event B. How often A happens that B happens
* **P(B|A) is Likelihood probability:** Probability of the evidence given that the probability of A hypothesis is true. How often B happens that A happens
* **P(A) is Prior Probability:** Probability of hypothesis before observing the evidence. A is on its.
* **P(B) is Marginal:** Probability of Evidence. B is on its own.

where *A* and *B* are events and $P(B) \neq 0$ and *B* must be *different events*.
* **P(A|B) is a conditional probability:** The probability of event A occurring given that B is true. It is also called the *posterior probability* of given B.
* **P(B|A)** also a conditional probability: The probability of event B occurring that A is true. It can also be interpreted as the likelihood of A given fixed B $P(B|A) = L(A|B)$.
* **P(A)** and **P(B)** are the probabilities of observing A and respectively which are known as the *marginal or prior probability*.

*Example:* Let us say $P(Fire|Smoke)$ means how often there is fire, and $P(Smoke)$ means how often we see smoke;

$P(Fire|Smoke)$ means how often there is *fire* when we can see *smoke*
$P(Fire|Smoke)$ means how often we can see *smoke* when there is *fire*

So the formula tells us "forwards" in **P(Fire|Smoke)** when we know "backwards" **P(Smoke|Fire)**

+   * dangerous fires are rare (1%),
* but smoke is fairly common (10%) due to barbecues, **P(Smoke)**n* and 90% of dangerous fires make smoke, **P(Smoke|Fire)**

We can then discover the probability of dangerous Fire when there is Smoke:

```
$P(Fire|Smoke) = \frac{P(Smoke)P(Fire)}{P(Smoke)} = \frac{10\% \times 90\%}{100\%} = 9\%$
```

So it is still worth checking out smoke to be sure.