
| | Mean-squared error | Cross-entropy |
|---|---|---|
| Loss | $\frac{1}{2}(T-O)^2$ | $-T \log O - (1-T) \log(1-O)$ |
| Error $\delta$ | $O(1-O)(O-T)$ | $O-T$ |

**FIGURE 10.17**
A comparison between cross-entropy and mean-squared error for binary classification. For the binary classification task, we only need one output unit, and $O$ is the output of the output unit. The last row is the error $\delta$ of the output unit during the backpropagation process with the sigmoid activation function.

![](img/90c930779c8f928df6ff4481fc59f9a3_540_0.png)

Assuming T = 1 (positive tuple)

**FIGURE 10.18**
An illustration of cross-entropy and mean-squared error. Assume the training tuple is a positive tuple (i.e., $T = 1$).

Fig. 10.17 compares mean-squared loss and cross-entropy loss for a neural network with a single output unit with the sigmoid activation function for the binary classification task. As we have analyzed in Section 10.1.2, with the mean-squared error, when the output unit is saturated (e.g., $O \approx 0$ or $O \approx 1$), the error of the output unit $\delta \approx 0$, even if the predicted output does not match the actual output (i.e., large $|T - O|$). Such a gradient vanishing problem can be naturally avoided by the cross-entropy loss. As we can see Fig. 10.17, the error of the output unit $\delta = O - T$ with the cross-entropy loss. Therefore as long as the predicted output deviates from the actual output (i.e., large $|T - O|$), the error will not vanish even if the output unit itself is saturated ($O \approx 0$ or $O \approx 1$). Fig. 10.18 provides a further illustration on how cross-entropy loss avoids the gradient vanishing problem when the output unit is saturated.

For a multiclass classification task, suppose there are $C$ class labels in total. The actual target value $T$ is a binary vector of length $C$: $T = (T_1, T_2, ..., T_C)$, where $T_j = 1$ ($j = 1, ..., C$). If the training tuple belongs to the $j$th class and $T_j = 0$ otherwise. There are $C$ output units, and therefore the predicted target value $O$ is also a vector of length $C$: $O = (O_1, O_2, ..., O_C)$, where $O_j = P(T = j|X)$ ($j = 1, ..., C$). The cross-entropy in this case is defined as follows.

```
\(\text{Loss}(T, O) = - \sum_{j=1}^{C} T_j \log O_j\)
(10.12)
```

## 10.2.6 Autoencoder: unsupervised deep learning

Introducing autoencoder. For the backpropagation algorithm in Fig. 10.4, it requires the actual target value T, which could be the real-valued output for regression problem or the discrete-valued output for classification problem. In other words, the training process is supervised. But, what if there is no such supervision? Can we still use the backpropagation algorithm to train a feed-forward neural network? The answer is yes. Simply put, we set the output layer to share the same number of the input units, and just use the input data x as the target output T = x. Then, we use the backpropagation algorithm to minimize the loss between the predicted output T̂ and the target output T = x. In other words, we aim to use the neural network to reconstruct the input data x. This type of neural network is called autoencoder.

The simplest autoencoder has one hidden layer (see Fig. 10.19(a)), which consists of two parts, including the encoder f and the decoder g. The encoder f corresponds to the hidden layer that maps (i.e., encodes) the input x to its latent representation (or the code of the input) h. The decoder g corresponds to the output layer that maps (i.e., decodes) the latent presentation h to the predicted output T̂. The output layer has the same number of units as the input layer. The goal is to use the predicted output T̂ to reconstruct the input x. This can be done by running the backpropagation algorithm to minimize the disagreement between the predicted output T̂ and the original input x: Loss(x, T̂), where the loss function could be a mean-squared error or a cross-entropy loss. For both the encoder f and the decoder g, we could have multiple layers (Fig. 10.19(b)), and this is called stacked autoencoder.

A major difficulty with autoencoder is that it might simply copy the input to the output. This could happen, for example, if we use the same number of hidden units as the input layer in Fig. 10.19(a) and linear activation function for the hidden layer, which would make the autoencoder useless. To address this issue, we could either constrain the architecture of the autoencoder to require that the hidden layer has less units than the input layer or impose regularization terms on the model parameters (e.g., to

![](img/90c930779c8f928df6ff4481fc59f9a3_541_0.png)

FIGURE 10.19 Autoencoder (a) and stacked autoencoder (b). In both cases, x, h, and T̂ are vectors, and the output layer has the same number of units as the input layer. By minimizing Loss(x, T̂), we aim to reconstruct the input x by the output T̂, where Loss() is the loss function (e.g., mean-squared error, cross-entropy, etc.)

![](img/90c930779c8f928df6ff4481fc59f9a3_542_0.png)

FIGURE 10.20
An illustration of two strategies of applying autoencoder as a dimensionality reduction technique for clustering high dimensional data. For clarity, we assume there is only one encoder layer and one decoder layer.

require the latent representation **_h_** to be sparse), or adopt *denoising training*, where we aim to minimize the loss between the output of the autoencoder and a *perturbed version* of the input.

Autoencoder can be naturally used for unsupervised learning. Next, we give three examples of applying autoencoder for unsupervised learning, including dimensionality reduction, deep clustering and unsupervised pretraining.

### Autoencoder for dimensionality reduction.

The vector **_h_** at the encoder layer can be naturally viewed as a latent representation of the input data **_x_**. If the number of hidden units of the encoder layer is less than the input units, the autoencoder (Fig. 10.19(a)) or stacked autoencoders (Fig. 10.19(b)) effectively performs *dimensionality reduction*. This is conceptually similar to principle component analysis (PCA, introduced in Chapter 2). Indeed, if the decoder uses a linear activation function and mean-squared error as the loss function, the autoencoder in (Fig. 10.19(a)) is equivalent to PCA. By using a nonlinear activation function in the decoder or stacking multiple autoencoders together (Fig. 10.19(b)), (stacked) autoencoder is capable of learning a more powerful low-dimensional representation of the input data than PCA.

### Autoencoder for deep clustering.

In order to cluster high-dimensional data, a natural solution is to find clusters in a low-dimensional space where the clustering structure is more evident than the original space. Generally speaking, there are two strategies, to both of which autoencoder can be applied. See Fig. 10.20 for an illustration.

In the first strategy, we conduct dimensionality reduction, and *then* perform clustering in the low dimensional space. For example, we can first apply autoencoder to the input data (e.g., **_x_** in Fig. 10.19(a)) and the output of its encoder (e.g., **_h_** in Fig. 10.19(a)) provides the representation of the input data in a low-dimensional space. Then, we perform clustering (e.g., by K-means) on the low-dimensional space **_h_**. The advantage of this strategy lies in that the dimensionality reduction is performed as a preprocessing step of the clustering task. Once the low-dimensional space **_h_** is found, we can readily plug in any off-the-shelf clustering algorithm on it. However, since the dimensionality reduction step is conducted *before* the clustering step, the clustering structure of the input data set might become obscured in the low-dimensional space. For example, the two well-separated clusters in the original high-dimensional space might be overlapping with each other in the low-dimensional space, which would in turn impair the quality of the clustering results.

The second strategy aims to integrate the dimensionality reduction and the clustering steps together. In other words, we want to *embed* the dimensionality reduction step into the clustering step, so that the clustering structure of the input data is well preserved in the low-dimensional space. A variety of different dimensionality reduction approaches (e.g., PCA, autoencoder, matrix factorization) and various clustering methods (e.g., K-means, NMF, probabilistic clustering methods) can be adopted in this strategy. When we use a deep learning model (e.g., autoencoder) for the dimensionality reduction step, this strategy is referred to as *deep learning*. Compared with the first strategy, deep clustering often leads to a better clustering quality, at the cost of increased computational cost, owing to the coupling of the dimensionality reduction and clustering steps.

So, how can we integrate dimensionality reduction *and* clustering together? Let us take autoencoder (for the dimensionality reduction step) and K-means (for the clustering step) as an example to explain its key ideas from the optimization perspective.

In autoencoder, we aim to find the best encoder $f$ and decoder $g$ to re-construct the input data. In other words, we wish to minimize the following reconstruction loss

\(\min \sum_{i=1}^N \| \hat{T}_i - \mathbf{x}_i \|_2^2 \quad \text{where} \quad \hat{T}_i = g(f(\mathbf{x}_i)). \quad (10.13)\)

Recall that in k-means (introduced in Chapter 8), we aim to find the best cluster centers $c_j$ ($j = 1, ..., C$) and cluster membership for each input data tuple $\mathbf{x}_i$ ($i = 1, ..., N$) by minimizing another type of loss, namely the sum of squared errors (SSE):

\(\min \sum_{i=1}^N \sum_{\mathbf{x}_i \in c_j} \| \mathbf{x}_i - c_j \|_2^2. \quad (10.14)\)

Now, in order to integrate the dimensionality reduction (Eq. (10.13)) and clustering (Eq. (10.13)) together, we instead aim to simultaneously find the best encoder $f$, the decoder $g$, the cluster centers $c_j$ ($j = 1, ..., C$), and the cluster membership by minimizing a linear weighted sum of the above two types of loss (i.e., the reconstruction loss in Eq. (10.13) and the SSE in Eq. (10.14)):

\(\min \underbrace{\sum_{i=1}^N \| \hat{T}_i - \mathbf{x}_i \|_2^2}_{\text{reconstruction loss}} + \alpha \underbrace{\sum_{i=1}^N \sum_{f(\mathbf{x}_i) \in c_j} \| f(\mathbf{x}_i) - c_j \|_2^2}_{\text{SSE}}, \quad (10.15)\)

where $\hat{T}_i = g(f(\mathbf{x}_i))$, and $\alpha > 0$ is a regularization parameter to balance the relative weight of the two types of loss. Notice that the SSE in Eq. (10.15), we use $f(\mathbf{x}_i)$, that is, the output of the encoder $\mathbf{f}$, instead of the original input data $\mathbf{x}_i$. This is the key that differentiates itself from the first strategy
