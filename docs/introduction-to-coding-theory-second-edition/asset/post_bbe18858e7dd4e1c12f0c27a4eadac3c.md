
crucial point is to prove that the new algorithm has essentially the same behavior as the Monte Carlo algorithm considered earlier.

Here is the construction: choose a prime q satisfying n ≤ q ≤ 2n. Replace the probability p_i = 1/(2d_i) by the rational number p_i' = ⌊p_i·q⌋/q = n_i/q ≤ p_i. Use the Reed-Solomon code RS(2, q), which is an OA1(2, q, q) with q^2 rows. Eventually we omit some columns and obtain an OA1(2, q, q), which we call Ω. The rows of Ω are the elements of our probability space, with uniform distribution. The random variables f_i' are constructed as follows: choose N_i ⊆ F_q, |N_i| = n_i, put f_i'(x1,x2,...,xn) = 1 if x_i ∈ N_i, f_i' = 0 otherwise. Here (x1,x2,...,xn) ∈ Ω. Then f_i' has almost the same distribution as f_i. While the f_i are statistically independent, the f_i' are still **pairwise independent** (see Theorem 16.2). Just as in the preceding subsection, one has to study the behavior of the algorithm where the construction of I_k is determined by random choice of a row of Ω.

Here is the algorithm as proposed by Luby, which we want to call **RS-CHOICE**, as the stochastic element has been reduced to the choice of a word of the Reed-Solomon code. Let n = |V|, choose a prime q, n ≤ q ≤ 2n, and put p_i, p_i' as described above.

- If there is a vertex i such that d_i ≥ n/16, put I' = {i} (observe that this case can occur for at most 16 values of k).
- Assume d_i < n/16 for all i. Then p_i' ≥ 8/q. Moreover, the p_i' can be bounded by p_i in both directions; more precisely, 7/8 p_i ≤ p_i' ≤ p_i. Carry out the Monte Carlo algorithm, which differs from **MC-CHOICE** only in that the binary n-tuples are chosen from the rows of the Reed-Solomon code, with uniform distribution.

If the same analysis as before is carried out, qualitatively similar results to the case of **MC-CHOICE** are obtained. More precisely, one has

E(e_k − e_{k+1}) ≥ 1/18 · e_k.

In conclusion:

We considered algorithms for the maximal independent set problem in graphs. All the algorithms follow the general scheme described in the beginning. The decisive point is then the **CHOICE** algorithm, which is applied for each step to determine an independent set in the graph at hand. Two variants, **MC-CHOICE** and **RS-CHOICE**, have been considered. Both are parallel algorithms and use a stochastic element. The behavior of the global algorithm is very similar in both cases. The most important point here is the expected number of steps in the iteration, as a function of the number n of vertices of the graph. In both cases the expected number of steps in the iteration is O(n). The decisive difference is in the size of the underlying probability space. The original Monte Carlo algorithm **MC-CHOICE** uses

O(n) random bits (the size of the probability space is 2^n), whereas the algorithm **RS-CHOICE**, which is based on a two-dimensional Reed-Solomon code, uses only O(log(n)) random bits. It is even possible to construct a deterministic algorithm by testing all the rows of the Reed-Solomon code. The method of reducing the number of random bits by representing the random variables describing a Monte Carlo algorithm on a smaller probability space, while at the same time maintaining the essential features of the algorithm, is known as **derandomization**. **Complete derandomization** is obtained if the stochastic element is completely eliminated. In the case studied here we found that it suffices when the random variables are pairwise independent. This means that we can use an orthogonal array of strength 2 for the derandomization. This result had to be expected. The reason is that we were considering a graph problem. As a graph is a structure which is defined by a pairwise relation, it may be expected that pairwise independence is sufficient.

## The formalism of derandomization

The algorithms for the maximal independent set problem as discussed above indicate how and when derandomization may be expected to work in general. The point of departure is a randomized algorithm using a large number of statistically independent random variables.

- Assume the analysis of the algorithm shows that t-wise independence of the random variables suffices to guarantee the essential features, above all, the order of magnitude of the expected running time.

As the maximal independent set problem is a problem involving only edges of graphs, it is not surprising that pairwise independence is sufficient. However, the analysis leading to this conclusion is not short or trivial. The crucial step is to replace the two-valued random variables f_i (with probabilities p_i and 1 − p_i) by random variables f'_i (with probabilities p'_i and 1 − p'_i), which do not differ very much from f_i, are pairwise independent and represented on a small probability space. This is made more precise by the following definitions:

### 16.23 Definition.
Let f, f' be random variables with the same finite set Z of values. Then f, f' are ε close if, for every z ∈ Z, we have

|Pr(f = z) − Pr(f' = z)| ≤ ε.  (16.2)

In our example we replaced probabilities p_i by p'_i and made sure in the derandomized algorithm **RS-CHOICE** that we could assume ⁷⁄₈ p_i ≤ p'_i ≤ p_i. This shows that the corresponding random variables are ¹⁄₈ close.

### 16.24 Definition.
Let random variables f_i, i = 1,2,...,n be defined on finite probability spaces Ω_i. A representation of (f1,f2,...,fn) is a probability space Ω with random variables g1,...,gn defined on it such that the distribution of g_i is the same as the distribution of f_i, for every i. The representation is uniform if Ω has the uniform distribution, and it is t independent if any t of the g_i are statistically independent.

In the case of the maximal independent set problem, we used an orthogonal array of strength 2, more precisely, the two-dimensional Reed-Solomon code, to construct a two-independent uniform representation of (f'_1, f'_2, ..., f'_n) on the rows of the OA. In the light of our interpretation of an orthogonal array of strength t as a family of t-wise independent random variables (see Section 16.1), the following is trivial:

### 16.25 Proposition.
Let f_i, i = 1,2,...,n be random variables defined on finite sample spaces and let Ω be a finite sample space. Further, let v be a natural number such that p·v is an integer for every probability p occurring in the distribution of the f_i. If an OA_k(t,n,v) exists, then there exists a t-independent uniform representation of (f1,...,fn) on the rows of Ω.

We can now formulate the remaining conditions for the derandomization of a Monte Carlo algorithm. This still is vague because it remains open what the analysis which shows that t-wise independence suffices, looks like.

- Let f1,f2,...,fn be the independent random variables describing the Monte Carlo algorithm. Assume there are random variables f'_i such that f_i and f'_i are ε close for some 0 ≤ ε < 1 and such that (f'_1, f'_2, ..., f'_n) have a t-independent representation on some probability space Ω.

If these conditions are satisfied, then we can replace the stochastic choice of the original Monte Carlo algorithm by the choice of an element from Ω. As f'_i and f_i are ε close, it can probably be proved that the expected number of steps of the new algorithm will have the same order of magnitude as for the Monte Carlo algorithm. The value of ε should only affect the constants. Naturally we wish ε to be as small as possible. In our example we had ε = 1/8, and Ω consisted of the rows of the Reed-Solomon code, with uniform distribution. The effect of derandomization is then measured by the cardinality of Ω as compared with the cardinality of the direct product of the probability spaces on which the f_i were defined. If Ω is small enough, then a deterministic algorithm can be obtained by searching through all the elements of Ω and continuing with the element which gives the best result.

In Section 16.7 we will exploit another degree of liberty. This arises from weakening the notion of t-wise independence. The case t = 2 will be discussed in some detail. This idea will turn out to be very fruitful. It is possible to construct such arrays whose properties differ only slightly from 2-independence, but of a much smaller cardinality than orthogonal arrays of strength 2.
