![](bbox=[0.05, 0.06, 0.95, 0.23])

**Fig. 17.4**: Different representations of the identity of groups.

![](bbox=[0.05, 0.3, 0.95, 0.46])

**Fig. 17.5**: Different representations of the inverse of groups.

ial algebra $K$, for functor $\mathbf{Fun}$, we know that the identity is equivalent to a given algebra homomorphism: $\varepsilon: A \to K$, called an $A$ augmented mapping or counit, satisfying the commutativity shown in Figure 17.4(b). This commutativity is called the counit law or augmented law of $\varepsilon$.

Each element of group $G$ has an inverse element. Obviously, this is equivalent to a given group of anti-isomorphic $i: G \to G$, satisfying the commutativity shown in Figure 17.5(a). In the figure, $d: G \to G \otimes G$ is 'the diagonal morphism', i.e., $d(x) = (x, x)$. It is easy to verify that $d^{*}: A \otimes A \to A$ is the multiplication of $A$: $\mu$. Moreover, $f$ is the only group homomorphism of $G$ to $E$, and $\kappa$ is the unique algebraic homomorphism of $K$ to $A$. Similarly, for the functor $\mathbf{Fun}$, we know that the existence of the inverse is equivalent to a homomorphism $\gamma: A \to A$, called the pole mapping, satisfying the commutativity shown in Figure 17.5(b). This commutativity is called the pole law or the inverse law:

If the algebra on group $G$ is called $A$, the dual algebraic structure is introduced:

+   (1) Comultiplication: $\Delta: A \to A \otimes A$ satisfying $\Delta(f) = \sum_{i} f_{1,i} \otimes f_{2,i}$. The use of Sweedler symbols can be abbreviated as $\Delta(f) = f_{(1)} \otimes f_{(2)}$;

+   (2) Residual associate law: $(\Delta \otimes \mathrm{id}) \circ \Delta = (\mathrm{id} \otimes \Delta) \circ \Delta$;

+   (3) Residual unit element: $\varepsilon(f_{1}f_{2}) = \varepsilon(f_{1})\varepsilon(f_{2})$;

+   (4) Residual inverse: $S: m \circ (S \otimes \mathrm{id}) \circ \Delta = 1_{A}\varepsilon = m \circ (\mathrm{id} \otimes S) \circ \Delta$.