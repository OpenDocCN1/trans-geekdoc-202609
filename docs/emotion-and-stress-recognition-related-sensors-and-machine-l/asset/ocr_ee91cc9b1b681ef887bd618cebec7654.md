```
$L_{Weighted-softmax} = -\sum_{i=1}^{m} W_i \log(\hat{p}_i)$
```

where $m$ is the number of training samples in the softmax batch (i.e., the batch size), $y_i$ is the class label of the $i^{th}$ training sample, $W_i$ denotes the weight assigned to the class where the label $y_i$, and $\hat{p}_i$ is the softmax-predicted probability of the $i^{th}$ sample.

Although weighted-softmax loss is also able to tackle the imbalanced dataset, it has some limitations. Since weighted loss assigns less weight to the conventional softmax loss, it is incapable of handling not only high inter-class similarity but also high intra-class variations.

# 3.3.2. Review of Center Loss

Center loss [20] can be incorporated with conventional softmax loss to reduce the intra-class variations by compressing samples towards their corresponding center class in the feature space during training. Center loss for the $i^{th}$ training sample is:

```
$L_{Center} = \frac{1}{2} ||\mathbf{x}_i - \mathbf{c}_i||^2$
```

where $L_{Center}$ denotes the center $\mathbf{x}_i \in \mathbb{R}^d$ denotes the deep feature of the $i^{th}$ training sample (i.e., taken from the last fully connected layer, before the output layer), and $\mathbf{c}_i \in \mathbb{R}^d$ denotes the center of class label $y_i$; $d$ is the feature dimension.

To train the CNN model, joint supervision of softmax loss and center loss is employed as:

```
$L = L_{Softmax} + \lambda L_{Center}$
```

where $L$ denotes the total loss, $L_{Softmax} = -\sum_{i=1}^{m}\log(\hat{p}_i)$ is the entropy loss and $\lambda$ is a scalar used for balancing the two losses.

Since intra-class similarities are encouraged by the center loss, the centers may move closer to, or even overlap, each other. Furthermore, center loss is not proposed to deal with the imbalanced dataset problem. Due to dataset imbalance, the centers of major emotion classes are frequently updated than those of minor classes, which leads to poor FER performance on the minor classes.

# 3.3.3. The Proposed Weighted-Cluster Loss

To address the limitations of existing loss functions (e.g., weighted-softmax loss and center loss), we propose a new loss called weighted-cluster loss. It effectively tackles the imbalanced data by taking into consideration the imbalanced proportion in the number of samples of emotion class in training. Furthermore, weighted-cluster loss adds a new term to the center loss, which simultaneously pulls the centers of each class apart. This may allow the model to simultaneously handle the high intra-variance and the inter-class similarity in the dataset. The weighted-cluster loss for the $i^{th}$ training sample is given by Equation (4):

```
$L_{Weighted-cluster} = \frac{1}{2}\sum_{i=1}^{m} W_i \frac{||\mathbf{x}_i - \mathbf{c}_i||^2}{\sum_{j=1}^{k} ||\mathbf{x}_j - \mathbf{c}_j||^2} + a$
```

where $W_i$ denotes the weight assigned to the class where the label is $y_i$, $k$ denotes the number of emotion classes, and the constant, $a$, prevents the denominator from equaling 0. In this paper, we set $a=1$.

In Equation (4), the numerator penalizes the distance between the deep feature of the training sample (i.e., taken from the last fully connected layer before the output layer) and its corresponding center, and the denominator penalize the distance between the corresponding center and all other