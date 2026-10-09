
## 15.3 Mapping mechanism for learning expressions

abilities, and discriminant regions are all included in ob C. Discriminant functions, eigenvectors, probability formulae, and so on are all included in Mor C. Two classifiers constitute a special case of the multi-class case, which can be defined as category $\mathcal{D}$, so $\mathrm{ob} \, \mathcal{C} \to \mathrm{ob} \, \mathcal{D}$. Objects in C can correspond to objects in $\mathcal{D}$, $\mathrm{Mor} \, \mathcal{C} \to \mathrm{Mor} \, \mathcal{D}$, and a morphism in C can correspond to a morphism in $\mathcal{D}$.

$F: \mathcal{C} \to \mathcal{D}$, $A, B \in \mathrm{ob} \, \mathcal{C}$, then $F(A), F(B) \in \mathrm{ob} \, \mathcal{D}$. Assume that object A is a data set a1 and object B is a feature vector. Similarly, $G: \mathcal{C} \to \mathcal{D}$, $A, B \in \mathrm{ob} \, \mathcal{C}$, then $G(A), G(B) \in \mathrm{ob} \, \mathcal{D}$. The object A is a data set a2, and object B is a feature vector.

By the definition of functor, for the functor F, $A \mapsto F(A)$ and functor G, $A \mapsto G(A)$, there is a certain connection between data set objects $A_F$ and $A_G$. They all have the same law, i.e., they can produce many categories. Hence, there is a configuration shot that makes $A_F \to A_G$. By this reasoning, we obtain F(A) and G(A) for which there exists a morphism defined as $\alpha_A: F(A) \to G(A)$. Similarly, $\alpha_B: F(B) \to G(B)$.

The objects A, B in C have a morphism, denoted by $f: A \to B$, whose process and function are mainly to solve the feature vectors of data sets. By the definition of the functor $f \mapsto F(f)$, we can obtain $F(f): F(A) \to F(B)$.

Similarly, $G(f): G(A) \to G(B)$.

In summary, the two classifiers based on Bayesian decision theory can use the natural transformation. It is proven that the natural transformation theory has some applications in the learning problem.

In a learning system, the representation of any learning problem is expressed by a specific expression. The nature of the learning system is also determined by the effect of the expression. For a long time, this problem has been called the bottleneck problem of the system. According to the discussion in the previous section, the learning system can be represented by a category. How can the relation between the learning systems be expressed in the category of expressions? This section focuses on answering this question.

### 15.3.1 Abstract concept of an expression

The representation and application of the expression is the focus of this article. For convenience, we first need to find the commonalities of expressions. The original aim of category theory is to abstract many concrete mathematical objects and mappings with similar characteristics in different mathematical fields into unified concepts. This abstraction is achieved by morphism. For example, a set T is a single point set that can be equivalently represented as any set. From the viewpoint of category theory, there happens to be a mapping to set $T$. Therefore, morphism plays a major role in category theory. In fact, the research and application of learning expressions is nothing more than the relation of various mappings, and the theory of morphism can better reflect the relation of each part.

As a hypothesis, we consider a morphism in this learning expression. If any pair of parallel states in a pair is a morphism, then there is a left reducible, which is called a single morphism (monomorphism) of the category of the learning expression. Assume that $\mathbb{C}$ is a learning expression category, and $f: A \to B$ is a morphism in this learning expression. If any pair of parallel morphisms $g, h: C \to A$ in $\mathbb{C}$ satisfies $fg = fh$, we have $g = h$ (now called $f$ left reducible), where $f$ is called a monomorphism of the learning expression category.

Similarly, it can be assumed that $f$ is an epimorphism if and only if any pair of parallel morphism $g, h: B \to C$ satisfies $fg = fh$, and we have $g = h$ (now called $f$ right reducible).

The mapping principle of expressions in a linear discriminant function can be studied by means of the monomorphism and epimorphism of learning expressions.

**Example 15.5.** In linear learning category $\mathbb{C}$, there exists an epimorphism of the learning expression.

*Proof.* In the linear learning category $\mathbb{C}$, the object $X$ represents the data set $W$ that needs to be discriminated as the weight vector object. The morphism $f: X \cdot W \to B$ is a mapping of the data set object and the weight vector object to the discriminant function value object, denoted by $f: B(x) = W \cdot X + w_0$, where $w_0$ represents a threshold weight or bias for a variable value. The morphism $g: B \to R$ represents the mapping of the arithmetic distance process of the point distance from the hyperplane of the data set object. The object $R$ is an arithmetic distance object, which can distinguish the classification of the element points in $X$ and the distance from the hyperplane. Morphism $g$ can be represented by an expression $X = X_p + RW/\|W\|$ for its mapping process.

There is parallel morphism $g$ and morphism $h: B \to R$ at the same time, and the mapping process can be expressed by $R = B(x)/\|W\|$. For morphism $f, g, h$, $gf = hf$ can be obtained by the compound operation rate of category theory. The specific process is shown in Figure 15.6.

![](img/456a7a56403cbb2b5f1a261793529a51_451_0.png)

Since $g: X = X_p + RW / \|W\|$, i.e., $R = \|W\| / W(X - X_p)$ and $h: R = B(x) / \|W\|$, then

$$R = \frac{W \cdot X + w_0}{\|W\|} = \frac{W}{\|W\|} X + \frac{w_0}{\|W\|}\ .$$

Although the mapping process of morphism $g$, $h$ is different, the result and meaning of the mapping are quite similar; then, $g = h$. Hence, it is possible to have the full morphism of the learning expression in the linear learning category $\mathscr{C}$. $\square$

Before studying the expression of the functor, we must first understand the following assumptions and theorems.

$\mathscr{C}$ is a learning expression category, $A \in \mathrm{ob}\mathscr{C}$; define a functor $\mathscr{C}(A, -): \mathscr{C} \to \mathrm{Set}$ as follows:

$$B \mapsto \mathscr{C}(A, B), (f: B \to C) \mapsto (c(A, f), g \mapsto fg)\ .$$

We call $\mathscr{C}(A, -)$ the hom-functor on $A$. We can define the duality functor $\mathscr{C}(A, -): \mathscr{C}^{\mathrm{op}} \to \mathrm{Set}$. Under antithesis, we can define the contravariant hom-functor on $A$.

**Theorem 15.3.** (*Yoneda lemma*) *$\mathscr{C}$ is a category of learning expressions $A \in \mathrm{ob}\mathscr{C}$, $F: \mathscr{C} \to \mathrm{Set}$ is a functor, and $\mathsf{Nat}(\mathscr{C}(A, -), F)$ denotes all the natural transformations between functor $\mathscr{C}(A, -)$ and functor $F$. Then, there is a mapping from $\mathsf{Nat}(\mathscr{C}(A, -), F)$ to $F(A)$.*

**Definition 15.12.** $\mathscr{C}$ is a category of learning expressions, $F: \mathscr{C} \to \mathrm{Set}$ is a functor. If there is an object $A$ in $\mathscr{C}$ and a natural isomorphism $\phi: \mathscr{C}(A, -) \to F$, then we call ordered pair $(A, \phi)$ as a representation of $F$. If there is a representation of $F$, $F$ is a representable functor.

In Definition 15.12, a representation of $F$ can be considered as an ordered pair $(A, x)(A \in \mathrm{ob}\mathscr{C}$, $x \in F(A)$) (such that the natural transformation corresponding to $x$ is a natural isomorphism, i.e., for any object $B$ and each $y \in F(B)$, there exists a unique morphism $f: A \to B$ satisfy $F(f)(x) = y$). Thus, we can obtain an equivalent description of $F$ as follows:

For all the ordered pairs $(A, x)$ as objects and when morphism $f: (A, x) \to (B, y)$ is the morphism $f: A \to B$ such that $F(f)(x) = y$, it is obvious that this can constitute a category of learning expressions, and that a representation of $F$ is exactly an initial object in that category.

**Example 15.6.** *Oblivion functor $U: \mathrm{Gp} \to \mathrm{Set}$ from Lie group machine learning category $\mathrm{Gp}$ to the set category $\mathrm{Set}$ is a representable functor.*

*Proof.* *According to the definition of the functor, assume that functor $U$ exists. Then, each Lie group machine learning corresponds to the set, and each group homomorphism (continuous mapping, ring homomorphism, etc.) corresponds to this functor $U$.*
