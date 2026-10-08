# Advanced Deep Learning Techniques in Computational Physics

![](bbox=[0.238, 0.167, 0.762, 0.29])

**FIGURE 5.7**
The architecture of the graph neural network.

exploits the graph convolution network by introducing the aggregating and combination function as the message updating tools. In this research, it is observed that an appropriate MP step $M$ is critical to both the accuracy and the convergence of the framework. After a series of attempts, the MP step $M$ is ultimately designed as $N/21$, where $N$ is defined as the total number of nodes in the graph.

# 5.2.2 Data Generation and Training

After constructing the DL framework, it is of great significance to generate datasets for training. In this chapter, the computation results from the commercial software COMSOL Multiphysics are regarded as the ground truth. In order to guarantee the training efficiency, 32 samples are integrated into the DL architecture, three datasets with diverse geometry shapes are introduced. Correspondingly, three independent experiments are carried out to illustrate the universality of the DL architecture, the performance of the framework. In the first place, the proposed network is utilized to compute the electric potential of an ellipse-shape object. With a graph of 290 nodes, it is used to simulate the high voltage discharge needle. After that, the second example is an oval, which has 172 nodes and is investigated to induce a elliptic collision. The last model to be investigated with a circular hole at the center, which has 226 nodes and is intended to simulate an electromagnetic shielding chamber. All three datasets are assigned with random boundary conditions and sent to the commercial software for training.

With the proposed framework and datasets, it is feasible to start the training process. The work is performed on PyTorch [41], with an Adam optimizer[42]. The loss function is defined as the mean square of the predicted value $\psi(x', y')$ by COMSOL:

```
$L = \sum_{x',y'} \frac{(\psi(x', y') - \psi_0(x', y'))^2}{\psi_0(x', y')^2} (5.25)$
```

where $\psi_0(x', y')$ is obtained by COMSOL as the ground truth.