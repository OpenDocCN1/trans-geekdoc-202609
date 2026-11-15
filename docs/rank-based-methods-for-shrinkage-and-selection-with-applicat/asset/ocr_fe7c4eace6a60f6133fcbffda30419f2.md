![](bbox=[0.15, 0.1, 0.9, 0.43])

Figure 12.4 Neural network example of back propagation. In this case, \(\beta_3, \beta_{23}\) (upper light back-arrow) and \(\beta_0\) (lower light back-arrow) are to be computed using backprop.

where

```
\(\beta_{\text{matrix}} = \begin{bmatrix} \beta_{11} & \beta_{12} & \beta_{13} \\ \beta_{21} & \beta_{22} & \beta_{23} \\ \beta_{31} & \beta_{32} & \beta_{33} \\ \beta_{41} & \beta_{42} & \beta_{43} \end{bmatrix} .\)
```

These \(z\) values are “activated” in step 2 with relu to produce the \(a\)-vector,

```
\(a = relu(z).\) (12.5.2)
```

The \(a\)-vector is augmented with 1s for the bias term to form the \(a1\)-vector which is multiplied by the \(\beta_{\text{vector}} = (\beta_1, \beta_2, \beta_3, \beta_4, \beta_0)^T\) to produce \(z_{\text{out}}\) and passed through the sigmoid activation function to produce \(y_F\). This is step 3 given by

```
\(z_{\text{out}} = a1^T \beta_{\text{vector}},\) (12.5.3)
```

and step 4 as

```
\(y_F = p(z_{\text{out}}) = \frac{1}{1 + \exp(-z_{\text{out}})}.\) (12.5.4)
```