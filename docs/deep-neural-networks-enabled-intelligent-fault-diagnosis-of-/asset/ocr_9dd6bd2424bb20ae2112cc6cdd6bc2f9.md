# Neural Architecture Search for Intelligent Fault Diagnosis ■ 141

row of this matrix represents a mixed edge. The symbol $\otimes$ is defined by the interaction of the matrix and the search space.

The searching process can be regarded as a bi-level optimization problem, as shown in the following equation:

```
$A^* = \arg\min L_{val}(w^*(A), A)$
s.t. $w^*(A) = \arg\min L_{train}(w, A)$ $\quad$(8.2)
```

$w^*$ is the convolutional weights of OP under fixed $A$, and $A^*$ denotes the optimized sampling matrix. The search phase of DARTS is reduced to the optimization of the matrix $A$. The final searched architecture is derived by selecting the operator with the maximum coefficient from each row of the matrix.

# BDAS-BASED INTELLIGENT FAULT DIAGNOSIS

A schematic overview of our proposed BDAS method for domain matching fault diagnosis is described in Figure 8.1. It consists of four steps: data acquisition, training the hypernetwork, searching the matching network, and inference. The aerogene bevel gear fault data in the training dataset are collected, and divided into train dataset, validation dataset, and test dataset. The hyper-network is trained based warmup and path-dropout to obtain an intuitive fault proxy. After, the variational inference is used to extend each point of the sampling matrix to a distribution and a scale mixture is used to softly constrain the matching stage. Finally, the matching network can be sampled and ordered from the posterior distributions group by analyzing the inference results.

![](bbox=[0.105, 0.631, 0.894, 0.873])

Figure 8.1 An overview of the proposed method for domain matching fault diagnosis.