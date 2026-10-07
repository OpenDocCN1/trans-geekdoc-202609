
# Categorical Deep Learning

- * $f \otimes (g \otimes h) = (f \otimes g) \otimes h$ for all $f, g, h \in \mathcal{M}$;
- $id \otimes f = f \otimes id$ for all $f \in \mathcal{M}$.

**E.2** (Agories, see Capucci & Gavranović, 2023), Let $(\mathcal{M}, \otimes, I, \alpha, \lambda, \rho)$ be a monoidal category. An $\mathcal{M}$-category $C$ is a category $C$ with a functor $\blacktriangleright: \mathcal{M} \times C \to C$ together with natural isomorphisms $\eta_X : I \blacktriangleright X \cong X$ and $\mu_{M,N} : (M \otimes N) \blacktriangleright X \to M \blacktriangleright (N \blacktriangleright X)$, such that:

For all $M, N, P \in \mathcal{M}$ and $C$ the following diagram commutes:

![](img/92dd63b8e10fefd3f3f227bf65a30b83_18_0.png)

**Left and right units.** For all $C$ and $M \in \mathcal{M}$ The diagrams below commute.

![](img/92dd63b8e10fefd3f3f227bf65a30b83_18_1.png)

*Remark* E.3. As one may assume a monoidal category to be strict, by MacLane’s coherence theorem, we may assume categories are strict also (Capucci & Gavranović, 2023, Remark 3.4). This is to say, we may assume for any $\mathcal{M}$-category

- * The unit $\eta_X$ is an equality, it that $I \blacktriangleright X = id_C$ as functors of type $C \to C$; and

We will call such a **strict** category. We will use these to simplify exposition and some theorems.

**Example 4** (Monoidal action). Any monoidal category gives rise to a self-action.

**Example 5** (Famlies categories). Any category $C$ with copies has an action $\blacktriangleright: Set \times C \to C$ which maps $(X$

# E.1. Morphisms of Categories

**Definition 6** (Acrylic strong mon). Let $(\mathcal{C}, \blacktriangleright)$ be a $\mathcal{M}$-category. An $(T, \mu, \eta)$ on $C$ is **strong** if it is equipped with a natural transformation $\sigma_{P,A} : P(A) \to T(P(A))$, a strength such that diagrams in Definition E.9 commit.

**Example 7.** All forms of the type $A \blacktriangleright : Set \to Set$ are strong for the category (Set, $\times$), for any monoid $A$. This includes $G \blacktriangleright : Set \to Set$ from Example 2.2,$^{11}$

**Definition 8** (Acrylic endofun). Let $(\mathcal{C}, \blacktriangleright)$ be an $\mathcal{M}$-category. An endofun $F$ on $C$ is **strong** if it is equipped with a natural transformation $\sigma_{P,A} : F(A) \to F(P(A))$, a strength such that diagrams AS1 and AS2 in In Definition E.9 commit.

$^{10}$Another name for this is a $\mathcal{M}$-linear morphism, in (Capucci & Gavranović, 2023)

$^{11}$The strength is in fact a natural isomorphism.

**Definition E.9** (Actorical strong monad coherence diagrams). A monad $(T, \mu, \eta)$ on the category $C$ of a $\mathcal{M}$-category $(\mathcal{C}, \blacktriangleright)$ is called **strong** if it is equipped with a natural transformation $\sigma_{P,A} : P \otimes T(A) \to T(P \otimes A)$, making the following diagrams below commute:

**AS1**: Compatibility of strength and the monoidal unit.

**AS2**: Compatibility of strength and allegory multiplier.

![](img/92dd63b8e10fefd3f3f227bf65a30b83_19_0.png)

![](img/92dd63b8e10fefd3f3f227bf65a30b83_19_1.png)

**AS3**: Compt. of strength and monad multiplication.

![](img/92dd63b8e10fefd3f3f227bf65a30b83_19_2.png)

![](img/92dd63b8e10fefd3f3f227bf65a30b83_19_3.png)

**Example E.10**. the endofunctors from Examples 2.9 to 2.11, H4 and H7 are strong endofunctors, and their appropriate monads are strong. See Appendix (Example E.11).

**Example E.11**. We present a list of the strengths $\sigma_{P,X}$ of some relevant endofunctors (on the left) and their free monads (on the right)

Given the endofunctor $1 + A : Set$, its strength $\sigma_{P,X} : P \times (1 + A) \to 1 + A \times X$ is given by:
$\sigma_{P,X}(p,inl) = inl(p)$
$\sigma_{P,X}(p,inl) = inl(p,x)$

Given the endofunctor $A + (-)^2$, its strength $\sigma_{P,X} : P \times (A + (-)^2) \to A + (P \times X)^2$ is given by:
$\sigma_{P,X}(p,inl) = inl(p)$
$\sigma_{P,X}(p,pair(x,x')) = pair((p,x), (p,x'))$

Given the free monad $List_{+1}(A) : Set \to Set$, its strength $\sigma_{P,Z} : P \times List_{+1}(A) \to List_{P \times Z}(A)$ is given by:
$\sigma_{P,Z}(p, Nil) = Nil$
$\sigma_{P,Z}(p, z) = (p,z)$
$\sigma_{P,Z}(p,cons(a,as)) = cons(a, \sigma_{P,Z}(p,as))$

Given the free monad $Tree(A +-) : Set$, its strength $\sigma_{P,Z} : P \times Tree(A + Z) \to Tree(A + P \times Z)$ is given by:
$\sigma_{P,Z}(p,Leaf(a)) = Leaf(p,a)$
$\sigma_{P,Z}(p,inl(z)) = Leaf(p,z)$
$\sigma_{P,Z}(p,Node(l,r)) = Node(\sigma_{P,Z}(l), \sigma_{P,Z}(r))$

# F. Categorical Algebra

Good references for categorical algebra are (Lack, 2010) or Kelly, 2005). The latter deals with the more general notion of enriched categories of which 2-categories are a particular example.

# F.1. monads and their Lax Algebras

A 2-monad can be concisely defined as a Cat-monad (see Johnson et al., Sec. 6.5) An unpacking of its definition follows.

**Definition F.1** (2-monad). A 2-monad on $2-\mathcal{C}$ comprises:

- A 2-endofunctor $T$ on $C$;
- A 2-natural transformation $\mu : T^2 \Rightarrow T$;
- A 2-natural transformation $\eta : \text{id}_C \Rightarrow T$;

such that the (C-enriched variant) of the axioms in Definition B.1 holds. A Lax T-algebra $(A, a, \epsilon_A, \delta_A)$ where $(T, \eta, \mu)$ is a 2-monad on $C$, and $\epsilon_A$ and $\delta_A$ are the following 2-morphisms in $C$:

A object of $C$, $a : T(A) \to A$ is a morphism in $C$,

![](img/92dd63b8e10fefd3f3f227bf65a30b83_20_0.png)

that the unity and lax associativity conditions (Johnson et al., 2026, 6.5.6 and 6.5.7) are satisfied.

**Definition F.3** (Lax algebra homomorphism). Let $\mathcal{E}$ be a 2-category, $T$ a 2-monad on $\mathcal{E}$, and $(A, a, \epsilon_A, \delta_A)$ and $(B, b, \epsilon_B, \delta_B)$ be lax T-algebras. Then a alex homomorphism from $(A, a, \epsilon_A, \delta_A) \to (B, b, \epsilon_B, \delta_B)$ is a pair $(f, \kappa)$ where $f : A \to B$ is a morphism in $\mathcal{E}$ and $\kappa$ is a 2-morphism spanning by the following

![](img/92dd63b8e10fefd3f3f227bf65a30b83_20_1.png)

such that the diagrams (in Johnson et al., Def. 6.5.9) commute.

Lax algebras and lax algebra homomorphisms for the 2-monad $T$ form the category Lax-AlgMnd(T).

**Example F.4** (for M-modules). If $M$ is a monad, it is possible to study "M-modules", which we define as monoids equipped with a compatible action of $M^{12}$ terms of the 2-monad $\delta_\epsilon(M) \times -$ on the 2-category.

Here $\delta_\epsilon(M)$ is the category whose objects are elements of $M$, and morphisms are the identities. Since $M$ is a monad, $\delta_\epsilon(M)$ is a monadic category, so $\delta_\epsilon(M) \times -$ is a monad.

As the set of endomorphisms on a monad $A$ is isomorphic to the set of endofunctors on the category given the deloping of the monad, an M-module can be seen as a one-object algebra for this 2-monad. Indeed, this is a special case of any algebra.

**Example F.5** (Cocyles as lax monoids). The monoidal cycles, or "crossed monoids", used in (Dudzik et al., 2024) to study synchrony in networks, can be described as lax monoids for 2-monad algebras. As if $A$ is an M-module, $BA$ is an algebra for $\delta_\epsilon(M) \times -$.

G. The 2-category Para(C)

**Definition G.1** (para, Currutt et al., 2022; Capucci et al., 2022). Given a monoidal category $(\mathcal{M}, \otimes)$ and an M-category $\mathcal{C}$, let Para$(\mathcal{C})$ be the 2-category:

- Objects of the category;
- Morphisms $X \to Y$ are pairs $(P, f)$, where $P$ is an object of $M$ and $f : P \blacktriangleright X \to Y$ is a morphism of $C$.

> 12Contrary to a M-action A, where A is a set, in a M-module A comes equipped with a monoidal structure too.
