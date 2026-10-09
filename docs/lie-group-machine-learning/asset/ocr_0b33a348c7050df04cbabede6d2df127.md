of the data set. In the design of the symplectic group classifier, owing to the particularity of the symplectic group, the data set to be classified must be even-dimensional data. Only in this way can we use the symplectic grouperifier algorithm to classify it.

For the data set classification process, the data set is first pre-processed. The pre-processing takes the feature extraction of the data in the data set and extracts the feature sets that can be used for classification, which can improve the efficiency of the data classification process. Then, the data in the data set is integrated to form a unified data set, including data pattern matching and integration, data conflict or inconsistency processing, redundancy elimination, and other steps, which serve as the foundation for data classification. The general data classification process consists of two steps: first, in a given data set, find a common set of objects to establish a classification model, and then use the obtained model for classification; the data items are mapped to one of the classes. To establish the classification model, a part of the data set $X$ is generally used as the training sample set $X_{e}$ and the remaining part of it is used as the test sample set $X_{t}$. All the samples have a known class identifier. The classification algorithm forms a feature description by analysing $X_{e}$ and establishes a classification model. Further, $X_{t}$ is used to test the model classification accuracy; if the obtained accuracy is acceptable, the corresponding classification model can be used to classify future data [29].

According to the above process, this section describes the design process of the symplectic group classifier in data set classification. In the feature extraction stage, the data set to be classified is represented in the form of a symplectic group Sp(2n). Special attention is paid to the fact that the data in the data set in the form of the symplectic group must be even-numbered; otherwise, it cannot be expressed as a symplectic group. The 2n-dimensional data is represented as a sequence of (x₁, x₂, …, x₂ₙ), and the sequence is then divided into two n-dimensional vectors, $u = [x_{1}, \dots, x_{n}]^{T}, v = [y_{1}, \dots, y_{n}]^{T}$. Finally, two vectors are constructed into the symplectic inner product:

```
$\omega(u, v) = u^{T}Jv^{t}$
```

where

```
$J = \begin{bmatrix} 0 & I_{n} \\ -I_{n} & 0 \end{bmatrix} .$
```

Here, the 2n-dimensional data set is represented in a symplectic space. In this symplectic space, for the symplectic matrices consisting of two vectors in the data set, we use the matrix simplification method described in Section 3.2.1 and the method of symplectic transformation to reduce the symplectic matrix and obtain the singular eigenvalues of the matrices. The resulting singular values are arranged in the singular vector $[\lambda_{1}, \lambda_{2}, \dots, \lambda, 0, \dots, 0]^{T}$ in descending order. This vector is used as the singu-