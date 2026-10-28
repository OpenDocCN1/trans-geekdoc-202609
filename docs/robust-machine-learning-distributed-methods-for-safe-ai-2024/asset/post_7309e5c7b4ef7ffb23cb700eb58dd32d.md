
## Chapter 3
Federated Machine Learning

**Abstract** While presenting the basics of machine learning in the previous chapter, we assumed that we had access to a training sample $\mathcal{S}$ comprising data points that are (independently) drawn from the ground-truth distribution $\mathcal{D}$. We did not, however, explicitly mention how this dataset was collected or stored. A dominant practice in machine learning for many years has been to collect and store *user-generated data* on a single machine, which then uses the data to train a model. Although this approach is effective in training accurate models, it raises serious *privacy* concerns about the utilization of user data. Furthermore, training the model *centrally*, i.e., on a single machine, is becoming increasingly challenging due to the growing size of the models and the amount of data involved in modern machine learning tasks. To circumvent these limitations, a new paradigm has emerged: *federated machine learning*. This learning scheme consists in having several machines train a model in collaboration while keeping their data local. The computational load is distributed over multiple machines, and users can retain control over their local data. This paradigm is also sometimes coined as *collaborative* or simply *distributed* learning. In this chapter, we formalize the problem of federated machine learning in a server-based framework and present how to adapt gradient-descent methods in this context.

## 3.1 Machine Learning as a Distributed Problem

In this section, we first present the typical mathematical framework that characterizes federated machine learning, which is essentially machine learning on a distributed computing architecture. Then, we show how standard gradient-descent methods (such as mini-batch GD and, a fortiori, GD, and SGD) can be adapted to solve the federated machine learning problem.

### 3.1.1 Problem Statement

We consider a system with n machines, hereafter referred as nodes, represented by the set [n] := {1, …, n}. These nodes communicate either indirectly, through means of a central machine (a.k.a., server), or directly, in a peer-to-peer manner, over a network. Each node i has access to m training samples represented by set S_i drawn independently from a distribution D_i defined over X × Y. The resulting local loss function for each node i, denoted by L_i : R^d → R, is given by

```
$$\mathcal{L}_i(\theta) := \frac{1}{m} \sum_{(\mathbf{x},y)\in S_i} \ell\big(h_{\theta}(\mathbf{x}), y\big). \tag{3.1}$$
```

The objective of federated machine learning is to design a distributed algorithm that enables each node to compute a common optimal model θ* ∈ R^d that minimizes the average loss function for all the nodes, i.e., is a solution to

```
$$\min_{\theta\in\mathbb{R}^d} \mathcal{L}(\theta), \text{ where } \mathcal{L}(\theta) := \frac{1}{n} \sum_{i=1}^{n} \mathcal{L}_i(\theta). \tag{3.2}$$
```

### Remark 3.1

For simplicity, we assume that all the nodes have the same number of data points, i.e., m. In general, when nodes have a nonuniform number of training samples, instead of minimizing the average of their local loss functions, we minimize a weighted average, i.e., Σ_{i=1}^n p_i L_i(θ), where p_i's are positive real values such that Σ_{i=1}^n p_i = 1. Usually, if each node i has m_i data points, we choose p_i = m_i / Σ_{i=1}^n m_i. Although we focus on the minimization of the average loss, the results and techniques presented in this book can be easily extended to weighted average loss minimization by simply modifying each local loss function L_i to \tilde{\mathcal{L}}_i = n p_i \mathcal{L}_i.

### Comparison to the Centralized Methodology

The above optimization problem can be solved by simply collecting the respective training samples held by the nodes at a single machine and then implementing one of the centralized machine learning algorithms on the collective training set, e.g., one of the gradient-descent methods presented in Sect. 2.2.1. However, this centralized approach imposes disproportionate computational workload on a single machine and requires nodes to compromise the ownership of their data, which could discourage many nodes from participating in the learning procedure. A distributed machine learning algorithm, presented shortly in Sect. 3.1.2, can solve the optimization problem (3.2) without having the nodes directly share their local training samples. Instead, in a federated machine learning approach, a node i is required to share only information about its local loss function L_i at a finite number of points in the parameter space. Federated learning, however, requires all the nodes to coordinate their local actions during the entire learning procedure. This is unlike the centralized methodology, where the nodes need not participate in the learning procedure themselves, once they have exported their local training samples.

### System Architectures

Two main types of distributed system architecture have been considered: *server-based* and *peer-to-peer*. We illustrate the two architectures in Fig. 3.1. In the server-based architecture, the nodes collaborate through the means of a central coordinator commonly referred to as the server, sometimes called the *parameter server*. Note that the server can also be considered as an abstraction of a cluster of several machines that communicate with the nodes. In the peer-to-peer architecture, the nodes collaborate by communicating directly with each other, on a given network topology. Note that, when $n = 1$, both the peer-to-peer and the server-based architectures can easily be reduced to the centralized case.\footnote{For the server-based architecture, reducing the problem to the centralized setting when $n=1$ requires merging the server and the node into a single machine.} Accordingly, all the results we present in the remainder of this chapter immediately extend to the centralized setting. In the subsequent section, we present the simplest, and perhaps the most natural, distributed implementation of mini-batch GD in the server-based architecture. This implementation also easily extends to that of distributed GD and of distributed SGD.

**Remark 3.2** Throughout the rest of the book, we mainly focus on the server-based architecture, owing to its wider utility in practical systems. Some discussion and references pertaining to the peer-to-peer architecture can be found in the chapter notes of Chaps. 3, 4, and 5.

![](img/86043981d34dd325adb0d4b75e402b8d_46_0.png)

### 3.1.2 Distributed Gradient-Descent Methods

The basic operations of a gradient-descent method in the server-based architecture are very similar to those of the centralized setting, except that an iteration in the former proceeds in two phases: the local phase and the global phase. In each iteration t, the server initializes the local phase upon broadcasting its current model θ_t to all the nodes. Each node i computes an estimate g_t^(i) of the gradient of its local loss function L_i at the current model θ_t. The nodes return their respective gradient estimates to the server, thus initiating the second phase. In the global phase, the server updates the current model θ_t to θ_{t+1} by linearly combining θ_t with the average of the local gradients' estimates sent by the nodes. This distributed implementation of a gradient-descent method is illustrated in Fig. 3.2.

### Distributed Mini-batch GD

The implementation of the local phase of a distributed gradient-descent method depends upon the algorithm we intend to implement. In the specific case of the distributed mini-batch GD (DMGD) algorithm, each node queries a batch of data points (at random) from its local dataset and computes the corresponding gradient estimate for the local loss function at the current model. Hence, this gradient is a stochastic estimate of its local loss function. We describe the complete scheme of DMGD below, in Algorithm 4.

![](img/86043981d34dd325adb0d4b75e402b8d_47_0.png)

Fig. 3.2 An iteration of a distributed gradient-descent method with a server
