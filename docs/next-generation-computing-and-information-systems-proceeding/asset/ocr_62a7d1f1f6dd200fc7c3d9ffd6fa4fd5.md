Finally, adding the mean \(\mu\) to the columns of \(A\) yields the approximate data \([a_1, a_2, \dots, a_n]\). Global linearity limits PCA effectiveness.

Kernel PCA, also known as KPCA is an extension of PCA that incorporates kernel functions commonly used in support vector machines. It allows for the partitioning of data even if they are not linearly separable by leveraging a mapping technique called reproducing kernel Hilbert space. In KPCA observations are transformed into kernel matrices using the method:

```
\(K = k(x, y) = \phi(x)^T \phi(y)\) (11)
```

The kernel function, denoted as \(k(x, y)\) is used to evaluate the relationship, between observations \(x\) and \(y\). The reproducing kernel Hilbert space is where these observations are mapped by the function \(\phi\). Interestingly due to the kernel trick, there's no need to explicitly compute this mapping function. Instead, we only need to calculate the kernel function.

![](bbox=[0.283, 0.292, 0.715, 0.468])

Figure 3. Dataset before dimensionality reduction.

# 3.6 Results and discussion

As mentioned earlier, the pre-processing of the datasets was done before applying the RNN model. The t-SNE also plotted and visualized for multi-dimensional features shown in Figure 4.

![](bbox=[0.185, 0.602, 0.815, 0.9])

Figure 4. Dataset before dimensionality reduction.