# Deep generative models for recommender systems

![](bbox=[0.215, 0.095, 0.804, 0.603])

Figure 6.7 (a) NCF and (b) RRN

$g(V \cdot r + \mu) + b$, where $g$ is some activation function such as sigmoid and $V$ is the weight matrix and $\mu$ is the activation. The decoder reconstructs the latent representation as $f(W \cdot g(V \cdot r + \mu)) + b$, where $f$ is another activation function and $W$ and $b$ are weights and bias, respectively. The objective function of I-AutoRec is to learn

```
$$\sum_{r\in R} ||r - h(\theta)||^2, \quad h(\theta) = f(W \cdot g(V \cdot r + \mu) + b)$
```

Collaborative filtering neural network [31] further extends AutoRec using DAE. The structure of DAE is the same as shown in Figure 6.6(c), except that the input data is first corrupted with noises and the AE to reconstruct the uncorrupted data. The advantage of using DAE is to alleviate overfitting.