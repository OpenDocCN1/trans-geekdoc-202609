+   24. Andrej Karpathy and Li Fei-Fei. Deep visual-semantic alignments for generating image descriptions. In *Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition*, pages 3128–3137, 2015.

+   25. Yann LeCun, Yoshua Bengio, et al. Convolutional networks for images, speech, and time series. *The Handbook of Brain Theory and Neural Networks*, 3361:, 1995.

+   26. CNNs are a huge and interesting area. The textbook by Goodfellow et al. [2016] is a good place to learn more.

+   27. Tomas Mikolov, Ilya Sutskever, Kai Chen, Greg S. Corrado, and Jeff Dean. Distributed representations of words and phrases and their compositionality. In *Advances in Neural Information Processing Systems*, pages 3111–3119, 2013.

+   28. Sepp Hochreiter and Jürgen Schmidhuber. Long short-term memory. *Neural Computation*, 9(8):1735–1780, 1997.

+   29. For example, the new *Capsule* networks of Sabour et al. [2017] replace the max-pooling of CNNs with more structured summarization functions.

+   30. If $\Gamma = [\omega_1 \cdots \omega_p]$, then $\nabla \mathcal{L}(\Omega) = [\partial \mathcal{L} / \partial \omega_1 \cdots \partial \mathcal{L} / \partial \omega_p]$. The *Hessian* matrix, $
abla^2 \mathcal{L}$, has elements $[\nabla^2 \mathcal{L}]_{jk} = \partial \mathcal{L}^2 / \partial \omega_j \partial \omega_k$.

+   31. David E. Rumelhart, Geoffrey E. Hinton, Ronald J. Williams, et al. Learning representations by back-propagating errors. *Cognitive Modeling*, 5(3):1, 1988.

+   32. Herbert Robbins and Sutton Monro. A stochastic approximation method. *The Annals of Mathematical Statistics*, pages 400–407, 1951.

+   33. You can actually get away with biased gradients. In Hartford et al. [2017], we find that trading bias for variance can actually improve performance. But this is tricky business, and in any case the bias must be kept very small.

+   34. Olivier Bousquet and Léon Bottou. The tradeoffs of large scale learning. In *Advances in Neural Information Processing Systems*, pages 161–168, 2008.

+   35. Moritz Hardt, Ben Recht, and Yoram Singer. Train faster, generalize better: Stability of stochastic gradient descent. In *International Conference on Machine Learning*, pages 1225–1234, 2016.

+   36. Panagiotis Toulis, Edoardo Airoldi, and Jason Rennie. Statistical analysis of stochastic gradient methods for generalized linear models. In *International Conference on Machine Learning*, pages 667–675, 2014.

+   37. John Duchi, Elad Hazan, and Yoram Singer. Adative subgradient methods for online learning and stochastic optimization. *Journal of Machine Learning Research*, 12:2121–2159, 2011.

+   38. Diederik Kingma and Jimmy Ba. Adam: A method for stochastic optimization. In *3rd International Conference on Learning Representations (ICLR)*, 2015.

+   39. Nitish Srivastava, Geoffrey E. Hinton, Alex Krizhevsky, Ilya Sutskever, and Ruslan Salakhutdinov. Dropout: A simple way to prevent neural networks from overfitting. *Journal of Machine Learning Research*, 15(1):1929–1958, 2014.