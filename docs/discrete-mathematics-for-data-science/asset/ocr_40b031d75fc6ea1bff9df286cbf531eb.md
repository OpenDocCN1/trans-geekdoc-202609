We need to show that $P(n)$ is also true when $n = k + 1$. Note that the $kth$ odd number is $2k - 1$, so the next odd number is:

$(2k - 1 + 2)$ or $2k + 1$

Consider $P(k + 1)$. This is the above statement of $P(k)$ with the next odd number added to both sides:

[ 1 + 3 + 5 + \cdots + (2k - 1) ] + (2k + 1) = k^2 + (2k + 1)
= (k + 1)(k + 1)
= (k + 1)^2

Note that we used our assumption in the first line. Our work shows that the sum of the first $k + 1$ integers is the square of $k + 1$. Therefore, $P(k + 1)$ is true whenever $P(k)$ is true, and by the induction hypothesis, $P$ is true for all $n$.

As another example, consider an induction proof for the statement:

*for all* $n \in \mathbb{W}$*,* $3^n - 1$ *is even*

Our proof of this statement will use the facts that any even number contains a factor of 2 and that $3 \cdot 3^n = 3^{n+1}$.

Proof by mathematical induction:

Let: $n \in \mathbb{W}$

Base case:

Suppose $n = 0$. Then $3^n - 1 = 3^0 - 1 = 1 - 1 = 0 = 2 \cdot 0$, which is even by definition.

Therefore, there exists at least one $n \in \mathbb{W}$ such that $3^n - 1$ is even.

Inductive case: