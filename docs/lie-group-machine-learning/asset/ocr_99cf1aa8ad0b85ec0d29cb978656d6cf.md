Hence, we can say that the basic task of group theory is how to determine the equivalence and irreducibility of representation, to find all unequal irreducible representations of a given group, and how to denote the irreducible expression as a distinct sum.

Schur’s theorem is the most basic theorem in group representation theory, which applies to all groups and explains the basic characteristics of the unequal irreducible representation of groups.

> **Theorem 6.1.** Let $D^{(1)}(R)$ and $D^{(2)}(R)$ be the two unequal irreducible representations of group G, with dimensions $m_1$ and $m_2$, respectively, and let X be an $m_1 \times m_2$ matrix. If every element R satisfies:

$$D^{(1)}(R)X = XD^{(2)}(R),$$
$$\sum_{\rho} D^{(1)}_{\nu\rho}(R)X_{\rho\mu} = \sum_{\rho} X_{\nu\rho}D^{(2)}_{\rho\mu}(R)$$

then X = 0.

> **Inference 6.1.** The matrix of all the representable matrices D(R) of the irreducible representation D(G) must be a constant matrix, i.e., if D(R)X = XD(R), then $X = \lambda I$, where \lambda is a constant.

The main task of group theory is to find all the inequality irreducible representations of various typical groups and study the reduction method of reducible representation. First, find the group of all non-equivalent irreducible characteristics of the standard, i.e., the characteristics of the standard table, called the signature table. Then, we determine the irreducible representation matrix. Since the group elements can be expressed as the product of the generator, it is possible to determine the matrix of the generator.

# ### 6.1.2 Basic properties of the Lie group

The Lie group is a continuous group, and each element R can be described by a set of independent real parameters $(r_1, r_2 \dots)$ that change continuously within a certain area. A one-to-one correspondence is required between the group element and the parameter value in the region of change of the parameter. The number of independent real parameters is called the order of successive groups. The change area of parameters is called the group space.

Set element $R \in G$. The parameter is $r_1, r_2 \dots, r_g$, abbreviated as $R(r_1, r_2 \dots, r_g) = R(r)$. For the product of group elements, $R(r)S(s) = T(t)$, g parameters $t_j$ are functions of 2g variables $r_i$ and $s_k$: $t_j = f_j(r_1, \dots, r_g; s_1, \dots, s_g) = f_j(r; s)$.

The g functions $f_j(r; s)$ are called combinatorial functions of continuous groups, which fully describe the product rules of group elements. The combination functions