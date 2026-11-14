# ## 9.7 Inference as optimization

In this section, we discuss how to perform posterior inference by solving an optimization problem, which is often computationally simpler. See also Supplementary Section 9.3.

# ### 9.7.1 Inference as backpropagation

In this section, we discuss how to compute posterior marginals in a graphical model using automatic differentiation. For notational simplicity, we focus on undirected graphical models, where the joint can be represented as an exponential family (Section 2.4) follows:

\( p(\mathbf{x}) = \frac{1}{Z} \prod_c \psi_c(\mathbf{x}_c) = \exp(\sum_c \boldsymbol{\eta}_c^\mathsf{T} \mathcal{T}(\mathbf{x}_c) - \log A(\boldsymbol{\eta})) = \exp(\boldsymbol{\eta}^\mathsf{T} \mathcal{T}(\mathbf{x}) - \log A(\boldsymbol{\eta})) \quad \text{(9.93)} \)

where \(\psi_c\) is the potential function for clique \(c\), \(\boldsymbol{\eta}_c\) are the natural parameters for clique \(c\), \(\mathcal{T}(\mathbf{x}_c)\) are the corresponding sufficient statistics, and \(A = \log Z\) is the log partition function.

We will consider pairwise models (with node and edge potentials), and discrete variables. The natural parameters are the node and edge log potentials, \(\boldsymbol{\eta} = (\{\eta_{s;j}\}, \{\eta_{st;j,k}\})\), and the sufficient statistics are node and edge indicator functions, \(\mathcal{T}(\mathbf{x}) = (\{\mathbb{I}(x_s=j)\}, \{\mathbb{I}(x_s=j, x_t=k)\})\). (Note: we use \(s,t \in \mathcal{V}\) to index nodes and \(j,k \in \mathcal{X}\) to index states.)

The mean of the sufficient statistics are given by

\( \boldsymbol{\mu} = \mathbb{E}[\mathcal{T}(\mathbf{x})] = (\{p(x_s=j)\}_s, \{p(x_s=j, x_t=k)\}_{s \neq t}) = (\{\mu_{s;j}\}_s, \{\mu_{st;jk}\}_{s \neq t}) \quad \text{(9.94)} \)

The key result, from Equation (2.236), is that \(\boldsymbol{\mu} = \nabla_{\boldsymbol{\eta}} A(\boldsymbol{\eta})\). Thus as long as we have a function that computes \(A(\boldsymbol{\eta}) = \log Z(\boldsymbol{\eta})\), we can use automatic differentiation (Section 6.2) to compute gradients, and then we can extract the corresponding node marginals from the gradient vector. If we have evidence (known values) on some of the variables, we simply "clamp" the corresponding entries to 0 or 1 in the node potentials.

The observation that probabilistic inference can be performed using automatic differentiation has been discovered independently by several groups (e.g., [Dar03; PD03; Eis16; ASM17]). It also lends itself to the development of differentiable approximations to inference (see e.g., [MB18]).

# #### 9.7.1.1 Example: inference in a small model

As a concrete example, consider a small chain structured model \(x_1 - x_2 - x_3\), where each node has \(K\) states. We can represent the node potentials as \(K \times 1\) tensors (table of numbers), and the edge potentials by \(K \times K\) tensors. The partition function is given by

\( Z(\boldsymbol{\psi}) = \sum_{x_1, x_2, x_3} \psi_1(x_1)\psi_2(x_2)\psi_3(x_3)\psi_{12}(x_1, x_2)\psi_{23}(x_2, x_3) \quad \text{(9.95)} \)

Let \(\boldsymbol{\eta} = \log(\boldsymbol{\psi})\) be the log potentials, and \(A(\boldsymbol{\eta}) = \log Z(\boldsymbol{\eta})\) be the log partition function. We can compute the single node marginals \(\boldsymbol{\mu}_s = p(x_s=1:K)\) using \(\boldsymbol{\mu}_s = \nabla_{\eta_s} A(\boldsymbol{\eta})\), and the pairwise marginals \(\boldsymbol{\mu}_{s,t}(j,k) = p(x_s=j, x_t=k)\) using \(\boldsymbol{\mu}_{s,t} = \nabla_{\eta_{s,t}} A(\boldsymbol{\eta})\).

We can compute the partition function \(Z\) efficiently use numpy's einsum function, which implements tensor contraction using Einstein summation notation. We label each dimension of the tensors