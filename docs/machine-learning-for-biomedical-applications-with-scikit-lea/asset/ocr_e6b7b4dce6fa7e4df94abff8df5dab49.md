# Machine Learning for Biomedical Applications

1. Forward pass: Using current estimated weights $w_{jk}^{(L,n)}$, predict the activations $a_{jk}^{(L,n)}$ for sample $i$, starting from the first layer

```
$$a_{ik}^{(L,n)} = f_l^{(L)} \left( \sum_{j=0}^{D_l} w_{jk}^{(L,n)} x_{ij} \right) \quad (10.3)$
```

and iteratively moving through the layers $l = 2, \dots, M$

```
$$a_{ik}^{(L,n)} = f_l^{(L)} \left( \sum_{j=0}^{D_l} w_{jk}^{(L,n)} a_{ij}^{(L-1,n)} \right) \quad (10.4)$
```

2. Output errors: Calculate the output errors $\delta_{ik}^{(M,n)}$

$\delta_{ik}^{(M,n)} = a_{ik}^{(M)} - y_{ik}$ for standard regression and binary classification.

3. Backward pass: Moving backwards from layer $M$ towards layer 1,

+   - calculate the propagated errors $\delta_{ij}^{(l,n)}$

```
$$\delta_{ij}^{(l,n)} = \sum_{k=1}^{D_{l+1}} \delta_{ik}^{(l+1,n)} f_{l+1}'(a_{ik}^{(l+1,n)}) \quad l = M-1, \dots, 1; \quad (10.5)$
```

+   - calculate the derivatives with respect to the weights $w_{jk}^{(l,n)}$

```
$$\frac{\partial L_i}{\partial w_{jk}^{(l,n)}} = \delta_{ik}^{(l,n)} \cdot a_{ij}^{(l-1,n)} \quad l = M, \dots, 1; \quad (10.6)$
```

4. Update network weights using the gradient-descent equation (Eq. (3.8)) (or similar):

```
$$w_{jk}^{(l,n+1)} = w_{jk}^{(l,n)} - \eta \frac{\partial L_i}{\partial w_{jk}^{(l,n)}} \quad (10.7)$
```

The weights of the network $w_{jk}^{(l,n)}$ are initialized to small random values to ensure that neurons in each layer learn different information.

# 10.2.4 Exercises

+   1. Define the Rectified Linear Unit (ReLU) activation function. What is the problem with this activation function and how can it be addressed?