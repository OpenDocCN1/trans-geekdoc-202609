
Hence, we can say that the basic task of group theory is how to determine the equivalence and irreducibility of representation, to find all unequal irreducible representations of a given group, and how to denote the irreducible expression as a distinct sum.

Schur’s theorem is the most basic theorem in group representation theory, which applies to all groups and explains the basic characteristics of the unequal irreducible representation of groups.

> **Theorem 6.1.** Let $D^{(1)}(R)$ and $D^{(2)}(R)$ be the two unequal irreducible representations of group G, with dimensions $m_1$ and $m_2$, respectively, and let X be an $m_1 \times m_2$ matrix. If every element R satisfies:
>
> $$D^{(1)}(R)X = XD^{(2)}(R),$$
> $$\sum_{\rho} D^{(1)}_{\nu\rho}(R)X_{\rho\mu} = \sum_{\rho} X_{\nu\rho}D^{(2)}_{\rho\mu}(R)$$
>
> then X = 0.

> **Inference 6.1.** The matrix of all the representable matrices D(R) of the irreducible representation D(G) must be a constant matrix, i.e., if D(R)X = XD(R), then $X = \lambda I$, where \lambda is a constant.

The main task of group theory is to find all the inequality irreducible representations of various typical groups and study the reduction method of reducible representation. First, find the group of all non-equivalent irreducible characteristics of the standard, i.e., the characteristics of the standard table, called the signature table. Then, we determine the irreducible representation matrix. Since the group elements can be expressed as the product of the generator, it is possible to determine the matrix of the generator.

## 6.1.2 Basic properties of the Lie group

The Lie group is a continuous group, and each element R can be described by a set of independent real parameters $(r_1, r_2 \dots)$ that change continuously within a certain area. A one-to-one correspondence is required between the group element and the parameter value in the region of change of the parameter. The number of independent real parameters is called the order of successive groups. The change area of parameters is called the group space.

Set element $R \in G$. The parameter is $r_1, r_2 \dots, r_g$, abbreviated as $R(r_1, r_2 \dots, r_g) = R(r)$. For the product of group elements, $R(r)S(s) = T(t)$, g parameters $t_j$ are functions of 2g variables $r_i$ and $s_k$: $t_j = f_j(r_1, \dots, r_g; s_1, \dots, s_g) = f_j(r; s)$.

The g functions $f_j(r; s)$ are called combinatorial functions of continuous groups, which fully describe the product rules of group elements. The combination functions of the Lie group are analytic functions. As the function is continuously differentiable, calculus can be used to study the Lie group. Thus, the Lie group is the most extensively studied group.

### 6.1.2.1 Local properties of the Lie group

In the group space adjacent to the corresponding elements, called the adjacent elements, because the parameters of the constant element are often selected as zero (constant element adjacent elements), the parameters are infinitesimal, known as infinitesimal elements. Infinitesimal is a limit process. The nature of infinitesimal elements of the Lie group determines the local properties of the Lie group.

Consider an element g(\alpha) of the Lie group, where \alpha represents a set of m consecutive group parameters, and \alpha = 0 represents a unit element. If \alpha is small, g(\alpha) is very close to the unit, and it can be used in the vicinity of units for Taylor expansion:

$$ g(\alpha) = g(0) + \alpha^i \left. \frac{\partial g}{\partial \alpha^i} \right|_{\alpha^i=0} + \ldots . $$

Here, we use the tensor symbol to omit the sum of i, and we introduce the symbol $X_i = \left. \partial g / \partial \alpha^i \right|_{\alpha^i=0}$, which is called an infinitesimal operator or generator of a group. It is the derivative of the group element in the vicinity of the unit, and its number is also m. Note that the generator $X_i$ is independent of the group element, which reflects the nature of the group, i.e., the elements of the Lie group are expressed by generating generators and group parameters.

Thus, the difference between different groups is expressed as the nature and number of generators, and the number of generators, i.e., the number of group parameters, is called the dimension of the group. The exchange algebra between generators portrays the nature of the Lie group.

The generators of linear representations satisfy the common reciprocity relation:

$$ I_jI_k - I_kI_j = i \sum_\ell c_{jk}^\ell I_\ell $$ 
$$ c_{jk}^\ell = \left\{ \frac{\partial S_{\ell k}(r)}{I_j} - \frac{\partial S_{\ell j}(r)}{r_k} \right\}_{I=0} \ . $$

The algebra is closely related to the concept of the Lie group, and many of the properties of the Lie group can be discussed directly through Lie algebra. According to this concept, the reciprocity relation of the Lie group generators constitutes a reflection of the nature of Lie algebra.

Consider an input space G. If the linear space g on G has a binary operation $\{ x, y \} \rightarrow [ x, y ]$ (often referred to as transposition or inclusion), and it satisfies the following conditions:

- (1) This binary operation is bilinear, i.e.,
  $\left[ \lambda x + \mu y, z \right] = \lambda [x,z] + \mu [y,z] \ , \quad \forall \lambda \ , \ \mu \in G \ , \quad \forall x \ , \ y \ , \ z \in g \ ;$
- (2) [x, x] = 0, \forall x \in \mathfrak{g};
- (3) The Jacobi identity is established, i.e.,
  \begin{equation*} \text{[x, [y, z]] + [y, [z, x]] + [z, [x, y]] = 0, \quad \forall x, y, z \in \mathfrak{g}} \end{equation*}

then we say that $\mathfrak{g}$ is the Lie algebra on G.

In fact, when the nature of the Lie group is attributed to easy generation, such as an operation loop, i.e., the total effect after several operations, and returning to the unit element. This mainly reflects the local nature of the continuum. Therefore, the local identity of the Lie group is determined. If there are two or more groups, although the overall nature is different, the local nature and structure are the same; they correspond to the same Lie algebra, such as SU(2) group and SO(3) group. This relationship between the Lie group and its covering group is what we will discuss.

### 6.1.2.2 Overall properties of the Lie group

The overall nature of the Lie group study is to study the topological properties of the Lie group space. First, we discuss the connectivity of the group space. If any two elements in the group, which are in the group space as corresponding points, can be contained in a completely inclusive connection within the group space, then the group space is called connected. Such a continuous group is called a simply continuous group. The SO(3) group is a simple Lie group. Conversely, if the group space is divided into several pieces that are not linked, then this continuous group is called a mixed continuous group. For simple Lie groups, the elements of the groups can be expressed as infinitely many infinitesimal elements. In addition to the infinitesimal elements, it is necessary to give a special element (including the constant) in each successive slice of the group space, and their product can represent any element. For the linear representation, we can see that the representation matrix $D(R)$ of any element $R$ of the simple Lie group can be calculated by the generator, but for the mixed Lie group, we must also know the representation matrix $D(\sigma)$ of the spatial inversion element.

In the group space of the mixed Lie group, the set of the corresponding elements of the continuous piece containing the constant element constitutes the invariant subgroup of the mixed Lie group, and the other successive elements correspond to the cosine of the invariant subgroup. Therefore, the nature of the mixed Lie group is determined by the nature of a simple Lie group (invariant subgroup) and a representative element in each successive piece (coset).

Next, we discuss the connectivity of the Lie group. In the group space of a simple Lie group, the point of the element R can be connected to many lines by the corresponding point of the constant element. Some connections can change continuously in the group space, whereas others cannot. In this way, these connections are divided into groups, and the same group of connections can be continuously changed in the group space, whereas the connection of different groups cannot. The number of
