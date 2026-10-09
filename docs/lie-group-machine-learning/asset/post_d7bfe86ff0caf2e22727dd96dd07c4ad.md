
resentation of the unitary symplectic group, and the unitary element $u$ as the coordinate transformation matrix in the $2l$ complex space

$$x_a \xrightarrow{u} x_a' = \sum_{b} u_{ab} x_b \tag{17.4}$$

Thus, it is possible to define $n$-order tensor and tensor bases with respect to the $USp(2l)$ transformation

$$\begin{array}{l} T_{a_1...a_n} \xrightarrow{u} (Ou)_{a_1...a_n} = \sum_{b_1...b_n} u_{a_1b_1} \cdot \cdot u_{a_nb_n}T_{b_1...b_n} \\ \Theta_{a_1...a_n} \xrightarrow{u} O_u \Theta_{a_1...a_n} = \sum_{b_1...b_n} \Theta_{b_1...b_n}u_{b_1a_1} \cdot \cdot u_{b_na_n} \tag{17.5} \end{array}$$

## 17.5 Basic concepts of quantum groups

### 17.5.1 Image description of the quantum group

Before introducing quantum groups, some explanations should be provided.

First, a domain $K$ is given as the basis for defining objects such as manifolds, functions, algebras, and so on. For physicists, $K$ is the complex field $C$ or the real field $R$. For mathematicians, $K$ can be any domain, but if $K$ is not $R$ or $C$, the ‘state space’ can only be algebraic clusters, or ‘observable meta functions’, i.e., regular functions. Second, we substitute the physical terms ‘state space’ and ‘observable meta function’ with pure mathematical terms ‘space’ and ‘function’, respectively. As mentioned above, the means adopted are different, and the meanings of the two terms are different. We denote the algebra of the function on space $X$ as $\mathrm{Fun}(X)$. As we know, regardless of the method we discuss, $\mathrm{Fun}$ is the inverse equivalence of the space category to the category of functional algebra. If $\phi:X \rightarrow Y$ is the morphism of the space, the homomorphism of the corresponding function algebra is $\phi: \mathrm{Fun}(Y) \rightarrow \mathrm{Fun}(X)$, which is defined as $\phi(a) = a \circ \phi$.

In classical mechanics and quantum mechanics, there are two basic concepts: states and observables. In classical mechanics, a state is a point in the manifold that can be observed as the element on the manifold for a conditional function. Conditions are determined according to the nature of the problem and the means of discussing the problem, such as continuity, differentiability, analyisability and, regularity. In any case, the observable element always constitutes a commutative associative algebra. In quantum mechanics, the state is a one-dimensional subspace of the Hilbert space, and the observable element is the operator that is suitable for some condition in the Hilbert space. The observable elements always form an associative algebra. However, generally this algebra is no longer commutative. Thus, from a mathematical point of view, the difference between classical mechanics and quantum mechanics is that the latter replaces commutative algebra with noncommutative algebra. In many questions of classical mechanics, the state space is often a group (Lie group, algebraic group, etc., which are determined by the nature of the problem and how it is defined). In the corresponding case of quantum mechanics, it is said that the state space is a quantum group.

### 17.5.2 Definition and decision algorithm of quantum group

For now we consider the classic case only. In mechanics, the state space is generally not measurable. We can infer the nature of the state space only from the observable elements. Thus, a mathematical problem arises: how to describe the nature of 'space is a group' only in the language of functions, and how to portray the structure of the groups in space.

First, consider the nature of the group.
For a group $G$, its properties are as follows:

- 1. Multiplication: For all $g_1, g_2 \in G$, then $g = g_1g_2 \in G$;
- 2. Associativity: $(g_1g_2)g_3 = g_1(g_2g_3)$;
- 3. Unit Element: For all $g \in G$, if $1_G \in G$, $1_Gg = g = g1_G$;
- 4. Inverse: For all $g \in G$, if $g^{-1} \in G$, $gg^{-1} = 1_G = g^{-1}g$.

We can suppose that we have a Lie group or algebraic group $G$ as a space: $A = Fun(G)$. As is well known, we have a function $Fun(G \times G) = A \otimes A$, in which the tensor product '$\otimes$' has different meanings in different instances. For example, if $G$ is a Lie group, '$\otimes$' is understood as a topological tensor product. We can use the contravariant equivalence functor $Fun$ and multiplication of groups $m: G \times G \rightarrow G$ to derive an algebra homomorphism $\Delta: A \rightarrow A \otimes A$, which is called comultiplication $A$. Thus, the associativity of groups is obviously equivalent to the commutativity shown in Figure 17.3(a). As for the functor $Fun$, it is equivalent to the commutativity shown in Figure 17.3(b) (commutativity is called the surplus associativity of $\Delta$):

Group $G$ has an identity element. It is equivalent to giving a map $e$ from the ordinary group $E$ to $G$ with only one element, satisfying the commutativity shown in Figure 17.4(a). By focusing on the fact that the algebra corresponding to $E$ is a nontriv-

![](img/456a7a56403cbb2b5f1a261793529a51_517_0.png)

![](img/456a7a56403cbb2b5f1a261793529a51_518_0.png)

**Fig. 17.4**: Different representations of the identity of groups.

![](img/456a7a56403cbb2b5f1a261793529a51_518_1.png)

**Fig. 17.5**: Different representations of the inverse of groups.

ial algebra $K$, for functor $\mathbf{Fun}$, we know that the identity is equivalent to a given algebra homomorphism: $\varepsilon: A \to K$, called an $A$ augmented mapping or counit, satisfying the commutativity shown in Figure 17.4(b). This commutativity is called the counit law or augmented law of $\varepsilon$.

Each element of group $G$ has an inverse element. Obviously, this is equivalent to a given group of anti-isomorphic $i: G \to G$, satisfying the commutativity shown in Figure 17.5(a). In the figure, $d: G \to G \otimes G$ is 'the diagonal morphism', i.e., $d(x) = (x, x)$. It is easy to verify that $d^{*}: A \otimes A \to A$ is the multiplication of $A$: $\mu$. Moreover, $f$ is the only group homomorphism of $G$ to $E$, and $\kappa$ is the unique algebraic homomorphism of $K$ to $A$. Similarly, for the functor $\mathbf{Fun}$, we know that the existence of the inverse is equivalent to a homomorphism $\gamma: A \to A$, called the pole mapping, satisfying the commutativity shown in Figure 17.5(b). This commutativity is called the pole law or the inverse law:

If the algebra on group $G$ is called $A$, the dual algebraic structure is introduced:

- (1) Comultiplication: $\Delta: A \to A \otimes A$ satisfying $\Delta(f) = \sum_{i} f_{1,i} \otimes f_{2,i}$. The use of Sweedler symbols can be abbreviated as $\Delta(f) = f_{(1)} \otimes f_{(2)}$;
- (2) Residual associate law: $(\Delta \otimes \mathrm{id}) \circ \Delta = (\mathrm{id} \otimes \Delta) \circ \Delta$;
- (3) Residual unit element: $\varepsilon(f_{1}f_{2}) = \varepsilon(f_{1})\varepsilon(f_{2})$;
- (4) Residual inverse: $S: m \circ (S \otimes \mathrm{id}) \circ \Delta = 1_{A}\varepsilon = m \circ (\mathrm{id} \otimes S) \circ \Delta$.

It can be seen that Hopf algebra has all the properties of a general group, but unlike the general group, Hopf algebras do not have commutativity. As in quantum mechanics, to meet such a non-exchange relationship between $[x, p] = i$, coordinate $X$ and phase $P$ can be regarded as a function of quantum phase space, and the elements in the Hopf algebra can be seen as a function in the quantum group. Then, we can give the definition of Hopf algebra. The definition of Hopf algebra and the definition of the group are very similar.

**Definition 17.20.** A Hopf algebra $(A, m, 1_A, \Delta, \varepsilon, S)$ is an associative algebra with unit element $1_A$, and it has the following properties:

$\Delta (f_1f_2) = \Delta(f_1)\Delta(f_2)$ (17.6)

$(\Delta \otimes \text{id}) \circ \Delta = (\text{id} \otimes \Delta) \circ \Delta$ (17.7)

$\varepsilon (f_1f_2) = \varepsilon(f_1)\varepsilon(f_2)$ (17.8)

$(\varepsilon \otimes \text{id}) \circ \Delta = \text{id} \circ (\text{id} \otimes \varepsilon) \circ \Delta$ (17.9)

$m \circ (S \otimes \text{id}) \circ \Delta = 1_A\varepsilon = m \circ (\text{id} \otimes S) \circ \Delta$ (17.10)

where $A$ is an algebra in group $G$, $m$ is a non-commutative multiplicative mapping, $m (f_1 \otimes f_2) = f_1f_2$; $1_A$ is an identity element, $1_Af = f = f1_A$, $\Delta$ is a comultiplication mapping, $\Delta(f) = \sum_i f_{1i} \otimes f_{2i}$, $id$ is a characteristic mapping satisfying $id(f) = f$, $\varepsilon$ is a residual unit element satisfying $\varepsilon(f) = f(1_G)$, and $S$ is a residual inverse satisfying $S(f)(g) = f (g^{-1})$.

In the classical case, saying that a space is a group is equivalent to saying that a function algebra is a commutative Hopf algebra. However, not every commutative Hopf algebra can be used as a function algebra on a certain group. In the case of an algebraic group, the algebra calls the object in the inverse category of the category of the Hopf algebra an affine group. The category of affine algebraic groups is a complete subcategory of the category of affine groups. Back in the quantum situation, we naturally make the following definitions.

**Definition 17.21.** Algebras (not necessarily commutative) are called quantum semigroups; (not necessarily commutative) objects in the inverse category of Hopf algebras are called quantum groups.

In Definition 17.21, we treat the classical group as a quantum group – degenerate or bound quantum groups. It must be pointed out that the quantum group is no longer the usual sense of the group; it is not even the quantum affine space category (i.e., anti-algebra category) group. Moreover, unlike the affine group, it cannot be interpreted as a group functor.

Therefore, we can give the discrimination algorithm of quantum groups. Described in C language as follows:
