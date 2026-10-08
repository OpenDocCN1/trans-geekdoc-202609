However, this notation is cumbersome, and we write instead $p(x), p(y)$ and $p(x, y)$. In the above example $X$ is the coin and $Y$ is the die with $p(heads)=1/2, p(3)=1/6$ and $p(heads,3)=1/12$ for example.

The coin and die cannot influence each other, but other random variables can, for example the height and weight of a person. We expect a very tall person to not be heavy. Of course, there are also examples proving this expectation wrong. When two random variables do not influence each other, they are called *independent* or *dependent*. Two random variables $X$ and $Y$ are independent, if and only if

$p(X, Y)=p(X)p(Y) \quad (2.1)$

When learning from experiments, instead of recording probabilities in the grid we record how often a particular outcome occurs. Let the outcome is $X=x_i$ and $Y=y_j$. We denote $m_i$ the number of occurrences of $X=x_i$ disregarding $Y$, and $l_j$ the number of occurrences where $Y=y_j$ whatever $X$ is. The grid then looks like

| | $y_1$ | ... | $y_j$ | ... | $y_L$ |
|---|---|---|---|---||}{
| $x_1$ | $n_{11}$ | | $n_{1L}$ | | $m_1$ |
| | | | | | | |
| $X$ | $x_i$ | ... | $n_{ij}$ | ... | $m_i$ |
| | | | | | | |
| $x_M$ | $n_{M1}$ | | $n_{ML}$ | | $m_M$ |
| | $l_1$ | ... | $l_j$ | ... | $l_L$ |

We see that

$m_i=\sum_{j=1}^L n_{ij}$ and $l_j=\sum_{i=1}^M n_{ij}, \quad (2.2)$

since marginalizing over one random variable summing over all possible outcomes of the other.

We can now estimate the probabilities as fractions of the total number of experiments N:

$p(x_i)=\frac{m_i}{N}, p(y_j)=\frac{l_j}{N}$ and $p(x_i, y_j)=\frac{n_{ij}}{N}$.

Combining with this (2.2), we see that

$p(x_i)=\sum_{j=1}^L p(x_i, y_j). \quad (2.3)$