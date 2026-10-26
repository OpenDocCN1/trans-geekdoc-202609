
# A Statistical Machine Learning Perspective of Deep Learning: Algorithm, Theory, Scalable Computing

Maruan Al-Shedivat, Zhiting Hu, Hao Zhang, and Eric Xing

Petuum Inc  
&  
Carnegie Mellon University

## Element of AI/Machine Learning

![](img/cb490ed30bca4eda5fbba81c52a2c173_1_0.png)

Task

Model

- Graphical Models
- Nonparametric Bayesian Models
- Large-Margin
- Regularized Bayesian Methods
- Deep Learning
- Spectral/Matrix Methods
- Sparse Coding
- Sparse Structured I/O Regression

Algorithm

- Stochastic Gradient Descent / Backpropagation
- Coordinate Descent
- L-BFGS
- Gibbs Sampling
- Metropolis-Hastings

Implementation

- Mahout (MapReduce)
- MLlib (BSP)
- CNTK
- MxNet
- Tensorflow (Async)
- …

System

Hadoop　　Spark　　MPI　　RPC　　GraphLab　　…

Platform and Hardware

- Network switches
- Infiniband
- Network attached storage
- Flash storage
- Server machines
- Desktops/Laptops
- NUMA machines
- Mobile devices
- GPUs, CPUs, FPGA, TPU
- ARM-powered devices
- RAM
- Flash
- SSD
- Cloud compute (e.g. Amazon EC2)
- IoT networks
- Data centers
- Virtual machines

## ML vs DL

![](img/cb490ed30bca4eda5fbba81c52a2c173_2_0.png)

More, More, More!!

Data

Learning Machine

Predictions

Hypothesis

![](img/cb490ed30bca4eda5fbba81c52a2c173_2_1.png)

input layer

hidden layer 1

hidden layer 2

hidden layer 3

output layer

## Plan

- Statistical And Algorithmic Foundation and Insight of Deep Learning
- On Unified Framework of Deep Generative Models
- Computational Mechanisms: Programming Platforms and Distributed Deep Learning Architectures

## Outline

- Probabilistic Graphical Models: Basics
- An overview of DL components
  - Historical remarks: early days of neural networks
  - Modern building blocks: units, layers, activation functions, loss functions, etc.
  - Reverse-mode automatic differentiation (aka backpropagation)
- Similarities and differences between GMs and NNs
  - Graphical models vs. computational graphs
  - Sigmoid Belief Networks as graphical models
  - Deep Belief Networks and Boltzmann Machines
- Combining DL methods and GMs
  - Using outputs of NNs as inputs to GMs
  - GMs with potential functions represented by NNs
  - NNs with structured outputs
- Bayesian Learning of NNs
  - Bayesian learning of NN parameters
  - Deep kernel learning

## Fundamental questions of probabilistic modeling

- **Representation:** what is the joint probability distr. on multiple variables?

  $P(X_1, X_2, X_3, ..., X_d)$

  - How many state configurations are there?
  - Do they all need to be represented?
  - Can we incorporate any domain-specific insights into the representation?
- **Learning:** where do we get the probabilities from?
  - Maximum likelihood estimation? How much data do we need?
  - Are there any other established principles?
- **Inference:** if not all variables are observable, how to compute the conditional distribution of latent variables given evidence?
  - Computing $P(H|A)$ would require summing over $2^6$ configurations of the unobserved variables

![](img/cb490ed30bca4eda5fbba81c52a2c173_7_0.png)

## The two types of GMs

P(H|V)  
θ = argmax_θ P_θ(V)

- **Directed edges** assign causal meaning to the relationships (Bayesian Networks or Directed Graphical Models)

  P(X₁,X₂,X₃,X₄,X₅,X₆,X₇,X₈) =  
  P(X₁)P(X₂)P(X₃|X₁)P(X₄|X₂)P(X₅|X₂)  
  P(X₆|X₃,X₄)P(X₇|X₆)P(X₈|X₅,X₆)
- **Undirected edges** represent correlations between the variables (Markov Random Field or Undirected Graphical Models)

  P(X₁,X₂,X₃,X₄,X₅,X₆,X₇,X₈) =  
  1/Z exp{E(X₁)+E(X₂)+E(X₁,X₃)+E(X₂,X₄)+E(X₅,X₂)+  
  E(X₃,X₄,X₆)+E(X₆,X₇)+E(X₅,X₆,X₈)}

![](img/cb490ed30bca4eda5fbba81c52a2c173_11_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_11_1.png)

## 云计算概述

云计算（Cloud Computing）是一种基于互联网的计算方式，通过这种方式，共享的软硬件资源和信息可以按需提供给计算机各种终端和其他设备。

云计算是分布式计算、并行计算、效用计算、网络存储、虚拟化、负载均衡、热备份冗余等传统计算机和网络技术发展融合的产物。

- 按需自助服务（On-demand Self-service）
- 广泛网络访问（Broad Network Access）
- 资源池化（Resource Pooling）
- 快速弹性（Rapid Elasticity）
- 可计量服务（Measured Service）

云计算的五大基本特征构成了其核心价值，使得用户能够以更低成本、更高效率地获取计算资源。

### 三种服务模式

| 服务模式 | 英文名称 | 说明 |
| --- | --- | --- |
| 基础设施即服务 | IaaS | 提供虚拟化的计算资源、存储和网络 |
| 平台即服务 | PaaS | 提供开发平台和工具，如操作系统、数据库 |
| 软件即服务 | SaaS | 提供完整的软件应用程序服务 |

> 云计算的核心思想是将大量用网络连接的计算资源统一管理和调度，构成一个计算资源池向用户按需服务。

服务等级协议（SLA）是云计算服务商与用户之间达成的服务标准约定，确保服务质量和可用性达到承诺的水平。

- 1. 公有云（Public Cloud）
- 2. 私有云（Private Cloud）
- 3. 混合云（Hybrid Cloud）

企业根据成本和安全性需求选择合适的部署模型，其中混合云因兼具灵活性和安全性而越来越受到大型企业的青睐。

## Perceptron and Neural Nets

- From biological neuron to artificial neuron (perceptron)
- From biological neuron network to artificial neuron networks

![](img/cb490ed30bca4eda5fbba81c52a2c173_13_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_13_1.png)

McCulloch & Pitts (1943)

![](img/cb490ed30bca4eda5fbba81c52a2c173_13_2.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_13_3.png)

## Neural Network Model

![](img/cb490ed30bca4eda5fbba81c52a2c173_16_0.png)

Inputs

Age — 34

Gender — 2

Stage — 4

Weights: .6, .2, .1, .3, .7, .2

Hidden Layer

Weights: .5, .8

Output

0.6

> “Probability of being Alive”

Independent variables

Weights

Weights

Dependent variable

Prediction

## Backpropagation:  
Reverse-mode differentiation

- Artificial neural networks are nothing more than complex functional compositions that can be represented by **computation graphs**:

![](img/cb490ed30bca4eda5fbba81c52a2c173_21_0.png)

## Backpropagation:  
Reverse-mode differentiation

![](img/cb490ed30bca4eda5fbba81c52a2c173_22_0.png)

- Artificial neural networks are nothing more than complex functional compositions that can be represented by computation graphs:
- By applying the chain rule and using reverse accumulation, we get

  $$\frac{\partial f_n}{\partial x} = \sum_{i_1 \in \pi(n)} \frac{\partial f_n}{\partial f_{i_1}} \frac{\partial f_{i_1}}{\partial x} = \sum_{i_1 \in \pi(n)} \frac{\partial f_n}{\partial f_{i_1}} \sum_{i_2 \in \pi(i_1)} \frac{\partial f_{i_1}}{\partial f_{i_2}} \frac{\partial f_{i_1}}{\partial x} = \dots$$
- The algorithm is commonly known as backpropagation
- What if some of the functions are stochastic?
- Then use stochastic backpropagation!  
  (to be covered in the next part)
- Modern packages can do this automatically (more later)

## Modern building blocks of deep networks

- Activation functions
  - Linear and ReLU
  - Sigmoid and tanh
  - Etc.
- Layers
  - Fully connected
  - Convolutional & pooling
  - Recurrent
  - ResNets
  - Etc.

![](img/cb490ed30bca4eda5fbba81c52a2c173_24_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_24_1.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_24_2.png)

source: colah.github.io

![](img/cb490ed30bca4eda5fbba81c52a2c173_24_3.png)

## Modern building blocks of deep networks

- Activation functions
  - Linear and ReLU
  - Sigmoid and tanh
  - Etc.
- Layers
  - Fully connected
  - Convolutional & pooling
  - Recurrent
  - ResNets
  - Etc.
- Loss functions
  - Cross-entropy loss
  - Mean squared error
  - Etc.

Putting things together:

![](img/cb490ed30bca4eda5fbba81c52a2c173_25_0.png)

(a part of GoogleNet)

## Outline

- Probabilistic Graphical Models: Basics
- An overview of the DL components
  - Historical remarks: early days of neural networks
  - Modern building blocks: units, layers, activation functions, loss functions, etc.
  - Reverse-mode automatic differentiation (aka backpropagation)
- Similarities and differences between GMs and NNs
  - Graphical models vs. computational graphs
  - Sigmoid Belief Networks as graphical models
  - Deep Belief Networks and Boltzmann Machines
- Combining DL methods and GMs
  - Using outputs of NNs as inputs to GMs
  - GMs with potential functions represented by NNs
  - NNs with structured outputs
- Bayesian Learning of NNs
  - Bayesian learning of NN parameters
  - Deep kernel learning
