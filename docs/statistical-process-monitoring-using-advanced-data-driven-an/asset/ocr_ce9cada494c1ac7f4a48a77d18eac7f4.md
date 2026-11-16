sensitivity of representation learned towards the training input, where penalizing promotes the feature space mapping to be contractive in the neighborhood of the training data.

The aim of the training phase of the CAE is to determine parameters \(\theta = \{W, b_h, b_y\}\) for which \(\mathbf{y}\) is the reconstructed version of \(\mathbf{x}\) that minimizes the reconstruction error on a training dataset \(D\), which corresponds to minimizing the objective function:

```
\(\mathcal{J}_{CAE}(\theta) = \sum_{\mathbf{x} \in D} \left( \mathcal{L}(\mathbf{x}, g(f(\mathbf{x}))) + \lambda \| J_f(\mathbf{x}) \|_F^2 \right)\)
```

where \(\mathcal{L}\) refers to the reconstruction error, the cross-entropy loss when the activation function \(s_g\) used is the sigmoid and with inputs \(\mathcal{X} \in [0, 1]\). The term \(\mathcal{L}\) is expressed as follows: \(\mathcal{L}(\mathbf{x}, \mathbf{y}) = -\sum_i \log(y_i) + (1 - x_i) \log(1 - y_i)\). To enforce robustness of the representation \(f(\mathbf{x})\) obtained for a training input \(\mathbf{x}\), the penalization is measured as the Frobenius norm of the Jacobian \(J_f(\mathbf{x})\) of the nonlinear mapping applied to the input. The mapping is contracting the data efficiently and hence the name contractive autoencoder. The central role of the Jacobian term is a mapping filter by ignoring low variations and focusing more on significant representations to allow reconstruction of the training with small errors.

# 6.4.2 Probabilistic models

In this subsection, we present two commonly used energy-based models Boltzmann machine (BM) and restricted Boltzmann machine (RBM) that can be used to build up deep learning models.

# 6.4.2.1 Boltzmann machine

A Boltzmann machine (BM) is a stochastic neural network that comprises visible and hidden units, where the visible units are the input data (Fig. 6.11) [66]. In a BM, every unit is connected to all other units. The hidden units act as a set of latent variables (features) allowing BM to model distributions over visible state vectors (Fig. 6.11). The BM model aims to understand the distribution underlying the input data and regenerate the data using that distribution. It is represented by an undirected graph, part of Markov random field, which forms a network of symmetrically connected units (neurons), capable to make stochastic decisions or binary decision (0, 1).

The joint probability distribution of BM, which is an energy-based model, is computed based on an energy function as a Boltzmann distribution [66]:

```
\(P(\mathbf{v}) = \frac{1}{Z(\theta)} \exp(-E(\mathbf{v})),\)
```