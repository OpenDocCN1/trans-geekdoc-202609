for example, West [411] for an introduction on graphs). As a consequence, many ANN architectures which can process graphs as inputs, so-called graph neural networks (GNNs), have been introduced in the literature.

+   - We refer, for instance, to [362, 415, 439, 442] for overview articles on GNNs,

+   - we refer, for example, to [166, 366] for foundational articles for GNNs,

+   - we refer, for instance, to [399, 426] for applications of attention mechanisms (cf. Section 1.7.2 above) to GNNs,

+   - we refer, for example, to [55, 95, 412, 424] for GNNs involving convolutions on graphs, and

+   - we refer, for instance, to [16, 151, 361, 368, 414] for applications of GNNs to problems from the natural sciences.

# ### 1.7.4 Neural operators

In this section we review a few popular ANN-type architectures employed in operator learning. Roughly speaking, in operator learning one is not interested in learning a map between finite dimensional euclidean spaces, but in learning a map from a space of functions to a space of functions. Such a map between (typically infinite-dimensional) vector spaces is usually called an operator. An example of such a map is the solution operator of an evolutionary PDE which maps the initial condition of the PDE to the corresponding terminal value of the PDE. To approximate/learn operators it is necessary to develop parametrized families of operators, objects which we refer to as neural operators. Many different architectures for such neural operators have been proposed in the literature, some of which we now list in the next paragraphs.

One of the most successful neural operator architectures are so-called Fourier neural operators (FNOs) introduced in Li et al. [271] (cf. also Kovachki et al. [252]). Very roughly speaking, FNOs are parametric maps on function spaces, which involve transformations on function values as well as on Fourier coefficients. FNOs have been derived based on the neural operators introduced in Li et al. [270, 272] which are based on integral transformations with parametric integration kernels. We refer, for example, to [53, 251, 269, 410] and the references therein for extensions and theoretical results on FNOs.

A simple and successful architecture for neural operators, which is based on a universal approximation theorem for neural operators, are the deep operator networks (deepONets) introduced in Lu et al. [284]. Roughly speaking, a deepONet consists of two ANN s that take as input the evaluation point of the output space and input function values at predetermined "sensor" points respectively, and that are joined together by a scalar product to produce the output of the deepONet. We refer, for instance, to [115, 167, 249, 261, 276, 297, 335, ...