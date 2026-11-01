
# Neural Network History and Development

## Early Connectionist Models and Convolutional Networks
The work of Hubel and Wiesel inspired many of the early connectionist models of vision (Marr and Poggio, 1976). The neocognitron (Fukushima, 1980; Fukushima and Miyake, 1982), designed as a model of the visual cortex, was essentially a convolutional network in terms of model architecture, although an effective training algorithm for such networks had to wait until Yann LeCun and collaborators showed how to apply back-propagation (LeCun et al., 1995). One of the early commercial successes of neural networks was handwritten digit recognition using convolutional networks (LeCun et al., 1995).

## Recurrent Neural Networks
Recurrent neural networks (RNNs) were commonly proposed as models of brain function in the 1970s, but no effective learning algorithms were associated with these proposals. The method of back-propagation through time appears in the PhD thesis of Paul Werbos (1974), and his later review paper (Werbos, 1990) gives several additional references to rediscoveries of the method in the 1980s. One of the most influential early works on RNNs was due to Jeff Elman (1990), building on an RNN architecture suggested by Michael Jordan (1986). Williams and Zipser (1989) present an algorithm for online learning in RNNs. Bengio et al. (1994) analyzed the problem of vanishing gradients in recurrent networks. The long shortterm memory (LSTM) architecture (Hochreiter, 1991; Hochreiter and Schmidhuber, 1997; Gers et al., 2000) was proposed as a way of avoiding this problem. More recently, effective RNN designs have been derived automatically (Jozefowicz et al., 2015; Zoph and Le, 2016).

## Generalization and Regularization Methods
Many methods have been tried for improving generalization in neural networks. Weight decay was suggested by Hinton (1987) and analyzed mathematically by Krogh and Hertz (1992). The dropout method is due to Srivastava et al. (2014a). Szegedy et al. (2013) introduced the idea of adversarial examples, spawning a huge literature.

## Deep Network Properties and Architecture Search
Poole et al. (2017) showed that deep networks (but not shallow ones) can disentangle complex functions into flat manifolds in the space of hidden units. Rolnick and Tegmark (2018) showed that the number of units required to approximate a certain class of polynomials of n variables grows exponentially for shallow networks but only linearly for deep networks.

White et al. (2019) showed that their BANANAS system could do neural architecture search (NAS) by predicting the accuracy of a network to within 1% after training on just 200 random sample architectures. Zoph and Le (2016) use reinforcement learning to search the space of neural network architectures. Real et al. (2018) use an evolutionary algorithm to do model selection, Liu et al. (2017) use evolutionary algorithms on hierarchical representations, and Jaderberg et al. (2017) describe population-based training. Liu et al. (2019) relax the space of architectures to a continuous differentiable space and use gradient descent to find a locally optimal solution. Pham et al. (2018) describe the ENAS (Efficient Neural Architecture Search) system, which searches for optimal subgraphs of a larger graph. It is fast because it does not need to retrain parameters. The idea of searching for a subgraph goes back to the “optimal brain damage” algorithm of LeCun et al. (1990).

Despite this impressive array of approaches, there are critics who feel the field has not yet matured. Yu et al. (2019) show that in some cases these NAS algorithms are no more efficient than random architecture selection. For a survey of recent results in neural architecture search, see Elsken et al. (2018).

## Unsupervised Learning
Unsupervised learning constitutes a large subfield within statistics, mostly under the heading of density estimation. Silverman (1986) and Murphy (2012) are good sources for classical and modern techniques in this area. Principal components analysis (PCA) dates back to Pearson (1901); the name comes from independent work by Hotelling (1933). The probabilistic PCA model (Tipping and Bishop, 1999) adds a generative model for the principal components themselves. The variational autoencoder is due to Kingma and Welling (2013) and Rezende et al. (2014); Jordan et al. (1999) provide an introduction to variational methods for inference in graphical models.

## Autoregressive Models and Generative Adversarial Networks
For autoregressive models, the classic text is by Box et al. (2016). The Yule–Walker equations for fitting AR models were developed independently by Yule (1927) and Walker (1931). Autoregressive models with nonlinear dependencies were developed by several authors (Frey, 1998; Bengio and Bengio, 2001; Larochelle and Murray, 2011). The autoregressive WaveNet model (van den Oord et al., 2016a) was based on earlier work on autoregressive image generation (van den Oord et al., 2016b). Generative adversarial networks, or GANs, were first proposed by Goodfellow et al., (2015a) and have found many applications in AI. Some theoretical understanding of their properties is emerging, leading to improved GAN models and algorithms (Li and Malik, 2018b, 2018a; Zhu et al., 2019). Part of that understanding involves protecting against adversarial attacks (Carlini et al., 2019).

## Historical Branches
Several branches of research into neural networks have been popular in the past but are not actively explored today. Hopfield networks (Hopfield, 1982) have symmetric connections between each pair of nodes and can learn to store patterns in an associative memory, so that an entire pattern can be retrieved by indexing into the memory using a fragment of the pattern. Hopfield networks are deterministic; they were later generalized to stochastic Boltzmann machines (Hinton and Sejnowski, 1983, 1986). Boltzmann machines are possibly the earliest example of a deep generative model. The difficulty of inference in Boltzmann machines led to advances in both Monte Carlo techniques and variational techniques (see [Section 13.4](#Chapter13-04.xhtml#sec13-4)).

*Sidebar: Hopfield network*
*Sidebar: Boltzmann machine*

## Relationship to Biological Neural Networks
Research on neural networks for AI has also been intertwined to some extent with research into biological neural networks. The two topics coincided in the 1940s, and ideas for convolutional networks and reinforcement learning can be traced to studies of biological systems; but at present, new ideas in deep learning tend to be based on purely computational or statistical concerns. The field of computational neuroscience aims to build computational models that capture important and specific properties of actual biological systems. Overviews are given by Dayan and Abbott (2001) and Trappenberg (2010).

*Sidebar: Computational neuroscience*

## Textbooks, Key Figures, and Publication Venues
For modern neural nets and deep learning, the leading textbooks are those by Goodfellow et al. (2016) and Charniak (2018). There are also many hands-on guides associated with the various open-source software packages for deep learning. Three of the leaders of the field—Yann LeCun, Yoshua Bengio, and Geoff Hinton—introduced the key ideas to non-AI researchers in an influential Nature article (2015). The three were recipients of the 2018 Turing Award. Schmidhuber (2015) provides a general overview, and Deng et al. (2014) focus on signal processing tasks.

The primary publication venues for deep learning research are the conference on Neural Information Processing Systems (NeurIPS), the International Conference on Machine Learning (ICML), and the International Conference on Learning Representations (ICLR). The main journals are Machine Learning, the Journal of Machine Learning Research, and Neural Computation. Increasingly, because of the fast pace of research, papers appear first on `arXiv.org` and are often described in the research blogs of the major research centers.

## Footnotes
[1](#Chapter22-01.xhtml#sup22_1) Automatic differentiation methods were originally developed in the 1960s and 1970s for optimizing the parameters of systems defined by large, complex Fortran programs.
