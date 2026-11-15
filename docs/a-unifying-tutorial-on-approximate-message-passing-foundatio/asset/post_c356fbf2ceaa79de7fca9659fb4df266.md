
Since \(\|\cdot\| \equiv \|\cdot\|_2 \le D^{\frac{1}{2}-\frac{1}{r}}\|\cdot\|_r\) on \(\mathbb{R}^D\), we see that

\(\frac{1}{n} \sum_{i=1}^n \|X^{(i)} - Y^{(i)}\|^r \le \frac{D^{\frac{r}{2}-1}}{n} \sum_{i=1}^n \sum_{\ell=1}^D |x_i^\ell - y_i^\ell|^r = D^{\frac{r}{2}-1} \sum_{\ell=1}^D \|x^\ell - y^\ell\|_{n,r}^r.\) (B.23)

In addition, by applying the triangle inequality for \(\|\cdot\|_{n,r'}\) and arguing as in (B.23), we have

\(\left(\frac{1}{n} \sum_{i=1}^n (1 + \|X^{(i)}\|^{r-1} + \|Y^{(i)}\|^{r-1})^{r'}\right)^{1/r'}\)
\(\le 1 + \left(\frac{1}{n} \sum_{i=1}^n \|X^{(i)}\|^r\right)^{1/r'} + \left(\frac{1}{n} \sum_{i=1}^n \|Y^{(i)}\|^r\right)^{1/r'}\)
\(\le 1 + \left(D^{\frac{r}{2}-1} \sum_{\ell=1}^D \|x^\ell\|_{n,r}^r\right)^{\frac{r-1}{r}} + \left(D^{\frac{r}{2}-1} \sum_{\ell=1}^D \|y^\ell\|_{n,r}^r\right)^{\frac{r-1}{r}}\)
\(\le 1 + (D^{\frac{r}{2}-1})^{\frac{r-1}{r}} \sum_{\ell=1}^D (\|x^\ell\|_{n,r}^{r-1} + \|y^\ell\|_{n,r}^{r-1}),\) (B.24)

where the final bound follows since \(\|\cdot\|_r \le \|\cdot\|_{r-1}\) on \(\mathbb{R}^D\). Combining (B.22)-(B.24) yields the desired conclusion.

## References

- Advani, M. S., A. M. Saxe, and H. Sompolinsky (2020). “High-dimensional dynamics of generalization error in neural networks”. Neural Netw. 132: 428–446.

- Agresti, A. (2015). Foundations of Linear and Generalized Linear Models. New Jersey: Wiley.

- Albert, A. and J. A. Anderson (1984). “On the existence of maximum likelihood estimates in logistic regression models”. Biometrika. 71: 1–10.

- Aliprantis, C. D. and O. Burkinshaw (1998). Principles of Real Analysis. 3rd edn. San Diego: Academic Press.

- Alon, N., M. Krivelevich, and B. Sudakov (1998). “Finding a large hidden clique in a random graph”. Random Struct. Algorithms. 13: 457–466.

- Anderson, G., A. Guionnet, and O. Zeitouni (2010). An Introduction to Random Matrices. Cambridge: Cambridge University Press.

- Aubin, B., B. Loureiro, A. Maillard, F. Krzakala, and L. Zdeborová (2020). “The spiked matrix model with generative priors”. IEEE Trans. Inf. Theory. 67: 1156–1181.

- Aubin, B., A. Maillard, J. Barbier, F. Krzakala, N. Macris, and L. Zdeborová (2019). “The committee machine: Computational to statistical gaps in learning a two-layers neural network”. J. Stat. Mech. Theory Exp. 124023.

- Bai, Z. and J. Silverstein (2010). Spectral Analysis of Large Dimensional Random Matrices. 2nd edn. New York: Springer.

- Baik, J., G. Ben Arous, and S. Péché (2005). “Phase transition of the largest eigenvalue for nonnull complex sample covariance matrices”. Ann. Probab. 33: 1643–1697.

- Baik, J. and J. W. Silverstein (2006). “Eigenvalues of large sample covariance matrices of spiked population models”. J. Multivariate Anal. 97: 1382–1408.

- Bakhshizadeh, M., A. Maleki, and V. H. de la Pena (2020). “Sharp concentration results for heavy-tailed distributions”. URL: https://arxiv.org/pdf/2003.13819.pdf.

- Barata, J. C. A. and M. S. Hussein (2012). “The Moore–Penrose pseudoinverse: A tutorial review of the theory”. Braz. J. Phys. 42: 146–165.

- Barbier, J., M. Dia, N. Macris, F. Krzakala, T. Lesieur, and L. Zdeborová (2016). “Mutual information for symmetric rank-one matrix estimation: A proof of the replica formula”. Advances in Neural Information Processing Systems. 29: 424–432.

- Barbier, J. and F. Krzakala (2017). “Approximate message-passing decoder and capacity achieving sparse superposition codes”. IEEE Trans. Inf. Theory. 63: 4894–4927.

- Barbier, J., F. Krzakala, N. Macris, L. Miolane, and L. Zdeborová (2019). “Optimal errors and phase transitions in high-dimensional generalized linear models”. Proc. Natl. Acad. Sci. U.S.A. 116: 5451–5460.

- Barbier, J., N. Macris, and C. Rush (2020). “All-or-nothing statistical and computational phase transitions in sparse spiked matrix estimation”. URL: https://arxiv.org/pdf/2006.07971.pdf.

- Bartlett, P. L., P. M. Long, G. Lugosi, and A. Tsigler (2020). “Benign overfitting in linear regression”. Proc. Natl. Acad. Sci. U.S.A. 117: 30063–30070.

- Bayati, M., M. Lelarge, and A. Montanari (2015). “Universality in polytope phase transitions and message passing algorithms”. Ann. Appl. Probab. 25: 753–822.

- Bayati, M. and A. Montanari (2011). “The dynamics of message passing on dense graphs, with applications to compressed sensing”. IEEE Trans. Inf. Theory. 57: 764–785.

- Bayati, M. and A. Montanari (2012). “The LASSO risk for Gaussian matrices”. IEEE Trans. Inf. Theory. 58: 1997–2017.

- Beck, A. and M. Teboulle (2009). “A fast iterative shrinkage-thresholding algorithm for linear inverse problems”. SIAM J. Imaging Sci. 2: 183–202.

- Belkin, M., D. Hsu, S. Ma, and S. Mandal (2019). “Reconciling modern machine-learning practice and the classical bias-variance trade-off”. Proc. Natl. Acad. Sci. U.S.A. 116: 15849–15854.

- Belkin, M., D. Hsu, and J. Xu (2020). “Two models of double descent for weak features”. SIAM J. Math. Data Sci. 2: 1167–1180.

- Bellec, P. C., G. Lecué, and A. B. Tsybakov (2018). “SLOPE meets LASSO: Improved oracle bounds and optimality”. Ann. Statist. 46: 3603–3642.

- Benaych-Georges, F. and R. R. Nadakuditi (2011). “The eigenvalues and eigenvectors of finite, low rank perturbations of large random matrices”. Adv. Math. 227: 494–521.

- Berthier, R., A. Montanari, and P.-M. Nguyen (2020). “State evolution for approximate message passing with non-separable functions”. Inf. Inference. 9: 33–79.

- Blei, D. M., A. Y. Ng, and M. I. Jordan (2003). “Latent Dirichlet allocation”. J. Mach. Learn. Res. 3: 993–1022.

- Bogdan, M., E. van den Berg, C. Sabatti, W. Su, and E. Candès (2015). “SLOPE—Adaptive variable selection via convex optimization”. Ann. Appl. Stat. 9: 1103–1140.

- Bolthausen, E. (2014). “An iterative construction of solutions of the TAP equations for the Sherrington–Kirkpatrick model”. Comm. Math. Phys. 325: 333–366.

- Boucheron, S., G. Lugosi, and P. Massart (2013). Concentration Inequalities: A Nonasymptotic Theory of Independence. Oxford: Oxford University Press.

- Boyd, S., N. Parikh, E. Chu, B. Peleato, and J. Eckstein (2011). “Distributed optimization and statistical learning via the alternating direction method of multipliers”. Found. Trends Mach. Learn. 3: 1–122.

- Brown, L. D. and R. Purves (1973). “Measurable selections of extrema”. Ann. Statist. 1: 902–912.

- Bu, Z., J. Klusowski, C. Rush, and W. Su (2021). “Algorithmic analysis and statistical estimation of SLOPE via approximate message passing”. IEEE Trans. Inf. Theory. 67: 506–537.

- Bühlmann, P. and S. van de Geer (2011). Statistics for High-Dimensional Data: Methods, Theory and Applications. Berlin: Springer.

- Çakmak, B. and M. Opper (2019). “Memory-free dynamics for the Thouless–Anderson–Palmer equations of Ising models with arbitrary rotation-invariant ensembles of random coupling matrices”. Phys. Rev. E. 99: 062140.

- Candès, E. J. and B. Recht (2009). “Exact matrix completion via convex optimization”. Found. Comput. Math. 9: 717–772.

- Candès, E. J. and P. Sur (2020). “The phase transition for the existence of the maximum likelihood estimate in high-dimensional logistic regression”. Ann. Statist. 48: 27–42.

- Capitaine, M., C. Donati-Martin, and D. Féral (2009). “The largest eigenvalues of finite rank deformation of large Wigner matrices: Convergence and nonuniversality of the fluctuations”. Ann. Probab. 37: 1–47.

- Celentano, M. and A. Montanari (2022). “Fundamental barriers to high-dimensional regression with convex penalties”. Ann. Statist. 50: 170–196.

- Celentano, M., A. Montanari, and Y. Wu (2020). “The estimation error of general first order methods”. Proc. Mach. Learn. Res. 125: 1–64.

- Chen, W.-K. and W.-K. Lam (2021). “Universality of approximate message passing algorithms”. Electron. J. Probab. 26: 1–44.

- Dar, Y., V. Muthukumar, and R. Baraniuk (2021). “A farewell to the bias-variance tradeoff? An overview of the theory of overparameterized machine learning”. URL: https://arxiv.org/pdf/2109.02355.pdf.

- d'Ascoli, S., M. Refinetti, G. Biroli, and F. Krzakala (2020). “Double trouble in double descent: Bias and variance(s) in the lazy regime”. Proc. Mach. Learn. Res. 119: 2280–2290.

- Deng, Z., A. Kammoun, and C. Thrampoulidis (2019). “A model of double descent for high-dimensional binary linear classification”. URL: https://arxiv.org/pdf/1911.05822.pdf.

- Deshpande, Y., E. Abbe, and A. Montanari (2016). “Asymptotic mutual information for the balanced binary stochastic block model”. Inf. Inference. 6: 125–170.

- Deshpande, Y. and A. Montanari (2014). “Information-theoretically optimal sparse PCA”. In: 2014 IEEE International Symposium on Information Theory. 2197–2201.

- Deshpande, Y. and A. Montanari (2015). “Finding hidden cliques of size \sqrt{N/e} in nearly linear time”. Found. Comput. Math. 15: 1069–1128.

- Donoho, D. L., A. Javanmard, and A. Montanari (2013). “Information-theoretically optimal compressed sensing via spatial coupling and approximate message passing”. IEEE Trans. Inf. Theory. 59: 7434–7464.

- Donoho, D. L. and I. M. Johnstone (1994). “Minimax risk over l_p balls for l_q error”. Prob. Theory Related Fields. 99: 277–303.

- Donoho, D. L. and I. M. Johnstone (1998). “Minimax estimation via wavelet shrinkage”. Ann. Statist. 26: 879–921.

- Donoho, D. L., A. Maleki, and A. Montanari (2009). “Message-passing algorithms for compressed sensing”. Proc. Natl. Acad. Sci. U.S.A. 106: 18914–18919.

- Donoho, D. and A. Montanari (2015). “Variance breakdown of Huber (M)-estimators: n/p \to m \in (1, \infty)”. URL: https://arxiv.org/pdf/1503.02106.pdf.

- Donoho, D. and A. Montanari (2016). “High dimensional robust M-estimation: Asymptotic variance via approximate message passing”. Probab. Theory Related Fields. 166: 935–969.

- Dudley, R. M. (2002). Real Analysis and Probability. 2nd edn. Cambridge: Cambridge University Press.

- Dümbgen, L., R. J. Samworth, and J. A. Wellner (2021). “Bounding distributional errors via density ratios”. Bernoulli. 27: 818–852.
