# Hints for the exercises

0.1 Recall that $\|x - y\|_2^2 = \|x\|_2^2 - 2\langle x, y\rangle + \|y\|_2^2$. (This follows by expanding $\|x - y\|_2^2 = \langle x - y, x - y\rangle$.) Use this formula for $\|Z - \mathbb{E}Z\|_2^2$.

0.2 Check the identity $\mathbb{E}\|Z - a\|_2^2 - \mathbb{E}\|Z - \mu\|_2^2 = \|a - \mu\|_2^2$ where $\mu = \mathbb{E}Z$.

0.4 (a) Select the signs independently at random. Calculate the expected squared norm of the random vector $\pm x_1 \pm x_2 \pm \cdots \pm x_n$ using Example 0.3.

0.5 Choose $T = \{e_1, \dots, e_n\}$ where $e_i$ are the standard basis vectors. Then $\operatorname{conv}(T)$ is an $(n-1)$-dimensional simplex; draw a picture for $n = 3$. Let $x$ be the center of the simplex. All that remains is to calculate the distance from $x$ to each $(k-1)$-dimensional face of the simplex.

0.6 To prove the upper bound, multiply the sum of binomial coefficients by the quantity $(k/n)^k$, replace this quantity by $(k/n)^j$ in the left side, and use the binomial theorem. To prove the lower bound, use the definition of the binomial coefficient to express it as a product of $k$ fractions; check that each fraction is lower bounded by $n/k$.

0.7 Recall the scaling property of the volume in $\mathbb{R}^n$ used in the beginning of the proof of Theorem 0.0.4: the ball of radius $r$ has volume $r^n$ times the volume of the unit ball.

0.8 Compute the CDF of $\|X\|_2$, deduce the probability density function by differentiation, and then compute the expectation.

0.9 First, improve the bound on the number of balls in Corollary 0.0.3 using the following fact from elementary combinatorics: the number of ways to choose an unordered subset of $k$ elements from an $N$-element set, with possible repetitions, is $\binom{N+k-1}{k}$. Substitute $k = k_0 = n / \log(eN/n)$ and use Exercise 0.6 to bound the binomial coefficient by $C^m$. Then follow the proof of Theorem 0.0.4.

1.3 (a) Use induction on $m$. At the induction step, represent $\sum_{i=1}^m \lambda_i x_i$ as a convex combination of two vectors, one of which is $x_m$ and the other is some convex combination of $x_1, \dots, x_{m-1}$.

1.4 To prove the upper bound, express a point $x \in \operatorname{conv}(T)$ as a convex combination of some points in $T$ and use Jensen inequality from Exercise 1.3.

1.7 Condition on the value of $n$, but otherwise follow the proof of the result in Example 1.4.2.

1.8 What is the probability that a given subset of $k$ students is independent? How many subsets consisting of $k$ students are there? Answer these questions and use the union bound.

1.9 Following the proof of the result in Example 1.4.2, the problem reduces to checking that $n(1 - p_n)^{n-1} \to 0$.

1.10 (b) Expanding yields $\mathbb{E}S_n^2 = \sum_{i=1}^n \mathbb{E}X_i^2 + \sum_{i \neq j} \mathbb{E}X_i X_j$. Interpret each term $\mathbb{E}X_i X_j$ as the probability that both students $i$ and $j$ are friendless. Compute this probability.

1.11 Use Jensen inequality.

1.12 Write $\mathbb{E}|X|^p$ as $\mathbb{E}[|X||X|^{p-1}]$ and bound the second factor by its supremum.