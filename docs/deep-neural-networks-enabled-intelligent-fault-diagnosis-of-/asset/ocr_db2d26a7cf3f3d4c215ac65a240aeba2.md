# 44 Deep Neural Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

Figure 3.1, $v$ represents the visible layer, $i$ is the $i$-th visible unit, $h$ is the hidden layer, and $j$ is the $j$-th hidden unit. Connections between these two units are undirected. An energy function is proposed to describe the joint configuration $(v, h)$ between them, which is expressed as:

```
$$E(v,h) = \sum_{i\text{visible}} a_i v_i - \sum_{j\text{hidden}} b_j h_j - \sum_{i,j} v_i h_j w_{ij}.$\quad (3.1)$
```

Here, $v_i$, and $h_j$ represent the visible unit $i$ and hidden unit $j$, respectively; $a$ and $b_j$ are their biases. $w_{ij}$ denotes the weight between these two units. Therefore, the joint distribution of this pair can be obtained using the energy function where $	heta$ is the model parameter set containing $a, b$, and $w$:

```
$$p(v,h) = \frac{1}{Z(\theta)} \exp(-E(v,h)),$\quad (3.2)$
```

```
$$Z(\theta) = \sum_{v} \sum_{h} \exp(-E(v,h)).$\quad (3.3)$
```

Due to the particular connections in RBM model, it satisfies conditional independence. Therefore, conditional probability of this pair of layers can be written as:

```
$$p(h|v) = \prod_i p(h_i|v),\quad (3.4)$
```

```
$$p(v|h) = \prod_j p(v_j|h).$\quad (3.5)$
```

Mathematically,

```
$$p(h_j=1|v) = \sigma(b_j + \sum_i v_i w_{ij}),$\quad (3.6)$
```

```
$$p(v_i=1|h) = \sigma(a_i + \sum_j h_j w_{ij}),$\quad (3.7)$
```

where $\sigma(x)$ is the activation function. Generally, $\sigma(x) = 1/(1 + \exp(-x))$ is adopted.

Training Strategy of RBM

In order to set the model parameters, RBM needs to be trained using training dataset. In the procedure of training an RBM model, the learning rule of stochastic gradient