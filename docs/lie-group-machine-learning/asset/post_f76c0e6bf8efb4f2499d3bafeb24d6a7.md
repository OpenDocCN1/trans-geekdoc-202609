
# Fig. 6.2: Exchange diagram of $M_{1}$ and $M_{2}.$

**Proof.** The uniqueness is easy to prove. The following proof is about existence.

Let \(\{w_{i}\}\) be the base of the left invariant form \(1\), so that \(\psi^{*}\) is the transpose of \(\psi\). The form \(1\) on \(G \times H\) is \(\{\delta\pi_{1}(\psi^{*}(w_{i})) - \delta\pi_{2}(w_{i})\}\), where \(\pi_{1}\) and \(\pi_{2}\) are the standard projections on \(G \times H\) to \(G\) and \(H\), respectively. This form is left unchanged, and the generated ideal \(\mathcal{I}\) is a differential ideal. Thus, the maximal connected integral manifold \(I\) of \(\mathcal{I}\) through \((e, e)\in G \times H\) is a plum cluster of \(G \times H\), and its dimension is equal to the dimension of \(G\). In other words, it is a covering homomorphism.

It is assumed that \(G\) is simply connected, so \(\left.\pi_{1}\right|_{I}: I \to G\) is an isomorphism. Define \(\varphi: G \to H\) as \(\varphi = \pi_{2} \circ (\left.\pi_{1}\right|_{I})^{-1}\). Then, \(\varphi\) is a Lie group homomorphism, and \(\delta\varphi(w_{i}) = \psi^{*}(w_{i})\). Thus, \(d\varphi = \psi\) and the theorem is proved.

**Inference 6.3.** If a single-connected Lie group \(G\) and \(H\) have isomorphic Lie algebras, then \(G\) and \(H\) are isomorphic.

Ado theorem holds that for each Lie algebra, for a certain \(n\), there is a faithful representation in \(\operatorname{GL}(n, R)\). According to this theorem, if \(\frak{g}\) is a Lie algebra, then there is a Lie group, especially a single-connected Lie group, with \(\frak{g}\) for the algebra. In view of this result, we have the following:

**Theorem 6.7.** There is a one-to-one correspondence between the isomorphism of the algebra and the isomorphism of the single-connected Lie group.

**Proof.** If there are two curves \(\varphi_{i}: [0, a] \to M\) \((i = 1, 2)\), \(\varphi_{1}(0) = \varphi_{2}(0)\), and \(\varphi_{1}(a) = \varphi_{2}(a)\), having common start points and end points in \(M\), then \(M\) is simply connected. Let \(f: \tilde{M} \to M\) be a differentiable covering. The necessary and sufficient condition for being a universal coverage is that \(\tilde{M}\) is simply connected. Furthermore, the necessary and sufficient condition for a connected manifold \(M\) to be simply connected is that there is no nontrivial cover in it. In other words, if \(f_{1}: M_{1} \to M\) is an overide mapping in \(M\), then \(f\) must be a homeomorphism.

Let \(f: M_{1} \to M_{2}\) be a differentiable covering, \(\varphi: [0, a] \to M_{2}\) be a continuous parameter curve in \(M_{2}\), and \(p\) be an arbitrarily selected point in \(f^{-1}(\varphi(0))\). Then, there is a unique continuous mapping \(\tilde{\varphi}: [0, a] \to M_{1}\), which makes \(\tilde{\varphi}(0) = p\), \(f \circ \tilde{\varphi} = \varphi\), as shown in the following illustration, where \(\tilde{\varphi}\) is called a coverage curve for \(\varphi\).

**Definition 6.8.** Let \(p: M \to N\) be a covering map and \(f: I \to N\) be a road on \(N\). Then, \(f\) can be uniquely raised to road \(g: I \to M\) in \(M\), which makes \(p(g) = f\).

```
Algorithm 6.1: Judge the covering group
// Judge whether Lie group M is the covering group of the connected group
// Input: Lie group M, N
// Output: {0,1}
Procedure IsCovergroup(M,N)
If Isconnect(M) then
    For do
        If f and // At any point in M, a neighbourhood through f mapping belongs to N //
        then return 1;
        else
        return 0;
    endif
    endfor
else return 0;
endif
endprocedure
```

From the previous description, there is a one-to-one relationship between a Lie group and its Lie algebra. Since the connected groups of connected Lie group and single-connected covering groups are unique in the equivalent sense, it is only necessary to find the general coverage group of the Lie group, which can be used to solve a group of problems. Each point on the group manifold has a one-to-one correspondence with the group element, and the connection of any two points in the group manifold can be transformed into the equivalent curve on the group by the continuous deformation of the parameter space. As long as the cover of all the unequal irreducible expressions is found, the corresponding Lie group will be found.

# Theorem 6.8.

The connected group G must be connected, and the simply connected covering group $(\hat{G}, f)$ is called the universal covering group of G. Further, f is an isomorphism if and only if G itself is a single-connected Lie group.

Next, we present an algorithm for the universal covering group of the Lie group and simplify the Lie group problem to the problem of covering it.

```
Algorithm 6.2: Universal covering group algorithm for connected Lie group SCCG
//Input: Connected Lie group G
//Output: Universal covering group of G and covering mapping m
Step 1: Take the unit frame $(U, f)$. Create point set $\bigcup_{m=1}^{\infty} \overline{m(U \times U \times \cdots \times U)}$ starting from $U$.
Step 2: Take the elements $(u_1, u_2, \dots, u_m)$ and $(v_1, v_2, \dots, v_p)$ of this point set. According to $u, v, uv \in U$, we have the role $(u, v) = uv$. Further, $(u_1, u_2, \dots, u_m)$ changes with a limited step; check whether it can become $(v_1, v_2, \dots, v_p)$;
Step 3: The equivalence class of the element that satisfies the equivalent condition is denoted by $(u_1, u_2, \dots, u_m)^*$. Continue to select other elements;
Step 4: Make all the equivalence classes that fit the equivalence relation into a set of $\hat{G}$.
Step 5: If the covering mapping $f: (u_1, u_2, \dots, u_m)^* \longrightarrow u_1 u_2 \cdots u_m$ is established between the equivalence class set and $(u_1, u_2, \dots, u_m)$, then $(\hat{G}, f)$ is the coverage group of G.
```

The construction of the covering group shows that $df$ gives the isomorphism between the Lie algebra of $\tilde{G}$ and the Lie algebra of $G$. The reason is that for the unit elements $\tilde{e}$ and $e$ of $\tilde{G}$ and $G$, there exists the neighbourhood coordinates $\tilde{U}$ of the three-dimensional coordinates of the neighbourhood $\tilde{U}$ and $G$, so that $f$ is the homeomorphism of $\tilde{U}$ to $U$, and $df$ gives the algebraic isomorphism of the Lie algebra.

After finding the coverage group of the connected Lie group, for the unequal irreducible representation of the covering group, we must first find all their unequal irreducible signatures and list the signatures as the characteristic table. Then, we find the irreducible representation matrix. Since the group elements can be expressed as the product of the generator, it is sufficient to find the representation matrix of the generator. In fact, the common group of irreducible representation of the standard table, i.e., the matrix of the standard form and irreducible representation of the direct representation of decomposition, can be found in the book, and they only need to be applied to the learning problem.

### 6.2.3 Algorithm design

The purpose of learning is to find the optimal path from the initial state to the target state. If each state is called a node, it can form a group space. The group space is single-connected, i.e., each state can reach another state. In each connected state, each arc represents an operator, and one state can be directed to another state. Of course, according to different problems, a specific price can be set for the operation operator. If the starting point is from the initial node, and there is a path leading to the target node, then we can say that the learning problem is solvable. A path from the initial state to the target state forms an overlay.

To better describe real-world problems, we can map the sample data set $D$ to a new Lie group structure. However, the relationship between the various elements will not change corresponding to the original group of elements. On the one hand, we can regard $D'$ as a new set of samples produced by $D$, i.e., the coverage of the sample set $D$ does not change its essential characteristics, thus ensuring the correctness of the coverage mapping. On the other hand, for the two isomorphic sample sets $D$ and $D'$, the same road division method can be used, thus avoiding repetitive learning.

For example, for the individual points in the face (eyes, nose, mouth, etc.), take a number of sample points and their neighbourhood points. The continuous coverage of the mapping between the sample points maintains the original neighbourhood relationship, i.e., in the original space, the adjacent sample points remain adjacent in the mapped group.

Since the two Lie groups have local isomorphism, the topological properties of the original Lie group are maintained (both have the same Lie algebra). We know that the Lie algebra represents the reciprocal relation of the generators; hence, the groups also have the same generators. At the same time, the Lie algebra can be understood as a set
