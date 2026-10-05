# Article

https://doi.org/10.1038/s41726-020-01063-x

More broadly, our framework can serve as a paradigm for efficient reconstruction. Having the flexibility allows for more diverse scenarios and exploration. Moreover, other methods, such as gradient-based optimization, could integrate seamlessly with our framework to improve the reconstruction accuracy and enhance the robustness of models. The fact that our work only scratches the flat surface for sparse sensing, can be extended to tackle reconstruction in three-dimensional volumetric spaces. Further, by incorporating manifold strategies, we aim to unlock the potential for reconstruction on manifolds in future.

reconstruction performance. The differentiable operator is designed to acquire reconstructions on arbitrary locations and compute derivatives. With our approach, the learning framework enables the differentiability of the operator with respect to the placement. This use of gradient-based optimization techniques to perform the framework, by solving the optimization task in equation (1), opens a new pathway toward NN-based models, advancing the SOTA

# Methods

# Differentiable learning framework

NN-based reconstruction methods according to different tasks can be divided into two categories, which methods are either end-to-end like MLP and FCN or decoder-based. In the latter, the decoder, represented as $\mathcal{G}_{	heta}(s_i, x_i)$, is differentiable with respect to $	heta, s_i$ and $x_i$. Here, $x_i$ represents the query locations, which correspond to all global coordinates in our global framework.

# Validation of framework

The proposed framework is validated on six NN-based models, including MLP, PODN, FCN, GAN and SiN. We summarize the conceptual flow of our methods, and the detailed descriptions are as follows:

MLP. A representative work is to use a MLP for fluid reconstruction, demonstrating superior performance characteristics without having reprocessing the raw data. Following the related work, we use the MLP-based model to validate the proposed framework for global fluid reconstruction (Supplementary Fig. 1-C). The MLP extracts key features of observations through several fully connected layers

```
$u^{(L)}(s) = \sigma(W^{(L)}\sigma(W^{(L-1)}(\dots + W^{(1)}s + b^{(1)})\dots) + b^{(L)}); \quad (11)$
```

where $\sigma$ denotes the activation function, and the decoder contains the weights $W^{(l)}$ and biases $b^{(l)}$. The training dataset $\mathcal{D} = \{s_i, u_i\}_i$ consists of pairs of observations and reconstructions. With sufficient dataset, we aim to learn a loss function $\mathcal{L}(u, \hat{u}, 	heta)$ as a class of CNNs. The learning process of this MLP is mathematically formulated as

PODN. Reduced-order model using PODN is a well-established and widely used class of reduced-order model techniques for fluid reconstruction—it is used to perform online prediction to reduce the computational cost of high-dimensional simulations. Furthermore, proper orthogonal decomposition (POD) models are derived from a set of snapshots (snapshots) and NN is used to learn the mapping between observations and POD coefficients.

```
$	heta^* \in \arg\min_{\theta} \sum_i ||a_i - a(s_i)||^2; \quad (12)$
```

The forward pass reconstructs global fluid fields based on limited observations, providing the best model parameters for the current placement. By default, uniform placement is used as the initial sensors for the first model. Then, through iterations, random adaptive placement strategies are used to update the locations.

The reverse process minimizes sensors locations and provides deployment for the forward process. Given the best model parameters $	heta^*$ is used to calculate the gradient information, derivative of objective function with respect to placement $s$. Consequently, automatic update of placement is performed for each iteration $\gamma_t$. In this process, the gathering operator calculates the derivative of $s$ with respect to $x_i$, which is $\frac{\partial \mathcal{L}}{\partial x_i} = \frac{\partial \mathcal{L}}{\partial s} \frac{\partial s}{\partial x_i}$.

PODN is utilized to validate the proposed framework (Supplementary Fig. 1-2). We first collect snapshots such that $u_i = \sum_j a_{ij} \phi_j$, where $u_i$ are the POD models, $\phi_j$ are the singular modes and $a_{ij}$ are the coefficients. The decomposition is obtained with sufficient dataset. Then the training dataset $\mathcal{D} = \{s_i, a_i\}_i$ is constructed. With the training data, we aim to learn a mapping from observations to coefficients: $s \rightarrow a$. The learning process is mathematically formulated as

```
$	heta^* \in \arg\min_{\theta} \sum_i ||a_i - a(s_i)||^2; \quad (13)$
```

```
$x^{(t+1)} = x^{(t)} - \alpha \frac{\partial \mathcal{L}}{\partial x^{(t)}}; \quad (14)$
```

$m^t = \beta m^{t-1} + (1-eta)g^t$, $m^t$ denotes the defined learning rate and $eta$ and $\alpha$ denote the attention rates. A higher learning rate affects the convergence speed (Supplementary Table 2).

Finally, the forward and reverse processes are executed until there is no further improvement in the objective function or the maximum iteration of sensors $N^{max}$. This framework empowers models with differentiable placement optimization to handle The step of update is given by

Once the NN model is trained, it can be used to predict new fields by using input observations. Substituting the estimated coefficients $\hat{a}_i$ into $u_i = \sum_j \hat{a}_{ij} \phi_j$, the solution $u$ is obtained from the linear combination of POD modes.

Nature Intelligence | July 2025 | Pages 1129–1140

1137