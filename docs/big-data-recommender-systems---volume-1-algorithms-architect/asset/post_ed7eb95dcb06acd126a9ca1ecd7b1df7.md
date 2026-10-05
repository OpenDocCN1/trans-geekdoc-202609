
# Deep generative models for recommender systems

![](img/6d0ce7dba01af52e1c2fae47d5b04a05_145_0.png)

**Figure 6.9 Collaborative variational autoencoder:** (a) shows the integrated graphical structure of PMF and VAE and (b) shows the content generation part using VAE

Section 6.2.3), this posterior is intractable to compute; consequently, we resort to VI. The ELBO for this model is given as follows:

```
log P(X, R) = E_q[log P(Z, U, V, R, X) - q(U, V, Z)] (6.35)
```

Here, the variational distribution $q$ is over three latent variables, $U, V,$ and $Z$. The RHS of the ELBO (i.e., the likelihood term) can be expanded as

```
\mathcal{L}(U, V, \theta, \phi) = E_{q(Z)}[log P(X|Z) - \mathscr{D}(q(Z|X) || P(Z))] + E_{q(Z)}[log P(V|Z) + log P(R|U) + log Pr(U)] (6.36)
```

where $\phi$ and $\theta$ are the set of weights for the encoder and decoder networks, respectively. The first term of the above equation is simply the ELBO of VAE, while the second term is likelihood of PMF. One can observe that the ELBO of VAE has two parts, the first is simply the sum squared error between the predicted and actual inputs, and the second term is $\mathscr{D}$ the KL divergence between two multivariate normal distributions which is given as

```
\mathscr{D}(q(Z|X)||Pr(Z)) = -\frac{1}{2}(tr (\Sigma_{\phi}(x)) + (\mu_{\phi}(x))^T (\mu_{\phi}(x)) - log det(\Sigma_{\phi}(x))) (6.37)
```

In the likelihood function $\mathcal{L}(U, V, \theta, \phi)$, it is straightforward to take the gradient w.r.t. to $\theta$; however, the gradient w.r.t. to $\phi$ cannot be estimated since the sampling operation is not a deterministic function. This in turns makes back-propagation unfeasible. A reparameterization trick is adopted to obtain samples of $z$ from an isotropic normal distribution where $z = \mu_{\phi}(x) + \epsilon \Sigma_{\phi}(x)$, $\epsilon \sim N(0, I)$ and $x$ is the attribute vector of a single item [34]. Substituting the corresponding distributions in 6.36, the following MAP estimate is obtained:

```
\mathscr{L}^{MAP}(U, V, \theta, \phi) = \mathscr{L}(VAE) - \sum_{ij} \frac{C_{ij}}{2}(R_{ij} - U_i^T V_j)^2 - \frac{\lambda_U}{2} \sum_{i} ||U_i||^2 - \frac{\lambda_V}{2} \sum_{j} E_{q(Z|Z)} ||V_j||^2 (6.38)
```

where $\mathcal{L}(VAE)$ indicates the ELBO of VAE. Readers should note that the above expressions are not strictly a MAP estimate since the parameter Z is still inferred using a variational distribution. Hence, we denote the above expression as $\mathcal{L}^{MAP}$.

**Rating prediction:** After learning the parameters $U, V$ and $Z$, for an observed item $D$ the predicted rating for an item $j$ by a user $i$ can be obtained as follows:

```
$E[R_{j|D}] \approx E[u_i|D] + E[v_j|D]$ \quad (6.39)
```

If there are no regrets for an item $j$, the term $E[v_j|D]$ will not have any effect over the above expression, and the predicted rating will be purely based on the content information of the item.

# 6.5 Summary

This chapter presents some recent trends in generative and DL models for recommender systems. It begins by introducing classic generative models such as PMF and LDA and the methodology of integrating PMF with LDA to create a hybrid model called CTR. The second section introduces recommendation frameworks that are purely based on DL, where we discuss models as RBM-CF, AutoRec, NCF and RNN. The final section of this chapter illustrates the strengths and weaknesses of generative and DL models and explains the methodology of merging these techniques to create deep generative models such as CDAE and CVAE.

# References

- [1] Mnih A, Salakhutdinov RR. Probabilistic matrix factorization. In: Advances in Neural Information Processing Systems; 2008. p. 1257–1264.
- [2] Hofmann T. Probabilistic semantic indexing. In: Proceedings of the 22nd Annual International ACM SIGIR Conference on Research and Development in Information Retrieval. ACM; 1999. p. 50–57.
- [3] Blei DM, Ng Jordan. Latent Dirichlet allocation. The Journal of Machine Learning Research. 2003;3:993–1022.
- [4] Wang C, Blei DM. Collaborative modeling for recommending scientific articles. In: Proceedings of the 17th ACM KDD Conference on Knowledge Discovery and Mining. ACM; 2001. p. 448–456.
- [5] Schmidhuber J. Deep learning in neural networks: An overview. Neural Networks. 2015;65–117.
- [6] Covington P, Adams J, Sargin E. Deep neural networks for recommendations. In: Proceedings of the 10th ACM Conference on Recommender Systems. ACM; 2016. p. 191–198.
- [7] Cheng HT, Koc L, Harmsen J, et al. Wide & deep learning. In: Proceedings of the 1st Workshop on Deep Learning. ACM; 2016. p. 7–10.
- [8] Okura S, Tagami Y, Ono S, et al. Embedding-based recommendation for millions of users. In: Proceedings of the 23rd ACM SIGKDD Conference on Knowledge Discovery and Mining. ACM; 2017. 1933–1942.
- [9] Salakhutdinov R, Mnih A, Hinton G. Restricted Boltzmann machines for collaborative filtering. In: Proceedings of the 24th International Conference on Machine Learning. ACM; 2007. 791–798.
- [10] Sedhain S, Menon AK, Sanner S, et al. AutoRec: Autoencoders meet collaborative filtering. In: Proceedings of the 24th International Conference on World Wide Web. ACM; 2015. 111–112.
- [11] He X, Liao L, Zhang H, et al. Neural collaborative filtering. In: Proceedings of the 26th International Conference on World Wide Web. International World Web Conference Steering; 2017. 173–182.
- [12] Wu CY, Ahmed A, Beutel A, et al. Recurrent neural networks. In: Proceedings of The ACM International Conference on Web Search and Mining. ACM; 2017. 495–503.
- [13] Wang H, Wang N, Yang DY. Collaborative deep learning for recommender systems. In: Proceedings of the 21st ACM SIGKDD Conference on Knowledge Discovery and Mining. ACM; 2015. 1235–1244.
- [14] Li X, She J. Collaborative variational autoencoder for recommender systems. In: Proceedings of the 23rd ACM SIGKDD Conference on Knowledge Discovery and Mining. ACM; 2017. 305–314.
- [15] Koren Y, Bell R, Volinsky C. Matrix factorization techniques for recommender systems. Computer. 2009;42(8):30–37.
- [16] Liu B, Fu Y, Yao Z, et al. Learning geographical preferences for point-interest recommendation. In: Proceedings of the 19th ACM SIGKDD Conference on Knowledge Discovery and Mining. ACM; 2013. 1043–1051.
- [17] Chanie AJ, Blei DM, Eliassi-Rad T. A probabilistic model for using social networks in personalized item recommendation. In: Proceedings of the 9th ACM Conference on Recommender Systems. ACM; 2015. 43–50.
- [18] Hofmann T, Puzichha J. Latent class models for collaborative filtering. In: IJCAI vol. 99, 1999. 688–693.
- [19] Popescul A, Pennock DM, Lawrence S. Probabilistic models for unified collaborative and content-based recommendation in sparse-data environments. In: Proceedings of the Seventeenth Conference on Uncertainty in Artificial Intelligence. Morgan Kaufmann Publishers Inc.; 2001. 437–444.
- [20] Ye M, Liu X, Lee WC. Exploring social influence for recommendation: A generative model approach. In: Proceedings of the 35th ACM SIGIR Conference on Research and Development in Information Retrieval. ACM; 2012. p. 671–680.
- [21] Yuan Q, Cong G, Ma Z, et al. Who, where and when what: Discover spatio-temporal topics for twitter users. In: Proceedings of the 19th ACM SIGKDD Conference on Knowledge Discovery and Mining. ACM; 2013, p. 605–613.
