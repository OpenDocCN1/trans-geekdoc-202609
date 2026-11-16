# Figure 2. path representation

![](bbox=[0.28, 0.14, 0.72, 0.26])

# Crossover Operators

Several ways to do the crossing in tsp optimization context are described in the literature: Partially Mapped Crossover (**PMX**)(David Edward Goldberg, 1989), Order Crossover (**OX**) proposed by(L. Davis, 1985) which produces offspring that preserves the cities relative order of parents, Edge Crossover (**EX**) (L. D. Whitley, Starkweather, & Fuquay, 1989), Subtour Exchange Crossover (**SXX**) (Yamamura, Ono, & Kobayashi, 1992), Edge Exchange Crossover (**EXX**) (Murata & Itai, 2008), Edge Assembly Crossover (**EAX**) (J. Watson et al., 1998).

# Various Others Crossover Operators and Their Variations

the Modified crossover(L. Davis, 1985),this crossover operator is an extension of the one-point crossover for permutation problems.The Order-based crossover (**OBX**) which focuses on the relative order of the cities on the parent chromosomes, used by G. Syswerda in (L. D. Davis, 1991); Alternate Edges Crossover (**AEC**) is reported in (Grefenstette, Gopal, Rosmaita, & Van Gucht, 1985), the results with this operator have been uniformly discouraging. However, it was a good introduction to the other edge-preserving operators.(Deep & Mehrahtu, 2011) proposed three new additional variations of order crossover and their performance were far better than the existing variations. The variations are designed using cut point analysis on the standard ordered crossover operator. Freisleben and Merz(Freisleben & Merz, 1996) and (Merz & Freisleben, 1997) suggested the distance-preserving crossover (DPX) for TSP.

+   - **More Specific Crossover for Ordered Problems**
+       - **Position-Based Crossover Ppperator (POS)** (Goel & Wadhwa, 2013)
+       - **Voting Recombination Crossover Operator (VR)** (Muhlenbein, 1989)