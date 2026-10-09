of the Lie group are analytic functions. As the function is continuously differentiable, calculus can be used to study the Lie group. Thus, the Lie group is the most extensively studied group.

# 6.1.2.1 Local properties of the Lie group

In the group space adjacent to the corresponding elements, called the adjacent elements, because the parameters of the constant element are often selected as zero (constant element adjacent elements), the parameters are infinitesimal, known as infinitesimal elements. Infinitesimal is a limit process. The nature of infinitesimal elements of the Lie group determines the local properties of the Lie group.

Consider an element g(\alpha) of the Lie group, where \alpha represents a set of m consecutive group parameters, and \alpha = 0 represents a unit element. If \alpha is small, g(\alpha) is very close to the unit, and it can be used in the vicinity of units for Taylor expansion:

```
$$ g(\alpha) = g(0) + \alpha^i \left. \frac{\partial g}{\partial \alpha^i} \right|_{\alpha^i=0} + \ldots . $$
```

Here, we use the tensor symbol to omit the sum of i, and we introduce the symbol $X_i = \left. \partial g / \partial \alpha^i \right|_{\alpha^i=0}$, which is called an infinite scent operator or generator of a group. It is the derivative of the group element in the vicinity of the unit, and its number is also m. Note that the generator $X_i$ is independent of the group element, which reflects the nature of the group, i.e., the elements of the Lie group are expressed by generating generators and group parameters.

Thus, the difference between different populations is expressed as the nature and number of generators, and the number of generators, i.e., the number of group parameters, is called the dimension of the group. The exchange algebra between generators portrays the nature of the Lie group.

The generators of linear representations satisfy the common reciprocity relation:

```
$$ I_jI_k - I_kI_j = i \sum_\ell c_{jk}^\ell I_\ell $$ $$ c_{jk}^\ell = \left\{ \frac{\partial S_{\ell k}(r)}{I_j} - \frac{\partial S_{\ell j}(r)}{r_k} \right\}_{I=0} \ . $$
```

The algebra is closely related to the concept of the Lie group, and many of the properties of the Lie group can be discussed directly through Lie algebra. According to this concept, the reciprocity relation of the Lie group generators constitutes a reflection of the nature of Lie algebra.

Consider an input space G. If the linear space g on G has a binary operation $\{ x, y \} \rightarrow [ x, y ]$ (often referred to as transposition or inclusion), and it satisfies the following conditions:

+   (1) This binary operation is bilinear, i.e.,
$\left[ \lambda x + \mu y, z \right] = \lambda [x,z] + \mu [y,z] \ , \quad \forall \lambda \ , \ \mu \in G \ , \quad \forall x \ , \ y \ , \ z \in g \ ;$