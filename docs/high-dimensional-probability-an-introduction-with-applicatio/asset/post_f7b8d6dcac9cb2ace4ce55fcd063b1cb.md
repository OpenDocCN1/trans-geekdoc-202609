
**Example 8.3.5** (Half-spaces). A half-space in \(\mathbb{R}^n\) is a set of the form
\[
\{x : \langle a, x\rangle \le b\}
\]
where \(a\in\mathbb{R}^n\) and \(b\in\mathbb{R}\). Let \(\mathcal{F}\) be the class of indicators of all half-spaces in \(\mathbb{R}^n\). Then
\[
\operatorname{VC}(\mathcal{F}) = n+1.
\]

**Remark 8.3.6** (VC dimension vs. parameter count). VC dimension of a function class often roughly matches the number of parameters — for instance, half-spaces in \(\mathbb{R}^n\) are defined with \(n+1\) parameters, which matches their VC dimension (see Example 8.3.5). This is not a hard rule but rather a useful heuristic.

## 8.3.2 Pajor Lemma

Suppose the domain \(\Omega\) is finite and consists of \(n\) points. Then any class of Boolean functions \(\mathcal{F}\) on \(\Omega\) is also finite, and
\[
2^{\operatorname{VC}(\mathcal{F})} \le |\mathcal{F}| \le 2^n. \tag{8.27}
\]
(Why?) The upper bound is usually loose — most function classes are closer in size to the lower bound. This is not so obvious. To prepare for this result, let’s first show that there are as many shattered subsets of \(\Omega\) as the functions in \(\mathcal{F}\).

**Lemma 8.3.7** (Pajor lemma). *Let \(\mathcal{F}\) be a class of Boolean functions on a finite set \(\Omega\). Then*
\[
|\mathcal{F}| \le \left|\{\Lambda\subseteq\Omega : \Lambda \text{ is shattered by } \mathcal{F}\}\right|.
\]
*We include the empty set \(\Lambda=\emptyset\) in the count on the right side.*

Before the proof, let’s illustrate this result using Example 8.3.4. Here, \(|\mathcal{F}|=4\) and there are six subsets \(\Lambda\) that are shattered by \(\mathcal{F}\), namely \(\{1\},\{2\},\{3\},\{1,2\},\{1,3\}\) and \(\{2,3\}\). (Check!) Thus the inequality in Pajor lemma reads \(4\le6\).

*Proof of Lemma 8.3.7.* We proceed by induction on the cardinality of \(\Omega\). The case \(|\Omega|=1\) is trivial, since we include the empty set in the counting. Assume the lemma holds for any \(n\)-point set \(\Omega\), and let us prove it for \(\Omega\) with \(|\Omega|=n+1\). Chopping out one (arbitrary) point from the set \(\Omega\), we can express it as
\[
\Omega=\Omega_0\cup\{x_0\}, \quad \text{where } |\Omega_0|=n.
\]
The class \(\mathcal{F}\) then naturally breaks into two sub-classes
\[
\mathcal{F}_0:=\{f\in\mathcal{F}: f(x_0)=0\} \quad\text{and}\quad \mathcal{F}_1:=\{f\in\mathcal{F}: f(x_0)=1\}.
\]
By the induction hypothesis, the counting function
\[
S(\mathcal{F}) = \left|\{\Lambda\subseteq\Omega : \Lambda \text{ is shattered by } \mathcal{F}\}\right|
\]
satisfies
\[
S(\mathcal{F}_0)\ge|\mathcal{F}_0| \quad\text{and}\quad S(\mathcal{F}_1)\ge|\mathcal{F}_1|. \tag{8.28}
\]
Here, to properly use the induction hypothesis, we restrict the functions in \(\mathcal{F}_0\) and \(\mathcal{F}_1\) to the \(n\)-point set \(\Omega_0\).

To complete the proof, all we need to check is
\[
S(\mathcal{F}) \ge S(\mathcal{F}_0)+S(\mathcal{F}_1), \tag{8.29}
\]
for then (8.28) would give \(S(\mathcal{F})\ge|\mathcal{F}_0|+|\mathcal{F}_1|=|\mathcal{F}|\), as needed.

Inequality (8.29) may seem trivial. Any set \(\Lambda\) that is shattered by \(\mathcal{F}_0\) or \(\mathcal{F}_1\) is automatically shattered by the larger class \(\mathcal{F}\), and thus each set \(\Lambda\) counted by \(S(\mathcal{F}_0)\) or \(S(\mathcal{F}_1)\) is automatically counted by \(S(\mathcal{F})\). The problem, however, lies in the double counting. Assume the same set \(\Lambda\) is shattered by both \(\mathcal{F}_0\) and \(\mathcal{F}_1\). The counting function \(S(\mathcal{F})\) will not count \(\Lambda\) twice. However, a different set will be counted by \(S(\mathcal{F})\), which was not counted by either \(S(\mathcal{F}_0)\) or \(S(\mathcal{F}_1)\) — namely, \(\Lambda\cup\{x_0\}\). A moment’s thought reveals that this set is indeed shattered by \(\mathcal{F}\). (Check!) This establishes inequality (8.29) and completes the proof of Pajor lemma.

Let’s illustrate the key point in the proof of Pajor lemma:

**Example 8.3.8.** Let us again go back to Example 8.3.4. Following the proof of Pajor lemma, we chop out \(x_0=3\) from \(\Omega=\{1,2,3\}\), making \(\Omega_0=\{1,2\}\). The class \(\mathcal{F}=\{001,010,100,111\}\) then breaks into two sub-classes
\[
\mathcal{F}_0=\{010,100\} \quad\text{and}\quad \mathcal{F}_1=\{001,111\}.
\]
There are exactly two subsets \(\Lambda\) shattered by \(\mathcal{F}_0\), namely \(\{1\}\) and \(\{2\}\), and **the same** subsets are shattered by \(\mathcal{F}_1\), making \(S(\mathcal{F}_0)=S(\mathcal{F}_1)=2\). Of course, the same two subsets are also shattered by \(\mathcal{F}\), but we need two more shattered subsets to make \(S(\mathcal{F})\ge4\) for the key inequality (8.29). Here is how we construct them: append \(x_0=3\) to the already counted subsets \(\Lambda\). The resulting sets \(\{1,3\}\) and \(\{2,3\}\) are also shattered by \(\mathcal{F}\), and we have not counted them yet. Now we have at least **four** subsets shattered by \(\mathcal{F}\), making the key inequality (8.29) true.

## 8.3.3 Sauer–Shelah Lemma

We now deduce a remarkable upper bound on the cardinality of a function class in terms of VC dimension:

**Lemma 8.3.9 (Sauer–Shelah Lemma).** *Let \(\mathcal{F}\) be a class of Boolean functions on an \(n\)-point set \(\Omega\). Then*
\[
|\mathcal{F}| \le \sum_{k=0}^{d} \binom{n}{k} \le \left(\frac{en}{d}\right)^d
\]
where \(d=\operatorname{VC}(\mathcal{F})\).

*Proof.* Pajor lemma states that \(|\mathcal{F}|\) is bounded by the number of subsets \(\Lambda\subseteq\Omega\) shattered by \(\mathcal{F}\). The cardinality of each such set \(\Lambda\) is bounded by \(d=\operatorname{VC}(\mathcal{F})\), according to the definition of VC dimension. Thus
\[
|\mathcal{F}| \le \left|\{\Lambda\subseteq\Omega: |\Lambda|\le d\}\right| = \sum_{k=0}^{d} \binom{n}{k},
\]
since the sum in the right-hand side gives the total number of subsets of an \(n\)-element set with cardinalities at most \(d\). This proves the first inequality of the Sauer–Shelah lemma. The second inequality follows from the bound on the binomial sum we proved in Exercise 0.6.

Both Pajor and Sauer–Shelah lemmas are generally sharp (try Exercise 8.19).

## 8.3.4 Growth function

The Sauer–Shelah lemma assumes that the domain \(\Omega\) is finite. What about function classes \(\mathcal{F}\) on infinite domains like \(\Omega=\mathbb{R}^n\)? It is often convenient to measure the complexity of \(\mathcal{F}\) by the growth function:

**Definition 8.3.10** (Growth function). Let \(\mathcal{F}\) be a class of Boolean functions on a domain \(\Omega\). The growth function of \(\mathcal{F}\) is defined as the maximum number of functions that can be obtained by restricting all functions in \(\mathcal{F}\) to a subset of \(n\) elements:
\[
\Pi_{\mathcal{F}}(n) = \sup\left\{\left|\mathcal{F}\right|_{\Lambda} : \Lambda\subseteq\Omega,\ |\Lambda|=n\right\}.
\]

In this light, the VC dimension of \(\mathcal{F}\) can be seen as the largest \(d\) for which \(\Pi_{\mathcal{F}}(d)=2^d\). Immediate bounds on the growth function are
\[
2^d \le \Pi_{\mathcal{F}}(n) \le \left(\frac{en}{d}\right)^d \quad\text{for all } n\ge d, \tag{8.30}
\]
if \(d=\operatorname{VC}(\mathcal{F})<\infty\). The lower bound is a restatement of (8.27) and the upper bound follows from the Sauer–Shelah lemma (Lemma 8.3.9).

To see how the growth function can be useful, let’s deduce from (8.30) the stability of VC dimension with respect to natural operations.

**Proposition 8.3.11** (VC stability). Let \(\mathcal{F}\) and \(\mathcal{G}\) be two classes of Boolean functions on the same domain. Let
\[
\mathcal{F}\wedge\mathcal{G} = \{f\wedge g : f\in\mathcal{F},\ g\in\mathcal{G}\}
\]
where \(f\wedge g\) denotes the pointwise minimum of the functions \(f\) and \(g\). Then
\[
\operatorname{VC}(\mathcal{F}\wedge\mathcal{G}) \le 10\max\bigl(\operatorname{VC}(\mathcal{F}),\operatorname{VC}(\mathcal{G})\bigr).
\]
The same holds for the pointwise maximum \(\vee\).

*Proof.* Assume for contradiction that \(n := \operatorname{VC}(\mathcal{F}\wedge\mathcal{G}) > 10d\), where \(d=\max(\operatorname{VC}(\mathcal{F}),\operatorname{VC}(\mathcal{G}))\). Then
\[
2^n \le \Pi_{\mathcal{F}\wedge\mathcal{G}}(n) \le \Pi_{\mathcal{F}}(n)\cdot\Pi_{\mathcal{G}}(n) \le \left(\frac{en}{d}\right)^{2d}.
\]
(The first and last bounds follow from (8.30), and the middle bound should be clear by definition.) However, a simple calculation shows that \(2^n > (en/d)^{2d}\) whenever \(n>10d\). Contradiction.

Proposition 8.3.11 can be extended to any particular way of combining classes of functions — try Exercise 8.21. It can be helpful when we want to bound the VC dimension without computing it directly, such as in this example:

**Example 8.3.12** (Strips). A strip in \(\mathbb{R}^n\) is a set of the form
\[
\{x : |\langle a,x\rangle-b|\le c\} \qquad\text{where } a\in\mathbb{R}^n,\ b,c\in\mathbb{R},
\]
see Figure 8.7. Let \(\mathcal{F}\) be the class of indicators of strips. Example 8.3.5 gives
\[
\operatorname{VC}(\mathcal{F}) \le 10(n+1) \le 20n.
\]
Indeed, each strip can be represented as the intersection of two half-spaces \(\{x : \langle a,x\rangle-b\le c\}\) and \(\{x : \langle a,x\rangle-b\ge -c\}\). Thus the indicator of each strip is the pointwise minimum of the indicators of two half-spaces. Now apply the VC stability property (Proposition 8.3.11) and the result in Example 8.3.5.

![Figure 8.7](img/b122213aed28c1888de83a894123323e_242_0.png)

**Figure 8.7** Four different strips in \(\mathbb{R}^2\).

For more practice with growth function, show a mind-blowing dichotomy — this function can grow either polynomially or exponentially (Exercise 8.20) and compute the VC dimension of the union (Exercise 8.22).

## 8.3.5 Covering numbers via VC dimension

Covering numbers usually grow exponentially with dimension (see (4.17) for example). Now, let’s refine this heuristic by replacing the algebraic dimension with VC dimension — which can save us a lot.

Let \(\mathcal{F}\) be a class of Boolean functions on some domain \(\Omega\), and let \(\mu\) be any probability measure on \(\Omega\). Define the distance between functions
\[
d(f,g)=\|f-g\|_{L^2(\mu)} = \left(\mathbb{E}(f-g)(X)^2\right)^{1/2}, \tag{8.31}
\]
where \(X\) is a random variable with distribution \(\mu\). (If you have not done measure theory, just take an arbitrary random variable \(X\) taking values in \(\Omega\), and think of \(\mu\) as the name for the distribution of \(X\).)

Now let’s bound the covering numbers \(\mathcal{N}(\mathcal{F},L^2(\mu),\epsilon)\) of the class \(\mathcal{F}\) with respect to the metric (8.31):
