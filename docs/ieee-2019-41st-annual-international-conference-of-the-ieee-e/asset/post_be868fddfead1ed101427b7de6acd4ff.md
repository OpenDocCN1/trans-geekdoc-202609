
# S. Tarsyal et al.: Deep Dictionary Learning

# IEEE Access

bi-linear. For example, if the dimensionality of the sample is $m$ and the first dictionary is size $m \times n1$ and the second one is $n1 \times n2$, it is not possible to learn a single dictionary of size $m \times n2$ and expect the same results as a two-stage dictionary.

In general, for nonlinear activation functions, it is not possible to collapse multiple levels of dictionaries into a single level for testing. For the linear activation function, the multiple levels of dictionaries can be collapsed into a single stage by matrix multiplication of the different dictionaries and sparse code features from the fused single dictionary by standard $L1$-minimization.

# Algorithm 3 Testing Algorithm (for Non-Activation Function)

Generate features for first level

```
$Z_{l1} = \min ||X - D_{l1}Z_{l1}||^2$
```

From 2nd to penultimate level

```
$Z_{l2} = \min ||\varphi^{-1}(Z_{l2-1}) - D_{l2}Z_{l2}||^2$
```

For final level

```
$Z_{cm} = \min ||Z_{cm-1} - D_{cm}Z_{cm}||^2 + \lambda ||Z_{cm}||^2$
```

# Algorithm 1 Training Algorithm (for Any Function $\varphi$)

- Initialize: $D_l, i = 1 \dots n$

- For first level: repeat until convergence:

```
$Z_l = \min ||X - D_lZ_l||^2$
```

```
$D_l = \min ||\varphi^{-1}(Z_{l-1}) - D_lZ_l||^2$
```

- From 2nd to penultimate level: repeat until convergence:

```
$Z_l = \min ||\varphi^{-1}(Z_{l-1}) - D_lZ_l||^2$
```

```
$D_l = \min ||\varphi^{-1}(Z_{l-1}) - D_lZ_l||^2$
```

- For final level: repeat until convergence:

```
$Z_l = \min ||\varphi^{-1}(Z_{l-1}) - D_lZ_l||^2 + \lambda ||Z_l||^2$
```

```
$D_l = \min ||\varphi^{-1}(Z_{l-1}) - D_lZ_l||^2$
```

# Algorithm 2 Testing Algorithm (for Linear Activation Function)

- Collapse multiple levels of dictionaries into a single one

```
$D = D_1D_2 \dots D_n$
```

Compute features for the test sample $x_{test}$.

```
$z_{test} = \min ||x_{test} - Dz_{test}||^2 + \lambda ||z_{test}||^2$
```

for dictionary learning, instead of maximizing sparsity, we minimize the Euclidean distance between the data (X) and the synthesis (D,Z). Furthermore, RBM has a stochastic whereas dictionary learning typically uses binary or real values. On the other hand, deep dictionary learning can work on both linear and complex inputs.

Similar to RBM, a combination of the proposed dictionary learning with autoencoders can be performed. The synthesis learning model is expressed as: $X = DZ$ where $D$ is the sparse dictionary and $Z$ are the sparse coefficients. Usually one promotes sparsity in the features and the learning requires minimizing.

```
$||X - DZ||^2 + \lambda ||Z||^2$
```

This is the well-known sparsity prior where the task is to find that one can synthesize/generate signals from sparse features. There are also co-sparse dictionary learning paradigm [65] where the goal is to learn a dictionary when it is applied to the data $D\hat{X} = Z$. The corresponding learning is framed by minimizing

```
$|\hat{X} - D\hat{X}||^2 + \lambda ||D\hat{X}||^2$
```

If we combine analysis and sparsity, using $\hat{X} =$

```
$||\hat{X} - D\hat{X}||^2 + \lambda ||D\hat{X}||^2$
```

If we drop the sparsity term, it becomes

```
$||\hat{X} - D\hat{X}||^2$
```

This is similar to the sparse of dense dictionary with linear activation at the hidden layer. Further, we can express autoencoder in the terminology of dictionary learning – autoencoder is a model that learns the analysis and the synthesis dictionaries. To the best of our

# A. CONNECTION WITH EXISTING ALGORITHMS

In this section, we contrast the proposed deep dictionary approach with some popular dictionary learning algorithms, namely RBM and Autoencoder, and hierarchical dictionary learning. From Figures 1 and 5, it is evident in both RBM and dictionary learning, the task is to learn the network weights/atoms and the representation given the data. They differ from each other in the cost functions used. For RBM it is the Boltzmann function whereas

VOLUME 4, 2016

10101

knowledge, is the first work that shows the architectural similarity between autoencoders and dictionary learning.

We also briefly discuss the challenges with recently proposed dictionary learning algorithms. First, we would like to emphasize that the approach is not related to structural or dictionary learning techniques [66], [67]. In these studies, the proposed goal is to learn dictionary atoms that are related to each other. Generally, these studies follow learning techniques (single level) and the relationships between atoms of dictionary learning.

We next discuss the work on "Double Sparsity" [68] where the authors decompose the dictionary into a part of fixed basis (e.g., wavelet, and DCT) and a set of coefficients; instead of learning the full dictionary (as is in standard dictionary learning), they learn a dictionary that can be represented as a linear combination of fixed basis. The mechanism is formulated as follows: In this formulation, $\Phi = D$; instead of learning the full dictionary, the authors learned to synthesize the dictionary $D$ from a fixed basis $\Phi$. The advantage of this approach is that the learned dictionary has fast and adjoint operators (since it is synthesized from an efficient operator) and is useful for large-scale problems. Clearly, the proposed algorithm is different from Equation (28) [68]. We learned the full dictionary in each level and continue for multiple levels with a goal to learn abstract representations.

- 4. bg-img (smaller subset with random image)
- 5. bg-rot (smaller subset with random rotation)

These datasets are challenging to empirically deep learning algorithms [69]. Samples for each of the datasets are shown in Fig. 8. ![](img/5de391b384cc1d6b5a94c0bae136b4b_6.png)

FIGURE 8. Top to bottom, basic-rot, bg-band, bg-img.

The second database is related to the problem of classifying documents into their corresponding topic. We have used a commonly used 20-new dictionary [70] for the training and test sets collected at different times, a setting that is more of practical application. The training set contains 1,269 samples and the test set includes 7,505. We use many relevant features and follow the same pattern as [51].

# IV. EXPERIMENTAL EVALUATION

The effectiveness of the proposed deep dictionary learning is evaluated on multiple benchmarks from different areas such as images, text, and signals. The results are compared with state-of-the-art algorithms. 

# A. DATASETS

We evaluated the performance on several datasets. The first one is MNIST which consists of $28 \times 28$ digits ranging from 0 to 9. The dataset has 60,000 images for training and 10,000 samples for testing. It is noted that we have not performed any preprocessing on this dataset. Related to matrix learning, MNIST variants are also used which primarily have different training samples (10,000) and a larger number of test samples (60,000) are not used in this work because our method does not require tuning and SAE are already optimized for MNIST. Here is the list of these datasets:

- 1. basic (smaller subset of MNIST)
- 2. basic-rot (smaller subset with random rotations)
- 3. bg-band (smaller subset with uniformly distributed noise in background)

# S. Tariyal et al.: Deep Dictionary Learning

TABLE 1. Deep vs shallow dictionary learning.

| Dataset | Shallow (50) | 1 layer (300) | 2 layer (300-150) | 3 layer (300-150) |
|---|---|---|---|---|
| MNIST | 97.35 | 96.52 | 97.30 | 97.75 |
| basic | 95.02 | 94.39 | 95.27 | 95.80 |
| basic-root | 84.19 | 83.37 | 85.39 | 87.00 |
| bg-round | 87.19 | 86.52 | 87.49 | 89.35 |
| bg-img | 78.86 | 77.56 | 79.20 | 81.00 |
| bg-img-rot | 54.40 | 54.06 | 55.93 | 57.77 |
| 20-newgroup | 60.96 | 65.22 | 68.93 | |
| GTZAN | 76.57 | 75.70 | 79.68 | 83.31 |

![](img/5de391b384cc1d6b5a694c0bae136b4b_7_0.png)

FIGURE 1. First level dictionary learning for MNIST.

# B. EFFECT OF DICTIONARY LEARNING

We analyze the results of the proposed deep dictionary learning and the effect of increasing the number of layers. The objective of this experiment is to show that the representations learned from a single level of dictionary and multi-level dictionaries yield better classification performance. For example, with just one level, we learn 50 atoms for MNIST; 625 atoms for the bg-newgroup and 148 for GTZAN; compared to the last level of deep learning, we performed experiments with up to three levels. For the MNIST database and its variants, the number of atoms in the multi-level dictionaries: 300-150. For the 20-newgroup and the GTZAN (music database), the number of atoms varies from the previous layer. The classifier is performed with a simple K-Nearest Neighbor (K=1). Column 2 shows the results for shallow dictionary and Column 3 shows the results with different levels of deep learning. The results show that for all the databases, deep learning offers improvements over shallow dictionary learning. The improvement in accuracy is possibly owing to more abstract representation learned from layers. Depending on the complexity of the dataset, the difference in performance varies from 0.4% to 9%. Table 2 indicates the first layer dictionary on MNIST database.

Generally, the atoms are initialized by random choices from the training set; this leads to variability. In this research, we propose a deterministic initialization based on the QR decomposition of the dictionary matrix. Orthogonal factors from Q (in order) are used to initialize the dictionary.

We show that multi-level dictionaries cannot be collapsed into a single one and should not be expected to yield the results. The difference between performance of multi-level dictionary learning and single level learning is evident in Table 1; see columns 2 and 5. If the learning is linear, it is possible to collapse multiple

TABLE 2. Comparing the accuracy of DDL with DBN and SAE with KNN (K = 1) Classification.

| Dataset | DDL | DBN | SAE |
|---|---|---|---|
| MNIST | 97.75 | 97.05 | 97.33 |
| basic | 95.80 | 95.37 | 95.25 |
| basic-root | 87.00 | 81.44 | 84.83 |
| bg-round | 89.35 | 78.59 | 85.34 |
| bg-img | 81.00 | 75.22 | 74.99 |
| bg-img-rot | 57.77 | 48.53 | 49.14 |
| 20-newgroup | 70.48 | 70.09 | 67.98 |
| GTZAN | 83.31 | 80.99 | 82.29 |

# C. COMPARISON WITH DEEP LEARNING APPROACHES

Since the proposed deep architecture is inspired by existing deep learning approaches, we have our results with a stacked autoencoder (SAE) and deep belief network (DBN).
