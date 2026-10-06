
## 5.2 Variable Order Structure

```
$A \prec_{s,K} B \Longleftrightarrow \max \left\{ \sup_{b\in B\ a\in A} \psi(a-b, a), \sup_{a\in A\ b\in B} \psi(a-b, b) \right\} \leq 0$
```

if the arising terms exist.

It is obvious that these terms exist if the linear space $Y$ is normed, the sets $A$ and $B$ are weakly compact, and the functional $\psi$ is weakly lower semicontinuous (compare [72, Theorem 2.3]).

We investigate set optimization problems with a variable order structure. Based on the set less order relation in a real linear space $Y$, we consider a family $\mathcal{F}$ of nonempty subsets of $Y$, and we investigate minimal sets of $\mathcal{F}$ in a similar way as in Definition 5.2.

**Definition 5.4** Assumption 2.2 let $\mathcal{F}$ be a family of nonempty subsets of $Y$. A set $\tilde{A} \in \mathcal{F}$ is called a *minimal set* of $\mathcal{F}$ iff

```
$A \prec_{s,K} \tilde{A}, \tilde{A} \in \mathcal{F} \Longimplies \tilde{A} \prec_{s,K} A$.
```

Minimal sets can be characterized using the equivalence in Proposition 5.6.

**Theorem 5.1** [[74, Theorem 5.1]] Let Assumption 2.2 be satisfied, and let $\psi$ be a $-K$-convex representing functional. Then we have

$\tilde{A} \in \mathcal{F}$ is a minimal set of $\mathcal{F}$

```
$\Longleftrightarrow \forall A \in \mathcal{F}: \max \left\{ \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(\tilde{a}-a, \tilde{a}), \sup_{\tilde{a}\in\tilde{A}\ a\in A} \psi(a-\tilde{a}, \tilde{a}) \right\} \leq 0 \\ \text{or}$
```

```
$\max \left\{ \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(\tilde{a}-a, \tilde{a}), \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(a-\tilde{a}, \tilde{a}) \right\} > 0$
```

(5.5)

if the arising terms exist.

## **Proof**

- (a) Let $\tilde{A} \in \mathcal{F}$ be a minimal set of $\mathcal{F}$, and let $A \in \mathcal{F}$ be arbitrarily chosen. Then we consider two cases:

- (i) If $A \prec_{s,K} \tilde{A}$, then we obtain $\tilde{A} \prec_{s,K} A$, i.e., with Proposition 5.6

```
$$\max \left\{ \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(\tilde{a}-a, \tilde{a}), \sup_{\tilde{a}\in\tilde{A}\ a\in A} \psi(\tilde{a}-a, \tilde{a}) \right\} \leq 0.
```

- (ii) If $A \not\prec_{s,K} \tilde{A}$, we conclude with Proposition 5.6

```
$$\max \left\{ \min_{\tilde{a} \in A, a \in A} \psi(a - \tilde{a}, a), \min_{a \in A, \tilde{a} \in \tilde{A}} \psi(a - \tilde{a}, a) \right\} > 0.$$
```

This shows the first part of the assertion.

- Let $\tilde{A} \in \mathcal{F}$ be not a minimal set of $\mathcal{F}$. Then there exists some $A \in \mathcal{F}$ with $A \not\prec_{s,K} \tilde{A}$, i.e., with Proposition 5.6

```
$$\max \left\{ \min_{\tilde{a} \in A, a \in A} \psi(a - \tilde{a}, a), \min_{a \in A, \tilde{a} \in \tilde{A}} \psi(a - \tilde{a}, a) \right\} \le 0,$$
```

and $A \not\prec_{s,K} A$, i.e., with Proposition 5.6

```
$$\max \left\{ \min_{\tilde{a} \in A, a \in A} \psi(a - \tilde{a}, a), \min_{\tilde{a} \in \tilde{A}, a \in A} \psi(a - \tilde{a}, a) \right\} > 0.$$
```

Hence, the condition (5.5) is not fulfilled.

Theorem 5.1 is a slight extension of a result of Eichfelder and Pelecka [37, Theorem 4.1, (iii]) to the set less order relation, and its proof follows the lines of the proof of [37], Theorem 4.1, (iii).

## 5.3 Bibliographical Notes

This chapter presents results of Jahn [73, 74]. First, we start with some general remarks on set optimization already given in [70]. Set optimization has developed from an extension of continuous optimization to problems with set-valued maps. Early contributions can be found in the 1977 paper of Borwein [21] and the 1980 paper of Oettel [109]. There are several approaches in set optimization; however, we restrict ourselves to the study of the so-called set approach (compare the book by Khan, Tammer, and Zinescu [85]). The set approach works with a realistic order relation for comparison of sets, which was introduced into optimization by Kuroiwa [91]; a first publication is by Kuroiwa, Tanaka, and Ha [92]. Hamel [55] pointed out that outside the optimization community this kind of comparison of sets was already used by Young [143] in algebra and by Nishidate [107] in fixed point theory. Childe and Walster [25] were concerned with the comparison of sets in computer science and interval analysis. Since Chatea and Walster introduced the name “set less” for comparison of sets, which is also implemented in Fortran [130], this name is now used in many publications (compare Definition 5.1). Hahn and Ha [75] examined these known order relations and introduced new ones that are more realistic in practice. A rewriting of set as inequalities was already given by Hernández and Marín [59, Theorem 3.10, (iii)] using an extension of the scalarizing function [43]. Such a rewriting of set as inequalities was also given by Köbis and Löhne [88, Theorem 3.3 and 3.8] for scalarizing functions and various order relations. The signed distance can be found in the papers of Gutiérrez, Müller, and Molina [47, Proposition 4.1], Chen, Ansari, and Yao [24], Novo and Sanchez [78, Theorem 5.1] and Ha [51, Proposition 3]. However, in Proposition 5.1 one does not need an explicit form of the scalarizing functional. The results in Proposition 5.2 and Remark 5.1 are also marked by Köbis and Löhne [88, Remark 1] for specific scalarizing functionals. The characterization of a minimal set in Corollary 5.1 shows that set optimization problems with fixed order structure can be difficult optimization problems. The definition of the less variable order relation (Definition 5.3) was first given by Eichfelder and Pelecka [36, Definition 2.4] together with a variety of other variable order relations for sets. For a subsequent proper see also the work of Köbis, Le, and Tammer [90]. Proposition 5.5 was first given in the proof of Theorem 4.1 by Eichfelder and Pelecka [37] and subsequently by Köbis, Le, and Tammer, Theorems 3 and 6 for special scalarizing functionals.

It is already noted on page 90 that Theorem 5.1 is only a slight extension of the result of Eichfelder and Pelecka [37, Theorem 4.1, (iii)]. In fact, Eichfelder and Pelecka [37] did not use the exact definition of in their proof, so their result is more general and can easily be rewritten for a -K functional.

## Part III Deep Learning

In addition to order analysis, deep learning is also closely related to optimization. In fact, mathematical optimization is an important tool for learning approaches in deep neural networks. Since deep neural networks generally have a very large number of parameters, one has to solve optimization problems with really many variables. Therefore, special numerical methods are needed to solve these problems.

For a better understanding of the mathematical background of deep learning, Chap. 6 provides a mathematical introduction to this cutting-edge area of research. On this basis, deep neural networks with set-valued inputs are investigated in Chap. 7. This set-valued approach is more computationally intensive but has the advantage of producing more robust predictions. As in other applications, robustness will play an increasingly important role in AI.

## Chapter 6 Basics of Deep Learning

**Abstract** The topics of this chapter are important basic principles of deep learning, a comprehensive discussion of gradient methods, and the treatment of numerical examples. These subjects are treated from a more mathematical point of view. In the context of deep neural networks, we limit the introductory presentation mainly to supervised learning. Both deterministic and stochastic gradient methods are discussed. In the deterministic variants, also called batch gradient descent methods, emphasis is placed on effective step size rules, such as those of Barzilai and Borwein (IMA J Numer Anal 8:141–148, 1988) and a new variant in Algorithm 6.3. The numerical examples are of an illustrative nature.

## 6.1 Introduction

For many years, we have witnessed the highly successful application of artificial intelligence (AI) in many fields, especially in the processing of images, text, language, sound, and many other areas of applications. Here, computer science interacts with various scientific disciplines such as medicine, natural sciences, economics, and engineering as biomedical engineering.

Deep learning is an important subfield of machine learning, which in turn is a mastery of AI. It enables the discovery of complex structures in datasets and their mathematical formalization. In essence, deep learning is used to find complex classes of mathematical functions that form the base for “intelligent” predictions or decisions. These function classes typically have a large number of parameters that can be optimally determined using an existing dataset. This requires the use of mathematical optimization methods that can handle a large number of variables and a complicated objective function. Some of these optimization methods are the subject of this chapter.

Mathematical optimization is proving to be a key technology for the solution of complex problems in the field of AI. To illustrate this, let's start with a very simple introductory
