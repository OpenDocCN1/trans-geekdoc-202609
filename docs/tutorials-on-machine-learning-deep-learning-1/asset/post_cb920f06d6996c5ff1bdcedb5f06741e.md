
Algorithm 2. k-step parallel tempering with M temperatures
**Input:** RBM $(V_1,\dots,V_n,H_1,\dots,H_n)$, training batch $S$, current state $v$ of Markov chain with stationary distribution $p_r$ for $r=1,\dots,M$
**Output:** gradient approximation $\Delta v_i$, $\Delta b_j$, $\Delta c_i$ for $i=1,\dots,n, j=1,\dots,n$
1 init $\Delta v_i = \Delta b_j = \Delta c_i = 0$ for $i=1,\dots,n, j=1,\dots,n$
2 for each $v \in S$ do
   for $r=1,\dots,M$ do
     $v^{(0)} \leftarrow v$
     for $i=1,\dots,n$ sample $h_{i}^{(r)} \sim p(h_i|v^{(0)})$
     for $t=0,\dots,k$ do
       for $j=1,\dots,n$ sample $v_{r,j}^{(t+1)} \sim p(v_j|h_r^{(t)})$
       for $i=1,\dots,n$ sample $h_{r,i}^{(t+1)} \sim p(h_i|v_r^{(t+1)})$
   3 for $r \in \{2 \leq s \leq M \text{ and } s \pmod 2 \neq 0\}$ do
     swap $(v_{r}^{(k)})$ and $(v_{s}^{(k)})$ with probability given by (40)
   4 for $r \in \{3 \leq s \leq M \text{ and } s \pmod 2 \neq 1\}$ do
     swap $(v_{r}^{(k)})$ and $(v_{s}^{(k)})$ with probability given by (40)
   5 for $i=1,\dots,n, j=1,\dots,n$ do
     $\Delta w_{ij} \leftarrow \Delta w_{ij} + v_j^{(k)} - p(H_i=1)p(H_i=1|v_{j}^{(k)})$
     $\Delta b_j \leftarrow \Delta b_j + v_j^{(k)} - v_{j}^{(k)}$
     $\Delta c_i \leftarrow \Delta c_i + p(H_i=1) - p(1|v_{i}^{(k)})$

In each step of the algorithm, we run $k$ (usually $k=1$) sampling steps in each tempered chain yielding samples $(v_1, h_1), \dots, (v_M, h_M)$. After this, two neighboring chains with temperatures $T_r$ and $T_{r-1}$ may exchange particles $(v_r, h_r)$ and $(v_{r-1}, h_{r-1})$ with an exchange probability based on the Metropolis ratio,
$$\min \left\{1, \frac{p_r(v_{r-1}, h_{r-1})p_{r-1}(v_r, h_r)}{p_r(v_r, h_r)p_{r-1}(h_{r-1})}\right\}$$ (39)
which gives for RBM
$$\min \left\{1, \exp \left(-\frac{T_r}{T_{r-1}} (E(v_r, h_r) - E(v_{r-1}, h_{r-1}))\right)\right\}$$ (40)

After performing these swaps between chains, which enlarge the mixing rate, we take the next (eventually exchanged) sample $v_1$ of original chain (with temperature $T_1=1$) as a sample from the model distribution. This procedure is repeated $L$ times yielding samples $v_{1,1}, \dots, v_{1,L}$ used for the approximation of the expectation under the RBM distribution in the log-likelihood gradient (i.e., for the second term in (9)). Usually $L$ is set to the number of samples in the (mini) batch of training data as shown in algorithm 2.

Compared to CD, PT introduces computational overhead, but results in a faster mixing Markov chain and thus a less biased gradient approximation. The evolution of the log-likelihood training using PT with different values of $M$ can be seen in figure 2.

## 6 RBMs with Real-Valued Variables

So far we considered only observations represented by binary vectors, but one would like to model distributions over continuous data. There are several ways to define RBMs with real-valued variables. As demonstrated by [18], one can model a continuous distribution with a binary RBM by a simple "trick"—the input data is scaled to the interval $[0,1]$ and modeled by a probability of the visible variables to define. That is, instead of sampling binary values, the expectation $p(V_j=h)$ is regarded as the current state of the variable $V_j$. Except for the continuous value of the visible variables and the resulting changes, the sampling procedure learning remains the same. By keeping the energy function as given in (20) and just replacing the state $[0,1]^m$ of $V$ by $\mathbb{R}^m$, the conditional distributions of the visible variables belong to truncated exponential distributions. This can be shown in the way as the sigmoid function for binary RBMs is derived in (27). Visible neurons with a gaussian distribution can represent simple value gained by augmenting the energy with quadratic terms $d_j^2$ weighted by parameters $d_j, j=1,\dots,m$.

In contrast to the universal approximation capabilities of standard RBMs on real-valued units is rather constrained [38].

More generally, it is possible to cover continuous variables by extending the definition of an RBM to any RRF where the energy function is such that $p(h)=\prod p(h|v)$ and $p(v)=\prod p(v|h)$. As follows directly from the Hammersley-Clifford theorem and as discussed in [18], this holds for any energy function of form
$$E(v,h) = \sum_{i,j} \phi_{ij}(h_i, v_j) + \sum_{j} \psi_j(v_j) + \sum_{i} \nu_i(h_i)$$
with real-valued functions $\phi_{ij}$, $\psi_j$, $i=1,\dots,n$, and $j=1,\dots,m$, filling the constraint that the partition function $Z$ is finite. Well et al. come to almost the same generalized form of the energy function from arbitrary marginal distributions $p(v_j)$ and $p(h_i)$.

## 7 Loosening the Restrictions

In this closing section, we will give a very brief outlook on selected extensions RBMs that loosen the imposed restrictions on the bipartite topology by introducing dependencies on further random variables or allowing for arbitrary connections between nodes.

- **Conditional RBMs.** Several generalizations and extensions of RBMs exist. Notable examples are conditional RBMs (e.g., [35,29]). In these models, some of the parameters in RBM are replaced by functions of conditioning variables; see.
- **Boltzmann Machines.** Removing the "R" from RBM brings us back to where everything started—these MRFs consisting of a set of hidden and visible variables where the energy is given by
$$E(v, h) = -\sum_{i=1}^m h_{ij}v_j - \sum_{k=1}^n \sum_{l=1}^m v_{kl}h_l - \sum_{j=1}^m b_j$$
corresponds to one layer. These dependencies make sampling independently and training more difficult. However, specialized algorithms have been developed [32].

## Next Steps

The goal of this tutorial is to introduce RBMs from a probabilistic graphical model perspective, focusing on material we found helpful in our work. We hope that the reader is now equipped to move on to advanced models building deep learning architectures. All experiments in this tutorial can be reproduced using open source machine learning library.

**Acknowledgments.** The authors acknowledge support from the Federal Ministry of Education and Research under grant number 01GQ951.

## References

1. Ackley, D., Hinton, G.: A learning algorithm for Boltzmann machines. Cognitive Science 9, 147–169 (1985).
2. Bengio, Y.: Learning deep architectures for Trends in Machine Learning 21(6), 1601–1621 (2009).
3. Bengio, Y., Delelleau, O.: Justifying contrastive divergence. Neural Computation 21(6), 1601–1621 (2009).
4. Bengio, Y., Lamblin, P., Popovici, D., Larochelle, H.: Greedy training of neural networks. In Schkopf, B., Platt, J., Hoffman, T. (eds) Advances in Neural Information Processing (NIPS), 153–160 (2007).
5. Bishop, C.M.: Markov chains: Pattern recognition and machine learning. Springer (2006).
6. Bremaux, P.: Markov chains: Gibbs fields, Monte Carlo simulation, and queues.
7. Carreira-Perpián, M.A., Hinton, G.E.: Contrastive divergence. In 10th International Conference on Artificial Intelligence and Systems (AISTATS 2003), 59–66 (2003).
8. Cho, K., Rao, T.: Parallel tempering for learning restricted Boltzmann machines. In Proceedings of the International Joint Conference on Neural Networks (IJCNN 2010), pp. 3246–3253. IEEE Press (2010).
9. Desjaines, G., Curcelle, A.: Parallel tempering for stochastic likelihood learning of RBMs. In Lee, H., Ranzato, M., Hinton, G., Lecun, Y., Ng, A.Y. (eds) NIPS 2010 on Deep Learning and Unsupervised Learning.
10. Desjaines, G., Bengio, Y., Vincent, P., Delleau, E.: Parallel tempering for training of restricted Boltzmann machines. In JMLR Workshop and Conference Proceedings: AISTATS 2010, pp. 145–152 (2010).
11. Fisher, A., Hinton, G.E.: The Divergence of Gibbs Sampling Based Algorithms for Restricted Boltzmann Machines. In Diamantaras, K., Doch, W., Iadis, L.S. (eds) ICANN 2010, Part III. LNCS, vol. 6354, pp. 208–217. Springer, (2010).
12. Geiger, A. G., Bishop, A. C.: Reducing the bias of contrastive divergence. Neural Computation, 12, 664–673 (2000).
13. Geiger, M., Stein, D.: Stochastic learning, Gibbs distributions and the Bayesian restoration of images. IEEE Transactions on Pattern Analysis and Machine Intelligence, 6(7), 71–78 (1984).
14. Hastings, K.W.: Monte Carlo methods using Markov chains and applications. Biometrika, 57(1), 97–109 (1970).
15. Hinton, G.: Training deep belief nets by minimizing contrastive divergence. Neural Computation, 14, 1771–1800 (2002).
16. Hinton, G.E.: Boltzmann machines. Scholarpage 2(5), 1668 (2007).
17. Hinton, G.E.: Learning layers of representations. In Trends in Cognitive Science, Neural Computation 18(7), 1527–1554 (2006).
18. Hinton, G., Salakhutdin, R., Teh, Y.W.: Reducing the dimensionality of wide data with deep learning. Science, 315(5796), 504–507 (2006).
19. Gel, C., Bachman, T., Heidlich-Mier, V.: Sparse. Journal of Machine Learning Research 9, 953–966 (2008).
20. Kramer, J., Williams, C.: Parallel texture boltzmann machines. In: JMLR Workshop and Conference Proceedings: AISTATS 2012, pp. 628–646 (2012).
21. Koller, D., Friedman, N.: Probabilistic graphical models: Principles and techniques. MIT Press (2009).
22. Lauritzen, L.S.: Graphical models. Oxford University Press (1996).
23. Le Roux, R., Bengio, Y.: Representational power of restricted Boltzmann machines and deep belief networks. Neural Computation 20(6), 1631–1649 (2008).
24. Le Roux, N., Hinton, S., Winn, J.M.: Learning a generative model of images by factoring appearance and shape. Neural Computation 25(3), 595–650 (2011).
