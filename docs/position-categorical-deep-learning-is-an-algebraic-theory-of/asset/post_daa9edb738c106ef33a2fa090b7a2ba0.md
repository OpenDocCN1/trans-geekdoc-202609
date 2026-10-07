
## Categorical Deep Learning

**Definition 1.1** (Category). A category $C$, consists of a collection of objects, and a collection of morphisms between objects, such that:

Just as an interaction between categories, a natural transformation between functors; this is the first and final concept we cover.

- For each object $A \in C$, there is a unique identity $id_A: A \to A$.

**Definition 1.5** (Natural transformation). Let $F: C \to D$ and $G: C \to D$ be two functors between $C$ and $D$, a natural transformation $\alpha: F \to G$ of choice, for every object $X \in C$, is of a morphism $\alpha_X: F(X) \to G(X)$ in $D$ such that for every morphism $f: X \to Y$ in $C$, it holds that $\alpha_Y \circ F(f) = G(f) \circ \alpha_X$.

- For any two morphisms $f: A \to B$ and $g: B \to C$, there must exist a unique morphism whose composition $g \circ f: A \to C$.

The morphism $\alpha_X$ is called the component of the natural transformation at the object $X$, such to the following conditions:

- For any morphism $f: A \to B$, it holds that $id_B \circ f = f \circ id_A$.

- For three composable morphisms $f: A \to B, g: B \to C, h: C \to D$, composition is associative, i.e., $h \circ (g \circ f) = (h \circ g) \circ f$.

The components of a natural transformation assemble into 'natural squares'; commutative diagrams:

![](img/92dd63b8e10fefd3f3f227bf65a30b83_2_0.png)

We denote by $(C, AB)$ the collection of all morphisms from $A$ to $B$ in $C$, where a diagram commutes, if for any objects, two paths connecting to the same morphism.

We provide a typical example:

**Example 1.2** (The Set Category). Set is a category whose objects are sets, and functions are between them.

## 2. From Monad to Algebras

And another example, for geometric DL:

**Example 1.3** (Monads as categories). A group $G$, can be represented as a category, with a single object $G$, and morphisms $g: G \to G$ corresponding to elements. Note that $G$ is a group if the binary operation is isomorphic. Note that $G$ is a group if and only if its morphisms are isomorphisms, for each $g: G \to G$ there exists $h: G \to G$ such that $g \circ h = h \circ g = id$. More, we can identify one-object categories, which are not necessarily invertible, with monads.

Having the essential concepts, we want to discuss a categorical framework which generalizes geometric deep learning (Bronstein, 2021). We will define a powerful notion (monad algebra homomorphism) and demonstrate the specific case of monads induced by group actions. Generalising from monads and their algebras we will find that our theory can express processes structured data from computer science (e.g. lists and trees) and behave in set ways like automata.

The power of theory starts to emerge when we interact different categories. Just as functors of sets and morphisms of groups, there is a more generic concept of structure preserving between categories.

**Definition 1.4** (Functor). Let $C$ and $D$ be two categories. $F: C \to D$ is a functor between them, if it maps each object and morphism of $C$ to one in $D$, and the following conditions hold:

- For any object $A \in C$, $F(id_A) = id_{D(A)}$.

- For any composable morphisms $f, g$ in $C$, $F(g \circ f) = F(g) \circ F(f)$.

> ¹The term 'collection', rather than set, avoids Russell's paradox, as objects may be viewed as sets. Categories that can be defined with sets as small categories.

**Definition 2.1** (Monad). Let $C$ be a category. A monad on $C$ is a triple $(M, \eta, \mu)$ where $M: C \to C$ is an endofunctor, and $\eta: C \to M$ and $\mu: M \circ M \to M$ are natural transformations (where $\mu$ is function composition), making diagrams in Definition 1. commute.

**Example 2.2** (Group action monad). Let $G$ be a group. The functor $G \times - \text{Set} \to \text{Set}$ is an endofunctor mapping a set $X$ to the set $G \times X$.

> ²To the best of our knowledge, these ideas were first conjectured in Olah (2015) in the language of functional programming.

## Categorical Deep Learning

**Example 2.6 (Equivariant maps).** Equivariant maps are group action algebra homomorphisms. Consider any action from Example 2.4. An endomorphism of such action—that is, a $G$-algebra over $\mathbb{R}^{z \times x}$—an endomorphism which induces a commutative diagram:

```
$G \times \mathbb{R}^{z \times z_h} \xrightarrow{Gf} G \times \mathbb{R}^{z_h \times x}$
$\mathbb{R}^{z \times z_h}$
```

- $id_B: G \times X \to \text{Set}$ whose component at $X$ is the function $x \mapsto e$.
- $\mu: G \times X \to \text{Set}$ whose component at $X$ is the function $x \mapsto gx$.

**Definition 2.3 (Algebra for a monad).** An algebra for a monad $(M, \eta, \mu)$ on $C$ is a pair $(A, a)$ where $A \in C$ is an object and $a: M(A) \to A$ is a morphism satisfying the following diagram:

![](img/92dd63b8e10fefd3f3f227bf65a30b83_3_1.png)

**Example 2.4 (Group actions).** Let $G$ be a group and $X$ a set. A group action of $G$ on $X$ is a function $\rho: G \times X \to X$ such that $\rho(e, x) = x$ and $\rho(g, \rho(h, x)) = \rho(gh, x)$.

**Example 2.5 (Equivariant maps).** Let $G$ be a group and $X, Y$ be $G$-sets. A function $f: X \to Y$ is $G$-equivariant if for every $g \in G$ and $x \in X$, $f(g \cdot x) = g \cdot f(x)$.

