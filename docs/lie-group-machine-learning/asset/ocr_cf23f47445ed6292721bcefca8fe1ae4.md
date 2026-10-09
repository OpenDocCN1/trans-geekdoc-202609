must satisfy

```
$\alpha_i \{y_i (v \cdot x + b) - 1\} = 0, \quad i = 1, 2, \dots, n \quad (9.50)$
```

From (9.47), the samples of $\alpha_i = 0$ have no effect on the classification, and only the samples of $\alpha_i > 0$ can affect the classification. These samples support the optimal segmentation hyperplane, and these samples are called support vectors. At this point, we can get the final classification function as

```
$f(x) = \sum_{i=1}^{n} y_i \alpha_i (x \cdot x_i) + b^* \quad (9.51)$
```

The category attribution of the unknown sample is determined according to the symbol of $f(x)$.

# 9.5.1.2 Analysis of SVM in linearly inseparable cases

When the sample set is linearly inseparable, the sample set can be mapped to the high-dimensional feature space $F$, and the inner product can be realised by using the function satisfying a certain condition of the original space in $F$. The nonlinear classification problem of the original space is transformed into the linear classification problem of the target space. According to the relevant theory of functional analysis, as long as a kernel function satisfies the Mercer condition [59], it corresponds to the inner product in a certain space. Therefore, simply selecting the appropriate inner product function can solve this linearly inseparable problem. The objective function at this time is

```
$\max V(\alpha) = \sum_{i=1}^{n} \alpha_i - \frac{1}{2} \sum_{i,j=1}^{n} \alpha_i \alpha_j y_i y_j K(x_i \cdot x_j) \quad (9.52)$
```

and its corresponding classification function is

```
$f(x) = \sum_{i=1}^{n} y_i \alpha_i K(x \cdot x_i) + b^* \quad (9.53)$
```

# 9.5.2 The principle of KFDA

The kernel method [54] is a very useful computational theory that was originally used in SVM [55, 56]. It is widely used in existing linear algorithms, such as the kernel-based KPCA algorithm [57], kernel-based KICA algorithm [58], and KFDA algorithm. Next, we focus on the KFDA algorithm [31].

Because the FDA algorithm can only deal with linearly separable data, the classification performance is greatly degraded for other non-linear distributions or unknown complex distributions. For example, for the classification of the six distribution samples in Figure 9.8, the linear FDA algorithm cannot handle separating the asterisk sample from the plus sample, because it can never find a straight line to these samples after projection to the line while maintaining a good distinction.