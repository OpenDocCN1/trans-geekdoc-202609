# # Categorical Deep Learning

For every parametric map $(P, f) \in Para(C, Y)$ we have the strictly natural square in Equation (9). The 2-cell is given by the reparametrisation $\beta_{P,I}: P \otimes I \to I \otimes P$ with identity since we are assuming $\mathcal{M}$ is strict monoidal. It can be checked that indeed this satisfies the conditions of a 2-morphism in $Para_{\mathcal{M}}(C)$. This makes $Para_(\eta)$ a 2-natural transformation.

![](bbox=[0.365, 0.155, 0.905, 0.235])

+   * Multiplication Para_{(\mu): Para_{(\mu)}(T)^2 \to Para_{(\mu)}$ whose component at $X \in Para_{\mathcal{M}}(C)$ is the morphism $(I, m_X)$ where $m_X$ is the composite

![](bbox=[0.365, 0.295, 0.632, 0.315])

For every parametric morphism $(P, f) \in Para(C, Y)$ we have the strictly natural square in Equation (10). It is given by $\beta_{P,I}$ and is strict because $\mathcal{M}$ is strict monoidal. It can be checked that this satisfies the conditions of a 2-morphism in $Para_{\mathcal{M}}(C)$ This makes $Para_(\mu)$ a 2-natural transformation.

![](bbox=[0.365, 0.385, 0.905, 0.483])

Last, we need to check that $(\eta)$ and $Para_{(\mu)}$ satisfy the 2-natural coherence conditions. Since the components of components of $Para_{(\mu)}$ are trivial, this is straightforward to check.

Remark 6.9. For strictly monoidal $\mathcal{M}$ and strict category $(C, \bullet)$ the unit and comultiplication of $Para(T)$ are exactly the unit and multiplication of $T$.

The following shows us how the abstract of the 2-categorical framework of weight using (usage of the weight in two different places obtained by using the vertex) arises from the structure of a monoid induced by lax algebra of a strict monad on $C$.

**Theorem 6.10** (Lex) algebras for $Para(T)$ induce comoids, $T : C \to C$ a monad on $C$. Consider a lax algebra $(A, (P, \alpha, \epsilon_A, \delta_A)$ for the 2-monad $Para(T)$. Then $P$ is a comoid in $\mathcal{M}$ where $\epsilon_A$ is the data of count, and $\delta_A$ the data of comultiplication. The same statement holds for a lax algebra of $Para(T)$ comoid.

*Proof.* We start by unpacking the data of the lax algebra 2-cells.

![](bbox=[0.185, 0.738, 0.755, 0.803])

We can see that they are given by two parametrisations: $\epsilon_P: P \otimes I \to I$ and $\delta_P: I \otimes P \to P \otimes P$. These uniquely determine the morphisms $!_P : P \to I$ and $\Delta_P : P \to P \otimes P$ respectively. To show that this is a comoid, we need to unpack the lax laws which only on morphisms in $\mathcal{M}$. It is relatively tedious, straightforward to check that these conditions ensure $!_P$ and $\Delta_P$ satisfy the lax laws. $\square$

24