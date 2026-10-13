

## 2. (b)

现在，从每个分布中分别采样 `N₁ = 100` 和 `N₂ = 20` 个点并重复实验，以复现 [图 12.9](#Chp012_583-634_B9780443292385000184.xhtml#f0065) 的结果。

## 3. (c)

尝试不同的配置，并使用与真实簇数不同的 `K` 值进行尝试。对结果进行评论。

## 4. (d)

尝试不同的初始化点，也尝试远离簇真实均值的点。对结果进行评论。

## 2. 12.20

在区间 `[-1, 1]` 内生成 50 个等距输入数据点。假设两个线性回归模型，第一个模型尺度为 0.005、截距为 −1，第二个模型尺度为 0.018、截距为 1。使用第一个模型生成区间 `[-0.5, 0.5]` 内输入点的观测值，使用第二个模型生成区间 `[-1, -0.5] ∪ [0.5, 1]` 内输入点的观测值。此外，添加均值为零、方差为 0.01 的高斯噪声。接下来，实现第 [12.9.1](#Chp012_583-634_B9780443292385000184.xhtml#s0090) 节中开发的 EM 算法。将噪声精度 `β` 初始化为其真实值。对于第 1、5 和 30 次迭代，绘制数据点和模型的估计线性函数 `θ₁,ₖx + θ₀,ₖ`，`k ∈ {1, 2}`，以复现 [图 12.14](#Chp012_583-634_B9780443292385000184.xhtml#f0090) 的结果。

## 参考文献

*   [1] D. Arthur, S. Vassilvitskii, *k*-means++: the advantages of careful seeding, *Proceedings 18th ACM-SIAM Symposium on Discrete Algorithms*. *SODA*. 2007:1027–1035.
*   [2] L.E. Baum, T. Petrie, G. Soules, N. Weiss, A maximization technique occurring in the statistical analysis of probabilistic functions of Markov chains, *Ann. Math. Stat.* 1970;41:164–171.
*   [3] M.J. Beal, *Variational Algorithms for Approximate Bayesian Inference*. [PhD Thesis] University College London; 2003.
*   [4] L. Bo, C. Sminchisescu, A. Kanaujia, D. Metaxas, Fast algorithms for large scale conditional 3D prediction, *Proceedings International Conference to Computer Vision and Pattern Recognition*. *CVPR, Anchorage, AK*. 2008.
*   [5] J.S. Bridle, Probabilistic interpretation of feedforward classification network outputs with relationship to statistical pattern recognition, F. Fougelman-Soulie, J. Heurault, eds. *Neuro-Computing: Algorithms, Architectures and Applications*. Springer Verlag; 1990.
*   [6] O. Cappe, E. Mouline, Online EM algorithm for latent data models, *J. R. Stat. Soc. B* 2009;71(3):593–613.
*   [7] G. Casella, R.L. Berger, *Statistical Inference*. second ed. Duxbury Press; 2002.
*   [8] G. Celeux, J. Diebolt, The SEM algorithm: a probabilistic teacher derived from the EM algorithm for the mixture problem, *Comput. Stat. Q.* 1985;2:73–82.
*   [9] S.P. Chatzis, D.I. Kosmopoulos, T.A. Varvarigou, Signal modeling and classification using a robust latent space model based on *t*-distributions, *IEEE Trans. Signal Process.* 2008;56(3):949–963.
*   [10] S.P. Chatzis, D. Kosmopoulos, T.A. Varvarigou, Robust sequential data modeling using an outlier tolerant hidden Markov model, *IEEE Trans. Pattern Anal. Mach. Intell.* 2009;31(9):1657–1669.
*   [11] B. Delyon, M. Lavielle, E. Moulines, Convergence of a stochastic approximation version of the EM algorithm, *Ann. Stat.* 1999;27(1):94–128.
*   [12] A.P. Dempster, N.M. Laird, D.B. Rubin, Maximum likelihood from incomplete data via the EM algorithm, *J. R. Stat. Soc. B* 1977;39(1):1–38.
*   [13] S.F. Gull, Bayesian inductive inference and maximum entropy, G.J. Erickson, C.R. Smith, eds. *Maximum Entropy and Bayesian Methods in Science and Engineering*. Kluwer; 1988.
*   [14] M.R. Gupta, Y. Chen, Theory and use of the EM algorithm, *Found. Trends Signal Process.* 2010;4(3):223–299.
*   [15] L.K. Hansen, C.E. Rasmussen, Pruning from adaptive regularization, *Neural Comput.* 1993;6:1223–1232.
*   [16] L.K. Hansen, J. Larsen, Unsupervised learning and generalization, *IEEE International Conference on Neural Networks*. 1996:25–30.
*   [17] L.K. Hansen, Bayesian averaging is well-temperated, S. Solla, ed. *Proceedings Neural Information Processing*. *NIPS*. MIT Press; 2000:265–271.
*   [18] D. Haussler, M. Kearns, R. Schapire, Bounds on the sample complexity of Bayesian learning using information theory and the VC dimension, *Mach. Learn.* 1994;14:83–113.
*   [19] S. Haykin, *Neural Networks: A Comprehensive Foundation*. Prentice Hall; 1999.
*   [20] D.R. Hunter, K. Lange, A tutorial on MM algorithms, *Am. Stat.* 2004;58:30–37.
*   [21] E.T. Jaynes, On the rationale of the maximum entropy methods, *Proc. IEEE* 1982;70(9):939–952.
*   [22] E.T. Jaynes, Bayesian methods—an introductory tutorial, J.H. Justice, ed. *Maximum Entropy and Bayesian Methods in Science and Engineering*. Cambridge University Press; 1986.
*   [23] H. Jeffreys, *Theory of Probability*. Oxford University Press; 1992.
*   [24] M.I. Jordan, R.A. Jacobs, Hierarchical mixture of experts and the EM algorithm, *Neural Comput.* 1994;6:181–214.
*   [25] P. Liang, D. Klein, Online EM for unsupervised models, *Proceeding of Human Language Technologies: The 2009 Annual Conference of the North American Chapter of the Association for Computational Linguistics*. *NAACL*. 2009:611–619.
*   [26] T.J. Loredo, From Laplace to supernova SN 1987A: Bayesian inference in astrophysics, P. Fougere, ed. *Maximum Entropy and Bayesian Methods*. Kluwer; 1990:81–143.
*   [27] D.J.C. McKay, Bayesian interpolation, *Neural Comput.* 1992;4(3):417–447.

