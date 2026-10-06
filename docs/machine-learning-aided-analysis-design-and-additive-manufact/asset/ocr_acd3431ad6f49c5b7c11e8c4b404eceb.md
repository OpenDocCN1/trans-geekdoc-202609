Machine learning aided stochastic vibration analysis of functionally graded porous plates

where $\varepsilon \sim N(0, \delta^2)$. For Gaussian process regression, the relation function $f(\mathbf{x})$ is distributed as a Gaussian process:

```
$f(\mathbf{x}) \sim GP(m(\mathbf{x}), k(\mathbf{x}, \mathbf{x})) \quad (12.15)$
```

where $m(\mathbf{x})$ is the mean equation and $k(\mathbf{x}, \mathbf{x})$ is the covariance equation, with detailed formulations as:

```
$m(\mathbf{x}) = E[f(\mathbf{x})] \quad (12.16)$
```

```
$k(\mathbf{x}, \mathbf{x}') = E[(f(\mathbf{x}) - m(\mathbf{x}))(f(\mathbf{x}') - m(\mathbf{x}'))] \quad (12.17)$
```

where $E(\cdot)$ is the average of all values. The formulation $k$ is named as the kernel of Gaussian process. The appropriate kernel function could smooth the datapoints to higher dimension and provide each with regression training. One typical kernel based on GPR is the radial basis function kernel, which is presented as:

```
$k(\mathbf{x}, \mathbf{x}') = \sigma_f^2 \exp(-\frac{\|\mathbf{x}-\mathbf{x}'\|^2}{2\lambda^2}) \quad (12.18)$
```

where $\lambda$ is the length-scale hyperparameter and $\sigma_f^2$ is the signal variance parameter, which are adopted to enhance and promote the promotion of the resulting equation. Based on the mean and kernel function selected, the Gaussian process can be implemented to obtain the priori formulation values between the input–output points.

# 12.4.3 The extended support vector regression

The SVR which was proposed by Vapnik [15] has been popular over the past decades, exhibiting excellent ability in data pattern and regression fields. Subsequently, success of distribution support vector machine (DrSVM) and pq support vector machine (pq-SVM) in classification problems has inspired a new SVR model, the X-SVR by Feng et al. [13,14]. The decomposition method and the quadratic $\$-insensitive loss function has been implemented into the model with larger adaptability and stability.

For the input and output variables of $\mathbf{x}$ and $\mathbf{y}$, the X-SVR creates a hyperplane $\hat(\mathbf{x})$ to describe the relationship between the datapoints:

```
$$\hat(\mathbf{x}) = \mathbf{p}^T\mathbf{x} - \zeta \quad (12.19)$
```

where $\mathbf{p}, \mathbf{q} \in \mathbb{R}^q$ are the two positive hyperplane coefficients; $\zeta$ is the bias parameter. The above equation is suitable for linear regression with patterned inputs, for irregular ones one uses an implicit mapping $\Theta(\mathbf{x})$ to transform the variables into high-dimension Euclidian space with regularized distributions: