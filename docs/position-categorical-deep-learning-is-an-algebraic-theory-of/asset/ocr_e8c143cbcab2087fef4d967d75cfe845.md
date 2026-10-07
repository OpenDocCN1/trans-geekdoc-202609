# Categorical Deep Learning

**Example L4** (Mealy cell / Full RNN). Consider the inductor $I ightarrow O$ – Example 2.11. Via strength from Example E.10 we can the 2-endofunctor $Para(I ightarrow O) : Para(Set) ightarrow Para(Set)$. Then a Mealy cell arises as the coalgebra.

More concretely, a coalgebra consists of the carrier set $S$ and a parametric map $(P, cell^{	ext{Mealy}}) \in Para(Set), (S, I ightarrow S)$. Here $cell^{	ext{Mealy}}$ can be thought of as a map $P 	imes S ightarrow I ightarrow O 	imes S$, as shown in the figure below. We interpret it as a recurrent

![](bbox=[0.238, 0.195, 0.762, 0.258])

Figure 8. An example for $Para((I ightarrow O))$ 2-endofunctor of an object $S$ and a map $f: P 	imes S ightarrow I$ which we have taken liberty to unify.

neural network consuming a hidden state $S$, and output $O$ and an updated input $O$ and updated hidden state.

This suggests that neural networks can be thought of as Mealy machines, a perspective seldom advocated in the literature.

**Example L5** (Mealy machine). Consider the inductor $O ightarrow (I ightarrow -)$ from Example H.7. With $\sigma_{p,X}: P 	imes O 	imes (I ightarrow O) ightarrow Para(O 	imes (I ightarrow -))$, we get the 2-endofunctor $Para(O 	imes (I ightarrow -)) : Para(Set) ightarrow Para(Set)$. Then a Mealy cell arises as its coalgebra.

More concretely, a coalgebra consists of the carrier set $S$ and a parametric map $(P, cell^{	ext{More}}) \in Para(Set), (S, O 	imes (I ightarrow S))$. Here $cell^{	ext{More}}$ can be thought of as a map $P 	imes S ightarrow O 	imes (I ightarrow S)$, as shown in the figure below. We break it down into two pieces $cell^{	ext{More}}: P 	imes S ightarrow O$ and $cell^{	ext{More}}: P 	imes S ightarrow I$.

![](bbox=[0.238, 0.513, 0.762, 0.597])

Figure 9. An example for $Para(O 	imes (I ightarrow -))$ as a parametric model. Here the output does not depend on the current input.

# Unrolling Neural Networks via Transfinite Construction

We will reap the benefits of the transfinite construction of free monads on endofunctors, and the corresponding unrolling of these networks. Specifically, with Theorem G.10 heading towards the path of having weight arising out of the categorical framework, we can perform the unrolling of these networks. For the purposes of space and clarity, the unaking is done as length homomorphism of algebras for endofunctors of 2-monads.

**Example J.1** (Iterated Folding RNNs). Consider an algebra $(P, cell^{	ext{fold}})$ of $Para(1+A 	imes -)$, a folding RNN cell (Example I.1). Its unrolling is a $Para(1+A 	imes -)$ where $\Delta p: P ightarrow P 	imes P$ is the copy map.

```
$$1+A \times List(A) \xrightarrow{\Delta p} 1+A \times X\n\gamma(Nil, Cell) \Downarrow (P, cell^{	ext{fold}})\nList(A) \xrightarrow{f_{rent}} X\n\quad \quad \quad (17)$
```

Here the map $f_{rent}$ is the parametric analogue of a *fold* (Example 2.12):