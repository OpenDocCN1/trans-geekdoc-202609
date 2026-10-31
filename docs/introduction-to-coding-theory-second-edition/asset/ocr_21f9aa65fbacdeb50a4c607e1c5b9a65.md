as well (use the inverse permutation). Also, if $\mathcal{C}$ is equivalent to $\mathcal{D}$, and $\mathcal{D}$ is equivalent to $\mathcal{E}$, then $\mathcal{C}$ is equivalent to $\mathcal{E}$. All codes equivalent to some code $\mathcal{C}$ form an **equivalence class**. The number of all permutations of an $n$-set is $n!$. The group $S_n$ of all permutations on $n$ objects is the **symmetric group**.

Such a clearly defined notion of equivalence is really helpful. As an example, if I want to decide the existence of a linear code with certain parameters $[n,k,d]_q$, I can assume the generator matrix starts with a $(k,k)$-unit matrix, that is, $G=(I|A)$ where $A$ is a $(k,n-k)$-matrix. Why is that so? Assume a code with these parameters exists, with generator matrix $G$. There must be some $k$ columns of $G$, which are linearly independent.

Choose a permutation $\sigma$ mapping these $k$ coordinates into the first $k$ coordinates. The image of my code under $\sigma$ is an equivalent code with a generator matrix whose $k$ first columns are linearly independent. After Gauß elimination, we should find a generator matrix of the form $G=(I|A)$.

It should now be clear when two codes are equivalent under permutations of coordinates. A highly interesting situation occurs if we find a permutation $\sigma$ such that $\sigma(\mathcal{C})=\mathcal{C}$ (in words: the image of our code under $\sigma$ is the code itself). In this case we call $\sigma$ an **automorphism** of $\mathcal{C}$. The automorphisms of $\mathcal{C}$ form a subgroup, the **stabilizer** or automorphism group of $\mathcal{C}$. We saw a large example in Chapter 7. The generator matrix for the binary Golay code $[23,12,7]_2$ given there has the special feature that all rows are cyclic shifts of the first row. In other words, the cyclic permutation

$\sigma : 1 \mapsto 2,\ 2 \mapsto 3, \dots\ 22 \mapsto 23,\ 23 \mapsto 1$

is an automorphism of $\mathcal{G}_{23}$.

It is clear that the identity permutation (fixing all coordinates) always is an automorphism. If $\sigma$ is an automorphism, then the inverse permutation $\sigma^{-1}$ is an automorphism. Also, if $\sigma_1$ and $\sigma_2$ both are automorphisms, then the concatenation $\sigma_2 \circ \sigma_1$ is an automorphism as well. In other words, the set of all automorphisms of a code $\mathcal{C}$ is a group, the automorphism group.

# **12.18 Definition.** *The permutation automorphism group of a code $\mathcal{C}$ of length $n$ is the group of all permutations $\sigma$ of the coordinates which satisfy $\sigma(\mathcal{C})=\mathcal{C}$.*

As an example, consider the following generator matrix of an octal (8-ary) four-dimensional code of length 16 :

$$\begin{pmatrix}1 0 0 0 a_1 a_2 a_3 a_4 a_1^2 a_2^2 a_3^2 a_4^2 a_1^4 a_2^4 a_3^4 a_4^4\\0 1 0 0 a_2 a_1 a_4 a_3 a_2^2 a_1^2 a_4^2 a_3^2 a_2^4 a_1^4 a_4^4 a_3^4\\0 0 1 0 a_3 a_4 a_1 a_2 a_3^2 a_4^2 a_1^2 a_2^2 a_3^4 a_4^4 a_1^4 a_2^4\\0 0 0 1 a_4 a_3 a_2 a_1 a_4^2 a_3^2 a_2^2 a_1^2 a_4^4 a_3^4 a_2^4 a_1^4\end{pmatrix}$$

Here $(a_1,a_2,a_3,a_4)=(\epsilon^6,\epsilon^2,\epsilon,1)$ and the same representation of $\mathbb{F}_8$ as in Chapter 4 is used. The parameters of this code are $[16,4,12]_8$, but we do not want to prove this here.