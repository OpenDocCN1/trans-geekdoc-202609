# Developing the Fundamentals of Hypothesis Testing

The probability of three A responses and one A response in any order is the sum of the probabilities of these four combinations, or $4\pi^3(1-\pi)$. In general, to find the probability of having y A responses, we calculate the probability of a combination having exactly y responses and then multiply by the number of ways that outcome can occur.

The approach can be generalized to any value of $n$. If we assume the trials are independent, the probability of any specific combination of $y$ A responses and $(n-y)$ A responses is $\pi^y(1-\pi)^{n-y}$. The probability of exactly $y$ A responses and $(n-y)$ A responses

```
$p(y;n) = k\pi^y(1-\pi)^{n-y} \quad (4.1)$
```

where $k$ is the number of combinations consisting of exactly $y$ A and $(n-y)$ A responses.\nWe have just about a binomial function; we need a formula for $k$, the number of ways in which $y$ A and $(n-y)$ A responses can be combined. This number of combinations can be shown to be (see Appendix 4.1):

```
$k = \frac{n!}{y!(n-y)!} \quad (4.2)$
```

where $n! = (n)(n-1)(n-2)..(3)(2)(1)$ and $0! = 1$. Note that that

```
$\binom{n}{y}$
```

have the same value. Substituting $y=0, 1, 2, 3,$ and $4$ in into Equation 4.2, verify that $k$ takes the values $1, 4, 6, 4,$ and $1$, respectively; these are the numbers of combinations that appear in Table 4.1. Replacing $k$ in Equation 4.1 with the expression on the right side of Equation 4.2 yields this binomial probability:

```
$p(y;n) = \binom{n}{y}\pi^y(1-\pi)^{n-y} = \frac{n!}{y!(n-y)!}\pi^y(1-\pi)^{n-y} \quad (4.3)$
```

Equation 4.3 describes a family of distributions, with a different probability distribution for each distinct combination of $\pi$ and $n$. Table C.1 in Appendix C presents binomial distributions for selected values of $\pi$ and $n$. We restrict our examples to those that are described by the distributions in Table C.1 to save ourselves the trouble of computing binomial distributions from scratch. In Section 4.3.3, we will show how software can be used for these calculations.

Now we can calculate the probabilities of various outcomes in the ESP experiment Rachel was generating. If $n=20$ and $\pi=.25$, we can find the probability of say, seven or more correct responses. In Table C.1, we first find the row of rows that corresponds to $n=20$, and then we use the column corresponding to $p=.25$. Reading from the table, we see that $p(y=0)=.0032, p(y=2)=.0669$, and so on. These are the same values that would be obtained using Equation 4.3. We can find the probability of seven or more responses in several ways. One way is to find the probabilities for $7, 8, 9..20$ correct and add these 14 numbers together, then add these seven numbers together, and then subtract the sum from 1. The probability of getting 0–6 correct responses is .0032 + .0211