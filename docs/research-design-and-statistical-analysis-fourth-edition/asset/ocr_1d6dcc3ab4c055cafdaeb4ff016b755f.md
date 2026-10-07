# Basic Concepts in Probability 59

Of course, events are not always mutually exclusive. As we explained in Section 3.2.4, if events $E_1$ and $E_2$ are not mutually exclusive, the probability of their joint occurrence is (usually) greater than zero and must be taken into account, so that

```
$p(E_1 \text{ or } E_2) = p(E_1) + p(E_2) - p(E_1 \text{ and } E_2) \quad (3.12)$
```

For example, in Table 3.1, $p(A \text{ or psychology major}) = p(A) + p(psychology) - p(A \text{ and psychology}) = .27 + .60 - .15 = .72$, as we calculated by summing event probabilities using Equation 3.7. In this case,

# 3.3.8 The Multiplication Rule for Joint Events

As we did for the additive law, we saw with a special case. If $E_1$ and $E_2$ are independent events,

```
$p(E_1 \text{ and } E_2) = p(E_1) \times p(E_2) \quad (3.13)$
```

The law can be extended to any number of independent events, $E_1, E_2, \dots, E_n$,

```
$p(E_1 \text{ and } E_2 \text{ and... } E_n) = p(E_1) \times p(E_2) \times \dots \times p(E_n) \quad (3.14)$
```

If two events are independent, then the probability of their joint occurrence is equal to the product of their individual probabilities.

Note Equations 3.13 and 3.14 do not hold if the events are not independent. For example, $A$ and $psychology major$ are not independent and $p(A \text{ and psychology}) = .15$, but $p(A)p(psychology) = .27)(.60) = .162$. However, the multiplication rule can be extended to events that are not independent.

```
$p(E_1 \text{ and } E_2) = p(E_1) \times p(E_2 | E_1) = p(E_2) \times p(E_1 | E_2) \quad (3.15)$
```

Equation 3.15 follows directly from the definition of conditional probability, $p(E_i | E_j) = p(E_i \cap E_j)/p(E_j)$. Multiplying both sides of this equation by $p(E_j)$ yields $p(E_i) \times p(E_j) = p(E_j) \times p(E_i | E_j)$. For example, applying Equation 3.15 to the data of Table 3.1, we can see that $p(A \text{ and psychology major}) = p(psychology)p(A | psychology) = .60(15/60) = .15$.

Although the multiplication and addition rules are quite simple, people often mix them up, because the statement of the multiplication rule uses the word "and" and the statement of the addition rule does not. It should be emphasized that the multiplication rule tells us how to calculate $p(E_1, E_2)$, the probability of the joint occurrence of $E_1$ and $E_2$. The addition rule tells us how to calculate $p(E_1 \text{ or } E_2)$, the probability that $E_1$ or $E_2$ occurs. This union of $E_1$ and $E_2$ (i.e., $E_1$ or $E_2$) includes the joint event $E_1$ and $E_2$, but it also includes occurrences of $	ilde{E}_1$ without $E_2$ and of $	ilde{E}_2$ without $E_1$.

# 3.3.9 Bayes' Rule

There is one more probability rule that is useful to know. In Section 3.3.5, we noted that $p(E_1 | E_2)$ and $p(E_2 | E_1)$ are not the same thing and that they usually have different values.