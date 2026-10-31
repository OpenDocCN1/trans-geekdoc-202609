
### 8.5 Theorem. Let $n,m \to \infty$ such that $m/n \to p$. Then
$$\lim\left(\frac{1}{n}\log\binom{n}{m}\right)=h(p).$$
For a generalization to multinomials see Exercise 8.9.

## Basic properties of Shannon entropy

A basic tool in proving the basic properties of Shannon's entropy function is Jensen's inequality.

### 8.6 Definition. A real function $f(x)$ defined on an open interval $I$ is concave down if, for every $x_0 \in I$, there is a line $L$ through $(x_0,f(x_0))$ which is never under the graph of $f(x)$.

A function $f$ is concave down if, when biking along its graph from left to right, we lean to the right. This is certainly satisfied if $f''(x)<0$.

Let $g(x)=f(x_0)+\lambda(x-x_0)$ be the equation of the line in Definition 8.6. By the definition of concavity, $f(x)\le f(x_0)+\lambda(x-x_0)$ for all $x\in I$. Let $x_1\le x_2\cdots\le x_n$ be points in $I$ and $p_1,\dots,p_n$ probabilities of a probability space. Using the inequalities above yields
$$\sum_i p_i f(x_i)\le f(x_0)+\lambda\Big(\sum_i p_i x_i -x_0\Big).$$
Choose in particular $x_0=\sum_i p_i x_i$; observe that $x_0\in I$.

### 8.7 Theorem (Jensen's inequality). Let $f(x)$ be concave down on the open real interval $I$, let $x_1\le x_2\cdots\le x_n$ be points in $I$ and $p_1,\dots,p_n$ probabilities of a probability space. Then
$$\sum_i p_i f(x_i)\le f\Big(\sum_i p_i x_i\Big).$$

Equality holds if and only if $f(x)$ is a linear function (its graph is a straight line) on the interval $[x_1,x_n]$.

The proof for the case of equality is left as Exercise 8.5.

Clearly the log-function is concave down on the interval $(0,\infty)$. Choose positive numbers $x_i$ and a probability distribution $p_i$. An application of Jensen's inequality yields the famous inequality between the arithmetic and the geometric mean:

### 8.8 Theorem.
Let $x_i > 0$, $p_i \ge 0$, $i = 1,2,\dots,n$, where $\sum_i p_i = 1$. Then

$$\sum_{i=1}^n p_i \cdot x_i \ge \prod_{i=1}^n x_i^{p_i}.$$

*Equality holds if and only if all the $x_i$ with $p_i \neq 0$ are equal.*

Another application of Jensen’s inequality to the log-function will be used to establish a key property of the entropy:

### 8.9 Proposition.
Let $p_i$ and $q_i$ be positive numbers, $i = 1,2,\dots,n$ such that $\sum_i p_i = 1$. Put $\sum_i q_i = \alpha$. Then the following holds:

$$\sum_i p_i \cdot \log(1/p_i) \le \sum_i p_i \cdot \log(1/q_i) + \log(\alpha).$$

*Equality holds if and only if $q_i = \alpha p_i$ for all $i$.*

**PROOF**  Apply Jensen’s inequality to $x_i = q_i/p_i$. Observe $\sum_i p_i x_i = \sum_i q_i = \alpha$.

In the case $\alpha = 1$, when the $q_i$ form another probability distribution, this yields an interesting property of the entropy function: consider the expression $\sum_i p_i \cdot \log(1/q_i)$, where the $p_i$ form a fixed probability distribution and $(q_i)$ varies through the probability distributions. Proposition 8.9 says that this expression is minimized when $q_i = p_i$, hence by the entropy.

## Joint entropy and conditional entropy

Every probability space has its entropy. Another basic notion of probability theory and statistics is random variables.

### 8.10 Definition.
Let $\Omega$ be a probability space. A **random variable** on $\Omega$ is a mapping $f$ defined on $\Omega$.

As every random variable induces a probability distribution, we can also speak of the entropy of a random variable. Let $X$ and $Y$ be random variables with probability distributions $p_i = Pr(X = i)$ and $q_j = Pr(Y = j)$, respectively. Consider further the joint distribution of $X$ and $Y$, given by the probabilities $p(i,j) = Pr(X = i \text{ and } Y = j)$. Observe that the joint distribution carries more information than the distributions of $X$ and $Y$ taken together. In fact, we may arrange the probabilities $p(i,j)$ in a matrix with
rows indexed by i and columns indexed by j. The row sums are the p_i, the column sums are q_j. The other way around it is clear that the matrix is far from being determined by its row- and column sums.

### 8.11 Definition.
Let X, Y be random variables defined on the same probability space Ω. With the notation just introduced, we call X and Y statistically independent if, for every i in the range of X and j in the range of Y, we have

$p(i,j)=p_i \times q_j$.

The meaning behind this notion is that, in the case of independent random variables, information about the value of one of them gives no information whatsoever about the value of the other variable.

We wish to compare the entropies H(X) and H(Y) to the joint entropy H(X,Y). In fact, there are more entropies around.

### 8.12 Definition.
Let X, Y be random variables defined on the same probability space Ω. The conditional probability is

$p(i|j)=p(i,j)/q_j$.

*This is the probability that X = i if it is already known that Y = j.*

Observe that X and Y are independent if and only if p(i|j)=p_i always holds. For every fixed value j of Y, the conditional probabilities p(i|j) form a probability distribution. Denote the corresponding entropy by H(X|Y=j). It is natural to define a conditional entropy H(X|Y) as the weighted sum of these expressions, the weights being the probabilities q_j.

### 8.13 Definition.
The conditional entropy H(X|Y) is defined by $H(X|Y)=\sum_j q_j \cdot H(X|Y=j)= - \sum_{i,j} p(i,j) \cdot \log(p(i|j))$.

*Here i,j run through the values of X and Y, respectively.*

The conditional entropy is a new notion. It is not the entropy of a probability space. There is no probability space X|Y.

## The main theorem

The main theorem shows that our notions cooperate in exactly the way our interpretation suggests:

### 8.14 Theorem. Let X and Y be random variables defined on the same finite probability space. Then the following relations hold for the entropies:
- H(X,Y) ≤ H(X) + H(Y), with equality if and only if X and Y are independent.
- H(X,Y) = H(X) + H(Y|X) (the chain rule for entropies).
- H(X) ≥ H(X|Y), with equality if and only if X and Y are independent.

PROOF  Most interesting is the proof of the first statement. If we write out the definitions, we see that we have to prove the following statement: ∑_{i,j} p(i,j)·log(p(i,j)) ≥ ∑_{i,j} p(i,j)·log(p_i p_j). This follows from Proposition 8.9 in the case α = 1. It also follows from this proposition when equality occurs.

The second statement is a trivial formal manipulation; the third statement follows from the others: H(X) + H(Y) ≥ H(Y,X) = H(Y) + H(X|Y).

Recall that we interpret H(X) as a measure for the average amount of information per letter of a source operating with the corresponding probabilities. The first property of the main theorem says that the information contained in X and Y taken together is at most the sum of the individual informations. The second statement says that the joint information given by X and Y together can be written as the sum of the information given by X and the information given by Y when X is known. The third property says that knowledge of Y cannot increase our uncertainty about X. Exactly then will this knowledge not help when X and Y are independent.

Finally, we come to a natural notion, which is not to be found in Shannon's classical papers, mutual information:

### 8.15 Definition. The mutual information is I(X,Y) = H(X) − H(X|Y).

Observe that this notion is symmetric in X and Y : I(X,Y) = H(X,Y) − H(Y|X) − H(X|Y) = I(Y,X). Does this notion agree with our interpretation? H(X) is the uncertainty about X, and H(X|Y) is the remaining uncertainty about X once Y is known. We should therefore interpret the difference as the amount of information Y has disclosed about X.

The law of large numbers provides another interpretation of the entropy function. Let a sample space with probabilities p1,p2,…,pr be given. As
before, interpret this space as a source of information, where at every point of time one of r symbols is generated according to the probability distribution. Consider signals of length N (N-tuples of letters) generated by this source. Let h_i be the frequency of letter i ∈ {1,2,…,r}. The law of large numbers asserts the following:

For every pair ε, δ > 0 there is an N₀ = N₀(ε, δ) such that for every N ≥ N₀ the set of signals of length N can be partitioned in two parts:
- a set of total probability < ε, and
- a set all of whose elements satisfy

|h_i/N − p_i| < δ for all i.

The law of large numbers follows from the Tschebyscheff inequality, Theorem 9.10 in the next chapter. A proof of the law of large numbers will be sketched in the exercises section of Chapter 9.

The interpretation is as follows: if we pick a long signal at random, then we are almost sure that the relative frequencies of the letters are close to the probabilities. If S is such a signal of length N, then its probability is p = Pr(S) = ∏_i p_i^{h_i}. It follows that log(p) = ∑_i h_i·log(p_i), hence log(p)/N = ∑_i (h_i/N)·log(p_i). If S is one of the probable signals, then this expression is close to ∑_i p_i·log(p_i) = −H(p1,…,p_n). This is another interpretation of the entropy function.

This property is known in information theory as the **asymptotic equipartition property,** AEP; see Cover and Thomas [62].
