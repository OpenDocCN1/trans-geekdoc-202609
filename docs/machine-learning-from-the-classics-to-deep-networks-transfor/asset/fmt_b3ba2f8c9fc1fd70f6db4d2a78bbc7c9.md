
*   [23] M. Kearns, L.G. Valiant, Cryptographic limitations of learning Boolean formulae and finite automata, *J. ACM* 1994;41(1):67–95.
*   [24] J. Kittler, M. Hatef, R. Duin, J. Matas, On combining classifiers, *IEEE Trans. Pattern Anal. Mach. Intell.* 1998;20(3):228–234.
*   [25] I.L. Kuncheva, *Pattern Classifiers: Methods and Algorithms*. John Wiley; 2004.
*   [26] D. Meyer, F. Leisch, K. Hornik, The support vector machine under test, *Neurocomputing* 2003;55:169–186.
*   [27] D. Michie, D.J. Spiegelhalter, C.C. Taylor, eds. *Machine Learning, Neural, and Statistical Classification*. London: Ellis Horwood; 1994.
*   [28] R. Neal, J. Zhang, High dimensional classification with Bayesian neural networks and Dirichlet diffusion trees, I. Guyon, S. Gunn, M. Nikravesh, L. Zadeh, eds. *Feature Extraction, Foundations and Applications*. New York: Springer Verlag; 2006:265–296.
*   [29] G. Ratsch, M.K. Warmuth, Efficient margin maximizing with boosting, *J. Mach. Learn. Res.* 2005;6:2131–2152.
*   [30] G. Ridgeway, The state of boosting, *Comput. Sci. Stat.* 1999;31:172–181.
*   [31] B.D. Ripley, *Pattern Recognition and Neural Networks*. Cambridge University Press; 1996.
*   [32] R.E. Schapire, V. Freund, P. Bartlett, W.S. Lee, Boosting the margin: a new explanation for the effectiveness of voting methods, *Ann. Stat.* 1998;26(5):1651–1686.
*   [33] R.E. Schapire, M. Rochery, M. Rahim, N. Gupta, Boosting with prior knowledge for call classification, *IEEE Trans. Speech Audio Process.* 2005;13(2):174–181.
*   [34] J. Shotton, A. Fitzgibbon, M. Cook, T. Sharp, M. Finocchio, R. Moore, A. Kipman, A.A. Blake, Real-time human pose recognition in parts from single depth images, *Proceedings of the Conference on Computer Vision and Pattern Recognition*. *CVPR*. 2011.
*   [35] R. Quinlan, *C4.5: Programs for Machine Learning*. San Mateo: Morgan Kaufmann; 1993.
*   [36] D.B. Rubin, Iterative reweighted least squares, *Encyclopedia of Statistical Sciences, vol. 4*. New York: John Wiley; 1983:272–275.
*   [37] S. Russell, P. Norvig, *Artificial Intelligence: A Modern Approach*. third ed. Pearson; 2010.
*   [38] S. Theodoridis, K. Koutroumbas, *Pattern Recognition*. fourth ed. Academic Press; 2009.
*   [39] S. Theodoridis, A. Pikrakis, K. Koutroumbas, D. Cavouras, *An Introduction to Pattern Recognition: A MATLAB Approach*. Academic Press; 2010.
*   [40] L.G. Valiant, A theory of the learnable, *Commun. ACM* 1984;27(11):1134–1142.
*   [41] A. Webb, *Statistical Pattern Recognition*. second ed. John Wiley; 2002.
*   [42] D. Wolpert, Stacked generalization, *Neural Netw.* 1992;5:241–259.
*   [43] D. Wolpert, The lack of a priori distinctions between learning algorithms, *Neural Comput.* 1996;8(7):1341–1390.
*   [44] Y. Wu, H. Tjelmeland, M. West, Bayesian CART: prior structure and MCMC computations, *J. Comput. Graph. Stat.* 2007;16(1):44–66.

---

# Chapter 8: Parameter learning: a convex analytic path^⍟

## Chapter Outline

*   8.1  [Introduction](#Chp008_343-416_B9780443292385000147.xhtml#s0010)
*   8.2  [Convex sets and functions](#Chp008_343-416_B9780443292385000147.xhtml#s0015)
    *   8.2.1  [Convex sets](#Chp008_343-416_B9780443292385000147.xhtml#s0020)
    *   8.2.2  [Convex functions](#Chp008_343-416_B9780443292385000147.xhtml#s0025)
*   8.3  [Projections onto convex sets](#Chp008_343-416_B9780443292385000147.xhtml#s0030)
    *   8.3.1  [Properties of projections](#Chp008_343-416_B9780443292385000147.xhtml#s0035)
*   8.4  [Fundamental theorem of projections onto convex sets](#Chp008_343-416_B9780443292385000147.xhtml#s0040)
*   8.5  [A parallel version of POCS](#Chp008_343-416_B9780443292385000147.xhtml#s0045)
*   8.6  [From convex sets to parameter estimation and machine learning](#Chp008_343-416_B9780443292385000147.xhtml#s0050)
    *   8.6.1  [Regression](#Chp008_343-416_B9780443292385000147.xhtml#s0055)
    *   8.6.2  [Classification](#Chp008_343-416_B9780443292385000147.xhtml#s0060)
*   8.7  [Infinitely many closed convex sets: the online learning case](#Chp008_343-416_B9780443292385000147.xhtml#s0065)
    *   8.7.1  [Convergence of APSM](#Chp008_343-416_B9780443292385000147.xhtml#s0070)
*   8.8  [Constrained learning](#Chp008_343-416_B9780443292385000147.xhtml#s0080)
*   8.9  [The distributed APSM](#Chp008_343-416_B9780443292385000147.xhtml#s0085)
*   8.10  [Optimizing nonsmooth convex loss functions](#Chp008_343-416_B9780443292385000147.xhtml#s0090)
    *   8.10.1  [Subgradients and subdifferentials](#Chp008_343-416_B9780443292385000147.xhtml#s0095)
    *   8.10.2  [Minimizing nonsmooth continuous convex loss functions: the batch learning case](#Chp008_343-416_B9780443292385000147.xhtml#s0100)
    *   8.10.3  [Online learning for convex optimization](#Chp008_343-416_B9780443292385000147.xhtml#s0125)
*   8.11  [Regret analysis](#Chp008_343-416_B9780443292385000147.xhtml#s0140)
    *   [Regret analysis of the subgradient algorithm](#Chp008_343-416_B9780443292385000147.xhtml#s0145)
*   8.12  [Online learning and big data applications: a discussion](#Chp008_343-416_B9780443292385000147.xhtml#s0150)
    *   [Approximation, estimation, and optimization errors](#Chp008_343-416_B9780443292385000147.xhtml#s0155)
    *   [Batch versus online learning](#Chp008_343-416_B9780443292385000147.xhtml#s0160)
*   8.13  [Proximal operators](#Chp008_343-416_B9780443292385000147.xhtml#s0165)
    *   8.13.1  [Properties of the proximal operator](#Chp008_343-416_B9780443292385000147.xhtml#s0170)
    *   8.13.2  [Proximal minimization](#Chp008_343-416_B9780443292385000147.xhtml#s0175)
*   8.14  [Proximal splitting methods for optimization](#Chp008_343-416_B9780443292385000147.xhtml#s0185)
    *   [The proximal forward-backward splitting operator](#Chp008_343-416_B9780443292385000147.xhtml#s0190)
    *   [Alternating direction method of multipliers (ADMM)](#Chp008_343-416_B9780443292385000147.xhtml#s0195)
    *   [Mirror descent algorithms](#Chp008_343-416_B9780443292385000147.xhtml#s0200)
*   8.15  [Distributed optimization: some highlights](#Chp008_343-416_B9780443292385000147.xhtml#s0205)
*   [Problems](#Chp008_343-416_B9780443292385000147.xhtml#s0210)
    *   [Computer exercises](#Chp008_343-416_B9780443292385000147.xhtml#s0215)
*   [References](#Chp008_343-416_B9780443292385000147.xhtml#bl0010)

## 8.1 Introduction

The theory of convex sets and functions has a rich history and has been the focus of intense study for over a century in mathematics. In the terrain of applied sciences and engineering, the revival of interest in convex functions and optimization is traced back to the early 1980s. In addition to the increased processing power that became available via the use of computers, certain theoretical developments were catalytic in demonstrating the power of such techniques. For example, the advent of the so-called interior point methods opened a new path in solving the classical linear programming task. Moreover, it was increasingly realized that, despite its advantages, the least-squares (LS) method also has a number of drawbacks, particularly in the presence of non-Gaussian noise and the presence of outliers. It has been demonstrated that the use of alternative loss functions, which may not even be differentiable, can alleviate a number of problems that are associated with the LS methods. Furthermore, the increased interest in robust learning methods brought into the scene the need for nontrivial constraints, which the optimized solution has to respect. In the machine learning community, the discovery of support vector machines, to be treated in Chapter [11](#Chp011_519-582_B9780443292385000172.xhtml), played an important role in popularizing convex optimization techniques.
