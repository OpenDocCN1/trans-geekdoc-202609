![](bbox=[0.2, 0.09, 0.85, 0.33])

FIGURE 10.3: A five-layer network, adapted from Nielsen [2015].

Nodes in the interior of the network have a “classical” neural network structure. Suppose that $\eta_{h}(\cdot)$ is the $k$th node in interior layer $h$. This node takes as input a weighted combination of the output of the nodes in the previous layer of the network, layer $h - 1$, and applies a nonlinear transformation to yield the output. For example, the ReLU (for “rectified linear unit”) node is by far the most common functional form used today; it simply outputs the maximum of its input and zero, as shown in Figure 10.4.14 Suppose $z_{ij}^{h-1}$ is the output of node $j$ in layer $h - 1$ for observation $i$. Then the corresponding output for the $k$th node in the $h$th layer can be written as

![](bbox=[0.35, 0.58, 0.72, 0.83])

FIGURE 10.4: The ReLU function.