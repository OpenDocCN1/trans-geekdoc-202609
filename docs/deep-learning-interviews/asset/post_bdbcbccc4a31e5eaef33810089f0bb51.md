
## 8.2.8 Inference

| Parameter | Value |
| --- | --- |
| Initial LR | $0.00001$ |
| Momentum | $0.9$ |
| Batch size | $1024$ |

He then tells you that the learning rate (LR) is constant and suggests amending the training pipeline by adding the following code (8.50):

```
scheduler = optim.lr_scheduler.ReduceLROnPlateau(opt)
```

![](img/574135cb1d7125b50cf484d943cdd676_295_0.png)

What do you think about his idea?

- 6 Provide one reason against the use of the log-loss curve.

### PRB-257 CH.PRB-8.81.

You finished training a face recognition algorithm, which uses a feature vector of 128 elements. During inference, you notice that the performance is not that good. A friend tells you that in computer vision faces are gathered in various poses and perspectives. He therefore suggests that during inference you would augment the incoming face five times, run inference on each augmented image and then fuse the output probability distributions by averaging.

- 1 Name the method he is suggesting.
- 2 Provide several examples of augmentation that you might use during inference.

### PRB-258 CH.PRB-8.82.

Complete the sentence: If the training loss is insignificant while the test loss is significantly higher, the network has almost certainly learned features which are not present in an [...] set. This phenomenon is referred to as [...]

## 8.2.9 Optimization, Loss

### Stochastic gradient descent, SGD

#### PRB-259 CH.PRB-8.83.

What does the term stochastic in SGD actually mean? Does it use any random number generator?

#### PRB-260 CH.PRB-8.84.

Explain why in SGD, the number of epochs required to surpass a certain loss threshold increases as the batch size decreases?

### Momentum

#### PRB-261 CH.PRB-8.85.

How does momentum work? Explain the role of exponential decay in the gradient descent update rule.

#### PRB-262 CH.PRB-8.86.

In your training loop, you are using SGD and a logistic activation function which is known to suffer from the phenomenon of saturated units.

1. Explain the phenomenon.
2. You switch to using the tanh activation instead of the logistic activation, in your opinion does the phenomenon still exist?
3. In your opinion, is using the tanh function makes the SGD operation to converge better?

#### PRB-263 CH.PRB-8.87.

Which of the following statements holds true?

- i In stochastic gradient descent we first calculate the gradient and only then adjust weights for each data point in the training set.
- ii In stochastic gradient descent, the gradient for a single sample is not so different from the actual gradient, so this gives a more stable value, and converges faster.
- iii SGD usually avoids the trap of poor local minima.
- iv SGD usually requires more memory.

### Norms, L1, L2

#### PRB-264 CH.PRB-8.88.

Answer the following questions regarding norms.

1. Which norm does the following equation represent?
   $$ |x_1 - x_2| + |y_1 - y_2| \quad (8.41) $$
2. Which formula does the following equation represent?
   $$ \sqrt{\sum_{i=1}^{n}(x_i - y_i)^2} \quad (8.42) $$
3. When you read that someone penalized the L2 norm, was the Euclidean or the Manhattan distance involved?
4. Compute both the Euclidean and Manhattan distance of the vectors: $x_1 = [6, 1, 4, 5]$ and $x_2 = [2, 8, 3, -1]$.

#### PRB-265 CH.PRB-8.89.

You are provided with a pure Python code implementation of the Manhattan distance function (8.51):

```python
from scipy import spatial
x1 = [6, 1, 4, 5]
x2 = [2, 8, 3, -1]
cityblock = spatial.distance.cityblock(x1, x2)
print("Manhattan:", cityblock)
```

![](img/574135cb1d7125b50cf484d943cdd676_298_0.png)

In many cases, and for large vectors in particular, it is better to use a GPU for implementing numerical computations. PyTorch has full support for GPUs (and it's my favourite DL library ...), use it to implement the Manhattan distance function on a GPU.

#### PRB-266 CH.PRB-8.90.

Your friend is training a logistic regression model for a binary classification problem using the L2 loss for optimization. Explain to him why this is a bad choice and which loss he should be using instead.

# 8.3 Solutions

## 8.3.1 Cross Validation

On the significance of cross validation and stratification in particular, refer to “*A study of cross-validation and bootstrap for accuracy estimation and model selection*” [17].

### CV approaches

#### SOL-177 CH.SOL-8.1.

The first approach is a leave-one-out CV (LOOCV) and the second is a K-fold cross-validation approach.

#### SOL-178 CH.SOL-8.2.

Cross Validation is a cornerstone in machine learning, allowing data scientists to take full gain of restricted training data. In classification, effective cross validation is essential to making the learning task efficient and more accurate. A frequently used form of the technique is identified as K-fold cross validation. Using this approach, the full data set is divided into K randomly selected folds, occasionally stratified, meaning that each fold has roughly the same class distribution as the overall data set. Subsequently, for each fold, all the other (K – 1) folds are used for training, while the present fold is used for testing. This process guarantees that sets used for testing, are not used by a classifier that also saw it during training.

### K-Fold CV

#### SOL-179 CH.SOL-8.3.

True. We never utilize the test set during a K-fold CV process.

#### SOL-180 CH.SOL-8.4.

True. This is the average of the individual errors of K estimates of the test error:
$$ MSE_1, ..., MSE_K \quad (8.43) $$

#### SOL-181 CH.SOL-8.5.

The correct answer is: A 5-fold cross-validation approach results in 5 different model instances being fitted. It is a common misconception to think that in a K-fold approach the same model instance is repeatedly used. We must create a new model instance in each fold.

#### SOL-182 CH.SOL-8.6.

The correct answer is: we compute the **arithmetic mean** over the $K$ performance estimates from the validation sets.

### Stratification

#### SOL-183 CH.SOL-8.7.

The correct answer is: 3-fold CV. A $k$-fold cross-validation is a special case of cross-validation where we iterate over a dataset $k$ times. In each round, we split the dataset into $k$ parts: one part is used for validation, and the remaining $k-1$ parts are merged into a training subset for model evaluation. Stratification is used to balance the classes in the training and validation splits in cases where the corpus is imbalanced.

### LOOCV

#### SOL-184 CH.SOL-8.8.

1. **True**: In LOOCV $K=N$ (the full sample size).
2. **False**: There is no way of a-priori finding an optimal value for $K$, and the relationship between the actual sample size and the resulting accuracy is unknown.

## 8.3.2 Convolution and correlation

### The convolution operator

#### SOL-185 CH.SOL-8.9.

1. This is the definition of a convolution operation on the two signals $f$ and $g$.
2. In image processing, the term $g(t)$ represents a **filtering** kernel.

#### SOL-186 CH.SOL-8.10.

1. True. These operations have two key features: they are shift invariant, and they are linear. Shift invariance means that we perform the same operation at every point in the image. Linearity means that this operation is linear, that is, we replace every pixel with a linear combination of its neighbours.
2. True. See for instance Eq. (8.3).
3. True.

### The correlation operator

#### SOL-187 CH.SOL-8.11.

1. True.
2. True.

#### SOL-188 CH.SOL-8.12.

A convolution operation is just like correlation, except that we flip over the filter both horizontally and vertically before correlating.

$$ f(x,y)\otimes h(x,y)=\sum_{m=0}^{M-1}\sum_{n=0}^{N-1} f^{*}(m,n) h(x+m,y+n) \quad (8.44) $$

### Padding and stride

Recommended reading: “A guide to convolution arithmetic for deep learning” by Vincent Dumoulin and Francesco Visin (2016) [22].
