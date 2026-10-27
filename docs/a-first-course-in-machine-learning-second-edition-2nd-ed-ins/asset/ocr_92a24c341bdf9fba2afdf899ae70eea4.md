The predictive density is therefore (where summations will not include the data point in question):

$p(x_n^m \mid z_{nv}^m = 1, w_v^m = 1) = \mathcal{N}(a, b^2 + \sigma^2) = L(x_n^m \mid k)$

Note that the expression for a brand new top-level component is identical but all the summations will equate to zero.

The probability of placing the object in component $v$ is therefore proportional to:

$P(z_{nv}^m = 1 \mid w_{vk}^m = 1, \ldots) \propto L(x_n^m \mid k) \left(\sum_n z_n^m\right)$

To compute the probability of placing the point in a new component in file $m$ we have to marginalise over the top level components (admitting the possibility of a new one). Let $s_k$ be the number of components across all files that are assigned to top-level component $k$:

$P(z_{nv}^m = 1 \mid \ldots) \propto \gamma_m \left(\frac{\alpha L(x_n^m \mid k^*) + \sum_l s_l L(x_n^m \mid l)}{\alpha + \sum_j s_j}\right)$

We can therefore use these two probabilities to decide if the $n$th object ought to go into one of the current components in the $m$th file, or a new component. If we choose a new component, we then need to choose which top-level component it ought to be associated with (or a new one). The probability of it being a current one is proportional to $s_l L(x_n^m \mid l)$ and the probability of a new one is proportional to $\alpha L(x_n^m \mid k^*)$.

This completes the sampler, although it might not be particularly efficient. To improve its efficiency, one could re-sample the $w_{vk}^m$ for each file-level component. It is fairly straightforward to compute the required distribution but, be careful: if, as in this case, the mean parameters have all been marginalised, the joint density of all of the objects assigned to this component cannot be assumed to be independent in the standard way (they are all dependent via the marginalisation of the mean parameters). This can be overcome by, for example, computing $p(x_1, x_2, x_3, \ldots \mid \ldots) = p(x_1 \mid \ldots)p(x_2 \mid x_1, \ldots)p(x_3 \mid x_1, x_2, \ldots)$ etc.

**EX 10.11.** The equation we are trying to obtain is the probability that the $i$th word in the $n$th document comes from topic $k$. This will be the product of two components: the probability of the $k$th topic in document $n$ multiplied by the probability of word $w$ (assuming that the $i$th word is word $w$) in topic $k$. Based on the definitions in the text, in the un-collapsed world, this would be given by:

$P(z_{ni} = k \mid x_{ni} = w, \beta_{kw}, \theta_{nk}) = \theta_{nk}\beta_{kw}$.

To obtain the collapsed version, we need to marginalise the parameters $\theta_n$ and $\beta_k$. Both are multinomials and have Dirichlet priors with parameters $\alpha$ and $\gamma$ respectively. We know from our work in mixture models that if we have one sample from a multinomial (say the $k$th value has been sampled) whose parameters are Dirichlet distributed, the probability of that sample is equal to the $k$th Dirichlet