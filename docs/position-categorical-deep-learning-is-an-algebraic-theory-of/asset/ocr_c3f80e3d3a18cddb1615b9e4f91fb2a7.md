# Categorical Deep Learning

**Example G.3** (Real Vector Spaces and Smooth Maps). Consider the cartesian Smooth whose objects are real vector spaces, and morphisms are smooth functions. When is cartesian, we can form Para(Smooth) modelling parametric smooth functions.

**Lemma G.4** (Embedding of $\mathcal{C}$ into $	ext{Para}(\mathcal{C})$). There is a 2-functor $\gamma : \mathcal{C} ightarrow 	ext{Para}(\mathcal{C})$ which is identity-on-objects and treats every morphism $f : A ightarrow B$ as trivially parametric, i.e. $f : A 	riangleright \gamma(f) \^{13}$

*Remark G.5.* When the category $(\mathcal{C}, 	riangleright)$ is strictly trivial the parametric functions do not require precomposition with the unit of actegory. That is to say that a morphism $f : X ightarrow Y$ of $\mathcal{C}$ is strictly the parametric morphism $(I, f) : X ightarrow Y$.

**Theorem G.6** (preserved colimits). Suppose $(\mathcal{M}, \eta, \mu)$ is a monoidal category, that $(\mathcal{C}, 	riangleright)$ is an $\mathcal{M}$-category, and that $X 	riangleright (\cdot) : \mathcal{C}$ preserves connected colimits.

*Remark G.7.* While in $\mathcal{C}$ there are only kind of colimits, the colimits we mean in Para$(\mathcal{C})$ are strict. The relationship to other flavours of colimit is a topic of ongoing research.

*Proof.* Note that for a colimit over a trivially parametrised category to commute, the 1-cells of the colimit must be the same. Then, we may the following chain of isomorphisms:

```
$$\text{Tr}_1\((	ext{Para }(\mathcal{C}))\) \left(\lim_{d\in\mathcal{D}} X_d, Y\right) \nsimeq \lim_{P\in\mathcal{M}} \mathcal{C} \left(\lim_{d\in\mathcal{D}} P \triangleright X_d, Y\right) \nsimeq \lim_{P\in\mathcal{M}} \mathcal{C} \left(\lim_{d\in\mathcal{D}} P \triangleright X_d, Y\right) \nsimeq \lim_{P\in\mathcal{M}} \lim_{d\in\mathcal{C}} (P \triangleright X_d, Y) \nsimeq \text{Ob}(\mathcal{M}) \times \lim_{d\in\mathcal{D}} (	ext{Ob}(\mathcal{M}) \times (\mathcal{C} \times (P \triangleright X_d, Y))) \nsimeq \lim_{d\in\mathcal{D}} \left(\prod_{P\in\mathcal{M}} \mathcal{C} (P \triangleright X_d, Y)\right) \nsimeq \lim_{d\in\mathcal{D}} \text{Tr}_1\((	ext{Para }(\mathcal{C}))\) (X_d, Y)\right)$
```

**Example G.8.** Fix $\mathcal{M}$-category $(\mathcal{C}, 	riangleright)$, and a monad $(T, \mu, \eta)$ on $\mathcal{C}$ with acteoretic strength $\sigma : \mathcal{M} 	riangleright T(X) ightarrow T(M) 	riangleright \mathbf{X}$. This gives us a monad of $	ext{Para}_{}_{}(	riangleright)$ on $	ext{Para}_{}(\mathcal{C})$ whose underlying endofunctor:

+   - Acts as $T$ as does on objects$^{14}$;
- Sends $(P, f) : X ightarrow Y$ to $(P, f')$, where $f'$ is the composite

```
$P 	riangleright T(X) \xrightarrow{\sigma_{P,X}} T(P 	riangleright X) \xrightarrow{T(f)} T(Y)$
```

and the unit 2-natural transformations are defined as follows:

+   - Unit Para,$(\eta) : \text{id}_{	ext{Para}_{}(\mathcal{C})} \Rightarrow \text{Para}_{}(	riangleright)$ T component at $X : \mathcal{C}$ is the element of $\text{Para}_{}(\mathcal{C})(X, T(X))$ given by the parametric morphism $(I, u_X)$, where $u_X$ is the composite

```
$$\mathbf{I} \triangleright X^{\gamma_X^{-1}} X \triangleright T(X)$
```

> $13}$Here we are treating $\mathcal{C}$ as 2-category with only identity 2-morphisms.
$^{14}$This is well defined since $\text{Ob}(\text{Para}(\mathcal{C})) = \text{Ob}(\mathcal{C})$

23