
Where $\frac{p - 1}{2}$ is even when $p \equiv 1 \pmod 4$ and odd when $p \equiv 3 \pmod 4$. Consequently, $\frac{p - 1}{2} \cdot \frac{q - 1}{2}$ is even if $p \equiv 1 \pmod 4$ or $q \equiv 1 \pmod 4$, while $\frac{p - 1}{2} \cdot \frac{q - 1}{2}$ is odd if $p \equiv q \equiv 3 \pmod 4$. Hence,

$$
\left( \frac{p}{q} \right)\left( \frac{q}{p} \right) = \left\{
\begin{matrix}
1, & \text{if } p \equiv 1 \pmod 4 \text{ or } q \equiv 1 \pmod 4 \text{ (or both)} \\
-1, & \text{if } p \equiv q \equiv 3 \pmod 4
\end{matrix}
\right.
$$

(1.9)

Since the only possible values of $\left( \frac{p}{q} \right)$ and $\left( \frac{q}{p} \right)$ are $\pm 1$. Therefore,

$$
\left( \frac{p}{q} \right) = \left\{
\begin{matrix}
\left( \frac{q}{p} \right), & \text{if } p \equiv 1 \pmod 4 \text{ or } q \equiv 1 \pmod 4 \text{ (or both)} \\
-\left( \frac{q}{p} \right), & \text{if } p \equiv q \equiv 3 \pmod 4
\end{matrix}
\right.
$$

(1.10)

### 1.1.7.2 Jacobi symbol

The Jacobi symbol is the generalization of the Legendre symbol and is formally defined as follows:

Let $n$ be a positive integer with prime factorization $n = p_1^{t_1} p_2^{t_2} \dots p_m^{t_m}$ and let $a$ be a positive integer relatively prime to $n$. Then the Jacobi symbol $\left( \frac{a}{n} \right)$ is defined by:

$$
\left( \frac{a}{n} \right) = \left( \frac{a}{p_1^{t_1} p_2^{t_2} \dots p_m^{t_m}} \right) = \left( \frac{a}{p_1} \right)^{t_1} \left( \frac{a}{p_2} \right)^{t_2} \dots \left( \frac{a}{p_m} \right)^{t_m}
$$

(1.11)

For example: $\left( \frac{2}{45} \right) = \left( \frac{2}{3^2 \cdot 5} \right) = \left( \frac{2}{3} \right)^2 \left( \frac{2}{5} \right) = (-1)^2 (-1) = -1$ and $\left( \frac{109}{385} \right) = \left( \frac{109}{5 \cdot 7 \cdot 11} \right) = \left( \frac{109}{5} \right) \left( \frac{109}{7} \right) \left( \frac{109}{11} \right) = \left( \frac{4}{5} \right) \left( \frac{4}{7} \right) \left( \frac{10}{11} \right) = \left( \frac{2}{5} \right)^2 \left( \frac{2}{7} \right)^2 \left( \frac{-1}{11} \right) = (-1)^2 (1) (-1) = -1$.

The above discussion regarding number theory concepts is an essential prerequisite for understanding the cryptographic algorithms [[4]](#01chap_01.xhtml#ref1_4), [[5]](#01chap_01.xhtml#ref1_5).

## 1.2 ABSTRACT ALGEBRA

Abstract algebra [[6]](#01chap_01.xhtml#ref1_6), [[7]](#01chap_01.xhtml#ref1_7) represents a class of powerful mathematical tools which have application in diverse fields. It is an extension of classical algebra which deals with abstract structures like groups, rings and fields instead of the usual number system. In this section, we will have an overview of these structures which is a prerequisite in understanding the core of cryptosystems.

An algebraic structure is characterized by the following three components:

*   An underlying set, which is often called the carrier set of the algebraic structure.
*   Operations defined on the elements of the underlying set.
*   Distinguished elements of the set called the constants of the algebraic structure.

For example: $(\mathbb{Z}, +, 0)$ is an algebraic structure, where $\mathbb{Z}$ = Set of integers, $+$ = Binary operation (Mapping from $\mathbb{Z}^2 \to \mathbb{Z}$), $\mathbb{Z}^2$ means the operation is applied between the two elements of the set $\mathbb{Z}$ and the resulting element also belongs to the set $\mathbb{Z}$, $0$ = $C$ Constant of algebra.

In general, the operator may take $m$ elements: $S^m \to S$, here, $m$ is called the arity of the operation. Any two algebraic structures may have the same signature, same number of operations with the same arity and the same number of constants. For example, $(\mathbb{Z}, +, \cdot, -, 1, 0)$ and $(\mathbb{R}, +, \cdot, -, 1, 0)$, here $\mathbb{R}$ is the set of real numbers. The two algebras having the same signature may not have the same property. $(\mathbb{Z}, -, 0)$ and $(\mathbb{Q}, +, 0)$. Here, commutative law holds for the second but not for the first.

**Sub-Algebraic Structure**: Let $A = \langle S, \circ, \triangle, k \rangle$ and $A' = (S', \circ', \triangle', k')$ be two algebras then $A'$ is a subalgebra of $A$ if i) $S' \subseteq S$, ii) $a \circ' b = a \circ b, \forall a, b \in S'$, iii) $\triangle' a = \triangle a, \forall a \in S'$ and iv) $k' = k$. If $A'$ is subalgebra of $A$ then $A'$ has the same signature as $A$ and obeys the same axioms.

**Zero and One Element**: Let $\circ$ be a binary operation on $S$. An element $1 \in S$ is an identity for operation $\circ$ if for every $x \in S$, $1_l \circ x = x \circ 1_r = x$. An element $0 \in S$ is a zero for operation $\circ$ if for every $x \in S$, $0_l \circ x = x \circ 0_r = 0$.

Consider the following algebraic structure: $S = \{a, b, c\}$, operation: $\circ$, group table:
$$
\begin{matrix}
\circ & a & b & c \\
a & a & b & b \\
b & a & b & c \\
c & a & b & c
\end{matrix}
$$
Find zeros and ones.

*Solution*: Right zero = $a, b$, No left zero, Left Identity = $b$, No right identity.

**Theorem**: Let $\circ$ be a binary operation on $S$ with left identity $1_l$ and right identity $1_r$. Then $1_l = 1_r$ and this is referred as a two-sided identity.

*Proof*: From left identity: $1_l \circ x = x$. Put $x = 1_r$. From right identity: $x \circ 1_r = x$. Put $x = 1_l$, $1_l \circ 1_r = 1_l$. Hence $1_r = 1_l$.

### 1.2.1 Semigroup

A semigroup is an algebraic structure with signature $\langle S, \circ \rangle$. Semigroups usually consist of algebraic structures with single binary operation and satisfy the closure and associative properties. For example: $\langle \mathbb{Z}, + \rangle$, $\langle \mathbb{Z}, \cdot \rangle$, $\langle \mathbb{R}, + \rangle$, $\langle \Sigma^*, \text{concatenation} \rangle$.

### 1.2.2 Monoid

A monoid is an algebraic structure with signature $\langle S, \circ, 1 \rangle$ where $\circ$ is a binary associative operation and $1$ is a two-sided identity for operation $\circ$. It satisfies the closure, associative and identity axioms. Examples of monoids include: $\langle \mathbb{Z}, +, 0 \rangle$, $\langle \mathbb{Z}, \cdot, 1 \rangle$, $\langle \mathbb{R}, +, 0 \rangle$, $\langle \Sigma^*, \text{concatenation}, \lambda \rangle$.

### 1.2.3 Group

A group is an algebraic structure with signature $\langle S, \circ, 1, - \rangle$ where $\circ$ is a binary associative operation and constant $1$ is a two-sided identity for operation $\circ$ and $-$ is a unary operation defined over the carrier such that $\forall x \in S, \bar{x}$ is an inverse of $x$ w.r.t. $\circ$. It satisfies the closure, associative, identity and inverse axioms. Examples of the group includes: $\langle \mathbb{Z}, +, 0, - \rangle$, here, $-$ represents unary minus. If $\circ$ operation is commutative then the group is known as an abelian group. Groups are the most commonly used algebraic structure in the construction of cryptosystems. Therefore, we will try to cover as much detail as possible keeping in mind the page limit.

**The groups possess a unique inverse**: Let element $a$ of the group have two inverses $b$ and $c$, $b \circ a = e$ and $c \circ a = e$, which implies $b \circ a = c \circ a \Rightarrow b \circ a \circ b = c \circ a \circ b$. Let $a \circ b = d$, $b \circ d = c \circ d$. Now, we know each element in the group has an inverse, $b \circ d \circ d^{-1} = c \circ d \circ d^{-1} \Rightarrow b \circ e = c \circ e$. Therefore, $b = c$.
