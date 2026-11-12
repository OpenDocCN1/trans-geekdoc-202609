score between the incidence matrices of $B_t(G^{\circ})$ and $B_t(G)$, and the perturbation score between the incidence matrices of $B_h(G^{\circ})$ and $B_h(G)$.

![](bbox=[0.13, 0.15, 0.9, 0.29])

Fig. 3. Perturbation score as function of the steps on the Markov chain. In each case, the curves for NuDHY and DiNGHY-B perfectly overlap.

On the datasets satisfying Corollary 1, we use the same number of steps $s$ as Preti et al. [20] to take a single sample for each dataset (details in the supplementary materials), and we measure the perturbation score between $\hat{G}^{\circ}$ and the current state of the Markov Chain every $\frac{s}{100}$ steps, for a total of 100 measurements.

Figure3 shows the perturbation score as function of the number of steps. DiNGHY converges faster than DiNGHY-B and NuDHY, with the latter two showing identical behavior (overlapping curves). Thus, the different approach to choosing NDSs taken by DiNGHY is to be preferred, as it leads to faster mixing.

# 7 Conclusion

We introduce the first null models for edge-ordered and edge-unordered non-degenerate dihypergraphs, capturing important properties of the observed network. By preserving non-degeneracy, our models are more realistic than existing ones in many scenarios, and thus should be preferred for statistical hypothesis testing. Our MCMC algorithms sample from the null models according to any user-specified distribution, and converge quickly. Directions for future work include strengthening the sufficient conditions for irreducibility (Theorem 1 and Corollary 1), and developing more descriptive null models for dihypergraphs, and efficient algorithms to sample from them.

Acknowledgments. This work is supported in part by the National Science Foundation awards CAREER-2238693 and AF-2312241, and by the National Science Foundation Graduate Research Fellowship Program under Grant No. 2439559. Any opinions, findings, and conclusions or recommendations expressed in this material are those of the Authors and do not necessarily reflect the views of the National Science Foundation.

Disclosure of Interests. The authors have no competing interests to declare that are relevant to the content of this article.