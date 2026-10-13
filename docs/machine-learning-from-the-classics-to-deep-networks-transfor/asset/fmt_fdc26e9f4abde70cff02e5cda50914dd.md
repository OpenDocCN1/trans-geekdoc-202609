
*   [26] R. Karlsson, F. Gustafsson, Complexity analysis of the marginalized particle filter, *IEEE Trans. Signal Process.* 2005;53(11):4408–4411.
*   [27] G. Kitagawa, Monte Carlo filter and smoother for non-Gaussian nonlinear state space models, *J. Comput. Graph. Stat.* 1996;5:1–25.
*   [28] J.H. Kotecha, P.M. Djurić, Gaussian particle filtering, *IEEE Trans. Signal Process.* 2003;51:2592–2601.
*   [29] J.H. Kotecha, P.M. Djurić, Gaussian sum particle filtering, *IEEE Trans. Signal Process.* 2003;51:2602–2612.
*   [30] J.S. Liu, R. Chen, Sequential Monte Carlo methods for dynamical systems, *J. Am. Stat. Assoc.* 1998;93:1032–1044.
*   [31] J.S. Liu, *Monte Carlo Strategies in Scientific Computing*. New York: Springer; 2001.
*   [32] J. MacCormick, M. Isard, Partitioned sampling, articulated objects, and interface-quality hand tracking, *Proceedings of the 6th European Conference on Computer Vision, Part II*. *ECCV*. London, UK: Springer-Verlag; 2000:3–19.
*   [33] A. Makris, D. Kosmopoulos, S. Perantonis, S. Theodoridis, A hierarchical feature fusion framework for adaptive visual tracking, *Image and Vision Computing* 2011;29(9):594–606.
*   [34] C. Musso, N. Oudjane, F. Le Gland, Improving regularised particle filters, A. Doucet, N. de Freitas, N.J. Gordon, eds. *Sequential Monte Carlo Methods in Practice*. New York: Springer-Verlag; 2001.
*   [35] A. Owen, Y. Zhou, Safe and effective importance sampling, *J. Am. Stat. Assoc.* 2000;95:135–143.
*   [36] M.K. Pitt, N. Shephard, Filtering via simulation: auxiliary particle filters, *J. Am. Stat. Assoc.* 1999;94:590–599.
*   [37] M.K. Pitt, R.S. Silva, P. Giordani, R. Kohn, Auxiliary particle filtering within adaptive Metropolis-Hastings sampling, [arXiv:1006.1914 [stat.Me]](http://www.arxiv.org/abs/1006.1914); 2010.
*   [38] M.N. Rosenbluth, A.W. Rosenbluth, Monte Carlo calculation of the average extension of molecular chains, *J. Chem. Phys.* 1956;23(2):356–359.
*   [39] R. van der Merwe, N. de Freitas, A. Doucet, E. Wan, The unscented particle filter, *Proceedings Advances in Neural Information Processing Systems*. *NIPS*. 2000.

# Chapter 18: Neural networks and deep learning: part I

## Chapter Outline

*   18.1 [Introduction](#Chp018_885-995_B978044329238500024X.xhtml#s0010)
*   18.2 [The perceptron](#Chp018_885-995_B978044329238500024X.xhtml#s0015)
*   18.3 [Feed-forward multilayer neural networks](#Chp018_885-995_B978044329238500024X.xhtml#s0020)
    *   18.3.1 [Fully connected networks](#Chp018_885-995_B978044329238500024X.xhtml#s0025)
*   18.4 [The backpropagation algorithm](#Chp018_885-995_B978044329238500024X.xhtml#s0030)
    *   [Nonconvexity of the cost function](#Chp018_885-995_B978044329238500024X.xhtml#s0035)
    *   18.4.1 [The gradient descent backpropagation scheme](#Chp018_885-995_B978044329238500024X.xhtml#s0040)
        *   [Pattern-by-pattern/online scheme](#Chp018_885-995_B978044329238500024X.xhtml#s0045)
        *   [Mini-batch schemes](#Chp018_885-995_B978044329238500024X.xhtml#s0050)
    *   18.4.2 [Variants of the basic gradient descent scheme](#Chp018_885-995_B978044329238500024X.xhtml#s0055)
        *   [Gradient descent with a momentum term](#Chp018_885-995_B978044329238500024X.xhtml#s0060)
        *   [Nesterov's momentum algorithm](#Chp018_885-995_B978044329238500024X.xhtml#s0065)
        *   [The AdaGrad algorithm](#Chp018_885-995_B978044329238500024X.xhtml#s0070)
        *   [The RMSProp with Nesterov momentum](#Chp018_885-995_B978044329238500024X.xhtml#s0075)
        *   [The adaptive moment estimation algorithm (Adam)](#Chp018_885-995_B978044329238500024X.xhtml#s0080)
        *   [Some practical hints](#Chp018_885-995_B978044329238500024X.xhtml#s0085)
        *   [Batch normalization](#Chp018_885-995_B978044329238500024X.xhtml#s0090)
    *   18.4.3 [Beyond the gradient descent rationale](#Chp018_885-995_B978044329238500024X.xhtml#s0095)
*   18.5 [Selecting a loss function](#Chp018_885-995_B978044329238500024X.xhtml#s0100)
*   18.6 [Vanishing and exploding gradients](#Chp018_885-995_B978044329238500024X.xhtml#s0105)
    *   18.6.1 [The rectified linear unit](#Chp018_885-995_B978044329238500024X.xhtml#s0110)
*   18.7 [Regularizing the network](#Chp018_885-995_B978044329238500024X.xhtml#s0115)
    *   [Dropout](#Chp018_885-995_B978044329238500024X.xhtml#s0120)
*   18.8 [Designing deep neural networks: a summary](#Chp018_885-995_B978044329238500024X.xhtml#s0125)
*   18.9 [Universal approximation property of feed-forward neural networks](#Chp018_885-995_B978044329238500024X.xhtml#s0130)
*   18.10 [Neural networks: a Bayesian flavor](#Chp018_885-995_B978044329238500024X.xhtml#s0135)
*   18.11 [Shallow versus deep architectures](#Chp018_885-995_B978044329238500024X.xhtml#s0140)
    *   18.11.1 [The power of deep architectures](#Chp018_885-995_B978044329238500024X.xhtml#s0145)
        *   [On the representation properties of deep networks](#Chp018_885-995_B978044329238500024X.xhtml#s0150)
        *   [Distributed representations](#Chp018_885-995_B978044329238500024X.xhtml#s0155)
        *   [On the optimization of deep networks: some theoretical highlights](#Chp018_885-995_B978044329238500024X.xhtml#s0160)
        *   [Generalization properties and the double descent curve phenomenon](#Chp018_885-995_B978044329238500024X.xhtml#s0165)
*   18.12 [Convolutional neural networks](#Chp018_885-995_B978044329238500024X.xhtml#s0170)
    *   18.12.1 [The need for convolutions](#Chp018_885-995_B978044329238500024X.xhtml#s0175)
        *   [The convolution step](#Chp018_885-995_B978044329238500024X.xhtml#s0180)
        *   [The nonlinearity step](#Chp018_885-995_B978044329238500024X.xhtml#s0185)
        *   [The pooling step](#Chp018_885-995_B978044329238500024X.xhtml#s0190)
    *   18.12.2 [Convolution over volumes](#Chp018_885-995_B978044329238500024X.xhtml#s0195)
        *   [Network in network and 1 × 1 convolution](#Chp018_885-995_B978044329238500024X.xhtml#s0200)
    *   18.12.3 [The full CNN architecture](#Chp018_885-995_B978044329238500024X.xhtml#s0205)
        *   [What deep neural networks learn](#Chp018_885-995_B978044329238500024X.xhtml#s0210)
    *   18.12.4 [CNNs: the epilogue](#Chp018_885-995_B978044329238500024X.xhtml#s0215)
*   18.13 [Recurrent neural networks](#Chp018_885-995_B978044329238500024X.xhtml#s0220)
    *   18.13.1 [Backpropagation through time](#Chp018_885-995_B978044329238500024X.xhtml#s0225)
        *   [Vanishing and exploding gradients](#Chp018_885-995_B978044329238500024X.xhtml#s0230)
        *   [The long short-term memory (LSTM) network](#Chp018_885-995_B978044329238500024X.xhtml#s0235)
    *   18.13.2 [Attention and memory](#Chp018_885-995_B978044329238500024X.xhtml#s0240)
*   18.14 [Adversarial examples](#Chp018_885-995_B978044329238500024X.xhtml#s0245)
    *   [Adversarial training](#Chp018_885-995_B978044329238500024X.xhtml#s0250)
*   18.15 [Capsule networks](#Chp018_885-995_B978044329238500024X.xhtml#s0255)
    *   [Training](#Chp018_885-995_B978044329238500024X.xhtml#s0260)
*   18.16 [Deep neural networks: some final remarks](#Chp018_885-995_B978044329238500024X.xhtml#s0265)
    *   [Transfer learning](#Chp018_885-995_B978044329238500024X.xhtml#s0270)
    *   [Multitask learning](#Chp018_885-995_B978044329238500024X.xhtml#s0275)
    *   [Geometric deep learning](#Chp018_885-995_B978044329238500024X.xhtml#s0280)
    *   [Open problems](#Chp018_885-995_B978044329238500024X.xhtml#s0285)
*   18.17 [Problems](#Chp018_885-995_B978044329238500024X.xhtml#s0290)
    *   [Computer exercises](#Chp018_885-995_B978044329238500024X.xhtml#s0295)
*   [References](#Chp018_885-995_B978044329238500024X.xhtml#bl0010)

## 18.1 Introduction
