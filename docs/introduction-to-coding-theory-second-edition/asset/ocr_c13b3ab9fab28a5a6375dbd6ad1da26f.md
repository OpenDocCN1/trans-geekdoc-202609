18.1.4. Construct q-linear q^b-ary codes of length q^a + 1, strength 2 and dimension (a + b)/b for every b ≤ a.

18.1.5. Let D_q(a,b) (where a ≥ b) be the q-linear q^b-ary code of dimension a/b and length q^a constructed in this section. Determine its strength and minimum distance.

18.1.6. Let a ≥ b and l = ⌊a/b⌋ − 1. Show that

$$\sum_{i=0}^{l} q^{a-ib} = (q^{a+b} - q^{a-lb})/(q^{b} - 1).$$

18.1.7. Determine the parameters of the OA resulting from the Bose-Bush construction when 2b ≤ a < 3b. Give at least two examples.

18.1.8. Determine the parameters of the codes in Theorem 18.9 for parameters m = 1, r' = 2 and show that they are d-optimal for q ≤ 4.

18.1.9. Construct linear codes [70,9,32]_2 and [196,9,96]_2.

# 18.2 The cyclic theory of additive codes

We developed the theory of linear cyclic codes in earlier chapters. Here we extend the theory to the category of additive codes. Formally, this is self-contained: the earlier linear theory is proved once again in the present chapter. It is instructive that this does not take much space or time. Some of the basic facts from those earlier chapters are used (subfield code, trace code, Galois closure, the Delsarte theorem and of course cyclotomic cosets). In this section we follow [20].

Start from Definition 18.1. We will develop the general theory of additive codes which are cyclic in the monomial sense under the general assumption that the characteristic p of the underlying field is coprime to the length n of the code. The main effect of the assumption is that the action of a (cyclic) group of order n on a vector space over a field of characteristic p is completely reducible, by Maschke's theorem (see Definition 18.14 and Theorem 18.15).

# 18.2.1 Code equivalence and cyclicity

Recall the notion of permutation equivalence from Section 12.4.

# 18.10 Definition.

Codes C and D are permutation equivalent if there is a permutation π on n objects such that

$$(x_1,x_2,...,x_n) \in \mathcal{C} \iff (x_{\pi(1)},x_{\pi(2)},...,x_{\pi(n)}) \in \mathcal{D}$$

for all x = (x_1,...,x_n) \in \mathcal{C}.