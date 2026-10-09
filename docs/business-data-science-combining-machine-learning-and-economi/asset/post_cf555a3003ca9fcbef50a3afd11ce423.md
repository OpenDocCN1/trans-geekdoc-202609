
8. Alex Krizhevsky, Ilya Sutskever, and Geoffrey E. Hinton. Imagenet classification with deep convolutional neural networks. In *Advances in Neural Information Processing Systems*, pages 1097–1105, 2012.

9. John Haugeland. *Artificial Intelligence: The Very Idea*. MIT Press, 1985.

10. Yann LeCun, Léon Bottou, Yoshua Bengio, and Patrick Haffner. Gradient-based learning applied to document recognition. *Proceedings of the IEEE*, 86: 2278–2324, 1998.

11. Matthias Feurer, Aaron Klein, Katharina Eggenspenger, Jost Springenberg, Manuel Blum, and Frank Hutter. Efficient and robust automated machine learning. In *Advances in Neural Information Processing Systems*, pages 2962–2970, 2015.

12. A tensor is a multidimensional extension of a matrix—that is, a matrix is another name for a two-dimensional tensor.

13. Ian Goodfellow, Yoshua Bengio, and Aaron Courville. *Deep Learning*. MIT Press, 2016.

14. In the 1990s, people spent much effort choosing among different node transformation functions. More recently, the consensus is that you can just use a simple and computationally convenient transformation (like ReLU). If you have enough nodes and layers, the specific transformation doesn’t really matter, so long as it is nonlinear.

15. Frank Rosenblatt. The perceptron: A probabilistic model for information storage and organization in the brain. *Psychological review*, 65:386, 1958.

16. David E. Rumelhart, Geoffrey E. Hinton, Ronald J. Williams, et al. Learning representations by back-propagating errors. *Cognitive Modeling*, 5(3):1, 1988.

17. Sepp Hochreiter and Jürgen Schmidhuber. Long short-term memory. *Neural Computation*, 9(8):1735–1780, 1997; and Yann LeCun, Léon Bottou, Yoshua Bengio, and Patrick Haffner. Gradient-based learning applied to document recognition. *Proceedings of the IEEE*, 86: 2278–2324, 1998.

18. Kurt Hornik, Maxwell Stinchcombe, and Halbert White. Multilayer feedforward networks are universal approximators. *Neural Networks*, 2:359–366, 1989.

19. Radford M. Neal. *Bayesian Learning for Neural Networks*, volume 118. Springer Science & Business Media, 2012.

20. Geoffrey E. Hinton, Simon Osindero, and Yee-Whye Teh. A fast learning algorithm for deep belief nets. *Neural Computation*, 18(7):1527–1554, 2006.

21. Yoshua Bengio, Yann LeCun, et al. Scaling learning algorithms towards AI. *Large-Scale Kernel Machines*, 34(5):1–41, 2007.

22. Alex Krizhevsky, Ilya Sutskever, and Geoffrey E. Hinton. Imagenet classification with deep convolutional neural networks. In *Advances in Neural Information Processing Systems*, pages 1097–1105, 2012.

23. Kaiming He, Xiangyu Zhang, Shaoqing Ren, and Jian Sun. Deep residual learning for image recognition. In *Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition*, pages 770–778, 2016.

24. Andrej Karpathy and Li Fei-Fei. Deep visual-semantic alignments for generating image descriptions. In *Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition*, pages 3128–3137, 2015.

25. Yann LeCun, Yoshua Bengio, et al. Convolutional networks for images, speech, and time series. *The Handbook of Brain Theory and Neural Networks*, 3361:, 1995.

26. CNNs are a huge and interesting area. The textbook by Goodfellow et al. [2016] is a good place to learn more.

27. Tomas Mikolov, Ilya Sutskever, Kai Chen, Greg S. Corrado, and Jeff Dean. Distributed representations of words and phrases and their compositionality. In *Advances in Neural Information Processing Systems*, pages 3111–3119, 2013.

28. Sepp Hochreiter and Jürgen Schmidhuber. Long short-term memory. *Neural Computation*, 9(8):1735–1780, 1997.

29. For example, the new *Capsule* networks of Sabour et al. [2017] replace the max-pooling of CNNs with more structured summarization functions.

30. If $\Gamma = [\omega_1 \cdots \omega_p]$, then $\nabla \mathcal{L}(\Omega) = [\partial \mathcal{L} / \partial \omega_1 \cdots \partial \mathcal{L} / \partial \omega_p]$. The *Hessian* matrix, $\nabla^2 \mathcal{L}$, has elements $[\nabla^2 \mathcal{L}]_{jk} = \partial \mathcal{L}^2 / \partial \omega_j \partial \omega_k$.

31. David E. Rumelhart, Geoffrey E. Hinton, Ronald J. Williams, et al. Learning representations by back-propagating errors. *Cognitive Modeling*, 5(3):1, 1988.

32. Herbert Robbins and Sutton Monro. A stochastic approximation method. *The Annals of Mathematical Statistics*, pages 400–407, 1951.

33. You can actually get away with biased gradients. In Hartford et al. [2017], we find that trading bias for variance can actually improve performance. But this is tricky business, and in any case the bias must be kept very small.

34. Olivier Bousquet and Léon Bottou. The tradeoffs of large scale learning. In *Advances in Neural Information Processing Systems*, pages 161–168, 2008.

35. Moritz Hardt, Ben Recht, and Yoram Singer. Train faster, generalize better: Stability of stochastic gradient descent. In *International Conference on Machine Learning*, pages 1225–1234, 2016.

36. Panagiotis Toulis, Edoardo Airoldi, and Jason Rennie. Statistical analysis of stochastic gradient methods for generalized linear models. In *International Conference on Machine Learning*, pages 667–675, 2014.

37. John Duchi, Elad Hazan, and Yoram Singer. Adaptive subgradient methods for online learning and stochastic optimization. *Journal of Machine Learning Research*, 12:2121–2159, 2011.

38. Diederik Kingma and Jimmy Ba. Adam: A method for stochastic optimization. In *3rd International Conference on Learning Representations (ICLR)*, 2015.

39. Nitish Srivastava, Geoffrey E. Hinton, Alex Krizhevsky, Ilya Sutskever, and Ruslan Salakhutdinov. Dropout: A simple way to prevent neural networks from overfitting. *Journal of Machine Learning Research*, 15(1):1929–1958, 2014.

40. This seems to contradict the earlier discussion about minimizing the variance of gradient estimates. The distinction is that we want to minimize variance because of noise in the data, but here we are introducing noise in the parameters *independent* of the data.

41. Alex Kendall and Yarin Gal. What uncertainties do we need in Bayesian deep learning for computer vision? *arXiv:1703.04977*, 2017.

42. It is a strange variational distribution, but basically the posterior distribution over $\Omega$ becomes that implied by $W$, with elements $\omega_{i}$ multiplied by random Bernoulli noise.

43. This application, on the news website *nysn.com* with headlines rather than ads, motivates much of the RL work in Agarwal et al. [2014].

44. William R. Thompson. On the likelihood that one unknown probability exceeds another in view of the evidence of two samples. *Biometrika*, 25:285–294, 1933.

45. For example, Matt Taddy, Herbert K.H. Lee, Genetha A. Gray, and Joshua D. Griffin. Bayesian guided pattern search for robust local optimization. *Technometrics*, 51(4):389–401, 2009.

46. Volodymyr Mnih, Koray Kavukcuoglu, David Silver, Andrei A. Rusu, Joel Veness, Marc G. Bellemare, Alex Graves, Martin Riedmiller, Andreas K. Fidjeland, Georg Ostrovski, Stig Petersen, Charles Beattie, Amir Sadik, Ioannis Antonoglou, Helen King, Dharshan Kumaran, Daan Wierstra, Shane Legg, and Demis Hassabis. Human-level control through deep reinforcement learning. *Nature*, 518(7540):529–533, 2015.

47. An exception to this is web search, which is a compelling real-world problem that has been effectively solved through AI.

48. As another example of AI moving into new domains, at the end of 2017 researchers from Carnegie Mellon built an AI system to beat human champions of Texas Hold ’em poker. Poker has explicit rules, but unlike Go or *Ms. Pac-Man*, it is a game of uncertainty and *imperfect* information. Brown and Sandholm [2017] use game theory to break a poker game into various subproblems.

49. For example, Daniel McFadden. Econometric models for probabilistic choice among products. *Journal of Business*, pages S13–S29, 1980; James J. Heckman. Sample selection bias as a specification error (with an application to the estimation of labor supply functions), 1977; and Angus Deaton and John Muellbauer. An almost ideal demand system. *The American Economic Review*, 70:312–326, 1980.
