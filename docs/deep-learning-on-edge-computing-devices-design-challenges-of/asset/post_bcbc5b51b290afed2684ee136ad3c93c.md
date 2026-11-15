
Network using stochastic computation. Zhang et al. [28] quantitatively analyzed the Convolutional Neural Network (CNN) and implemented the quantized CNN using the FPGA device. Recently, Gokhale [29] implemented an FPGA-based coprocessor to accelerate deep neural networks for mobile applications. Performed independently from the algorithmic researches, these hardware designs generally adopted different quantization approaches for embedded implementation, which saved memory footprint but resulted in notable loss of classification accuracy. On the other hand, the proposed DANoC system was optimized from algorithm to hardware, which led to over three orders of magnitude of improvement in hardware efficiency without degrading classification accuracy.

## 7.2 Algorithm design and optimization

In this section, we present the proposed hardware-oriented unsupervised deep learning algorithm. As the background knowledge, we first introduce the training algorithm of the famous Deep Belief Network.

### 7.2.1 Deep belief network and restricted Boltzmann machine

A Deep Belief Network (DBN) is constructed by stacking multiple layers of Restricted Boltzmann Machines (RBMs) and using the output of the previous-layer RBM as the input of the next-layer RBM (Fig. 7.1). It is found that the higher-layer RBM tends to encode informative abstraction for classification. A standard RBM consists of two layers of units. First, a matrix \(\mathbf{W} \in \mathbb{R}^{n \times d}\) is defined as the connection weights, where \(w_{ij}\) represents the connection between the visible unit \(v_i\) and the hidden unit \(h_j\). Second, the parameters \(b_j\) and \(c_i\) are the biases for the hidden and visible units, respectively. Given the vector forms of the hidden units \(\mathbf{h}\), the visible units \(\mathbf{v}\), and the biases \(\mathbf{b}\) and \(\mathbf{c}\), the energy of a configuration \((\mathbf{v}, \mathbf{h})\) can be written as

$$
E(\mathbf{v}, \mathbf{h}) = -\mathbf{b}^{\mathbf{T}}\mathbf{h} - \mathbf{c}^{\mathbf{T}}\mathbf{v} - \mathbf{v}^{\mathbf{T}}\mathbf{Wh}.
$$

As in general Boltzmann machines, the probability distributions over the hidden and visible vectors are defined as

$$
p(\mathbf{v}, \mathbf{h}) = \frac{1}{Z} e^{-E(\mathbf{v}, \mathbf{h})}, Z = \sum_{\mathbf{v}, \mathbf{h}} e^{-E(\mathbf{v}, \mathbf{h})}.
$$

Given Eq. (7.2), the marginal probability of the visible vector is

$p(\mathbf{v}) = \frac{1}{Z} \sum_{\mathbf{h}} e^{-E(\mathbf{v}, \mathbf{h})}.$ (7.3)

Since there are no direct connections between two hidden units at the same layer, the hidden units conditioned on **v** are independent of each other. Similarly, the visible units conditioned on **h** are also independent of each other. The units of a binary hidden layer, conditioned on the visible layer, are independent Bernoulli random variables. The binary state $h_j$ of the $j$th hidden unit is set to 1 with probability

$p(h_j = 1 | \mathbf{v}) = \delta(\sum_i w_{ij}v_i + b_j),$ (7.4)

where $\delta(x) = 1/(1 + \exp(-x))$ is the sigmoid activation function. Similarly, if the visible units are binary, then the visible units, conditioned on the hidden layer, are also independent Bernoulli random variables. In this case, the binary state $v_i$ of the $i$th visible unit is set to 1 with probability

$p(v_i = 1 | \mathbf{h}) = \delta(\sum_j w_{ij}h_j + c_i).$ (7.5)

On the other hand, if the visible units have real values, then the visible units, conditioned on the hidden layer, are independent Gaussian random variables defined as

$p(v_i | \mathbf{h}) = \mathcal{G}(\sum_j w_{ij}h_j + c_i, 1),$ (7.6)

where $\mathcal{G}$ represents the Gaussian distribution. Suppose $\boldsymbol{\theta} = \{\mathbf{W}, \mathbf{b}, \mathbf{c}\}$ is the parameter set of the RBM. Since the RBM is a generative model, the parameters can be calculated by performing stochastic gradient descent on the log-likelihood of the training samples [30]. The probability that the network assigns to a sample $\mathbf{v}^{(k)}$ ($k = 1, ..., K$) is given by summing over all possible hidden vectors as

$\arg \min_{\boldsymbol{\theta}} - \sum_k \log( \sum_{\mathbf{h}} e^{-E(\mathbf{v}^{(k)}, \mathbf{h}^{(k)})} ).$ (7.7)

By solving Eq. (7.7) we can calculate the parameters offline and use them to configure the RBM. After training the RBM, the DBN can be built by stacking multiple layers of RBMs trained in a layer-by-layer manner.

### 7.2.2 Adaptive restricted Boltzmann machine

For efficient hardware implementation, a sparsely weighted variant of the RBM was proposed, named the Adaptive RBM (AdaRBM), which adds an extra regularization term in Eq. (7.7) to shrink the weights adaptively. The regularization term is based on a mixed matrix norm defined as

$$
\|\mathbf{W}\|_M = \sum_i (\sum_j |w_{ij}|^2)^{1/2}, \quad (7.8)
$$

where the indices \(i\) and \(j\) are treated differently. It is easy to prove that the mixed norm is a legitimate matrix norm, and it is different from the standard L1 and L2 matrix norms, i.e., \(\|\mathbf{W}\|_{L_1} = \sum_i \sum_j |w_{ij}|\) and \(\|\mathbf{W}\|_{L_2} = (\sum_i \sum_j w_{ij}^2)^{1/2}.\)

The mixed matrix norm defined in Eq. (7.8) adds the vector norms of all rows in a matrix; therefore minimizing the mixed norm reduces the lengths of the matrix rows. It is worth noting that the shrinking process does not apply evenly to all rows. Shorter rows shrink faster than the rows with larger weights in the stochastic gradient descent process. As a result, the weights in short rows tend to shrink to zero after a finite number of iterations. Similarly, minimizing the mixed norm of a transposed matrix \(\mathbf{W}^T\) can reduce the weights in shorter columns to zero. To achieve the maximum compression rate, the AdaRBM attempts to shrink the weight parameters in shorter rows and columns simultaneously by minimizing

$$
\mathcal{R}_s(\mathbf{W}) = \lambda (\gamma \|\mathbf{W}\|_M + (1-\gamma)\|\mathbf{W}^T\|_M), \quad (7.9)
$$

where \(\lambda\) controls the sparsity of the weight parameters, and \(\gamma\) controls the balance between row sparsity and column sparsity. Formally, the AdaRBM training algorithm attempts to shrink the regularization term by incorporating it in the standard RBM of Eq. (7.7) as

$$
\underset{\theta}{\text{arg min}} - \sum_k \log (\sum_{\mathbf{h}} e^{-E(\mathbf{v}^{(k)}, \mathbf{h}^{(k)})}) + \lambda (\gamma \|\mathbf{W}\|_M + (1-\gamma)\|\mathbf{W}^T\|_M). \quad (7.10)
$$

### 7.2.3 Training algorithm

The objective function of Eq. (7.10) is the sum of a log-likelihood term and a regularization term. The derivatives of the log probability and the

### **Algorithm 7.1:** Training algorithm of the Adaptive RBM.

- 1: Given \(\langle v_i h_j \rangle_{\text{model}}\) represents the distribution defined by running a Gibbs chain, the parameters can be updated using the contrastive divergence rule as
  $$w_{ij} \Leftarrow w_{ij} + \epsilon (\langle v_i h_j \rangle_{\text{data}} - \langle v_i h_j \rangle_{\text{model}})$$
  $$b_j \Leftarrow b_j + \epsilon (\langle h_j \rangle_{\text{data}} - \langle h_j \rangle_{\text{model}})$$
  $$c_i \Leftarrow c_i + \epsilon (\langle v_i \rangle_{\text{data}} - \langle v_i \rangle_{\text{model}}),$$
  where \(\epsilon\) is a learning rate, and \(\langle \cdot \rangle_{\text{model}}\) is the expectation over the reconstruction data;

- 2: Update \(w_{ij}\) using the gradient of \(\mathcal{R}_s(\mathbf{W})\) as
  $$w_{ij} \Leftarrow w_{ij} - \lambda (\gamma \frac{w_{ij}}{\alpha + \sqrt{\sum_i w_{ij}^2}} + (1 - \gamma) \frac{w_{ij}}{\alpha + \sqrt{\sum_j w_{ij}^2}}),$$
  where \(\alpha\) is a small constant to avoid zero denominator.

- 3: Check the constraint and repeat the update process until it achieves convergence.

regularization term with respect to the parameters can be expressed as

\(\frac{\partial \log p(\mathbf{v})}{\partial w_{ij}} = \langle v_i h_j \rangle_{\text{data}} - \langle v_i h_j \rangle_{\text{model}} + \frac{\partial \mathcal{R}_s(\mathbf{W})}{\partial w_{ij}}, \quad (7.11)\)

\(\frac{\partial \log p(\mathbf{v})}{\partial b_j} = \langle h_j \rangle_{\text{data}} - \langle h_j \rangle_{\text{model}}, \quad (7.12)\)

\(\frac{\partial \log p(\mathbf{v})}{\partial c_i} = \langle v_i \rangle_{\text{data}} - \langle v_i \rangle_{\text{model}}, \quad (7.13)\)

\(\frac{\partial \mathcal{R}_s(\mathbf{W})}{\partial w_{ij}} = \lambda (\gamma \frac{w_{ij}}{\sqrt{\sum_i w_{ij}^2}} + (1 - \gamma) \frac{w_{ij}}{\sqrt{\sum_j w_{ij}^2}}), \quad (7.14)\)

where \(\langle \cdot \rangle_p\) indicates the expectation of the distribution \(p\). Unfortunately, similarly to the RBM training process, the above equations are not tractable, because the computation of the expectations is very difficult; however, we
