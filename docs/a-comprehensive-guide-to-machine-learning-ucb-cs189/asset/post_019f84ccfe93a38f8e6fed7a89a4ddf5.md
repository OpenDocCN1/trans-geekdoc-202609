
## CHAPTER 2. PROBABILISTIC MODELS IN MACHINE LEARNING

Note that there are two terms: the prior mean $\mu_W$, plus another that depends on both the data and the prior. The precision matrix of $W$'s prior $(\Sigma_W^{-1})$ controls how the data fit affects our estimate.

To gain intuition, let us consider the simplified case

```
$$\Sigma_W = \begin{bmatrix} \sigma_1^2 & 0 & 0 \\ 0 & \sigma_2^2 & 0 \\ \vdots & \vdots & \vdots \\ 0 & 0 & \sigma_n^2 \end{bmatrix}$$
```

When the variance $\sigma_j^2$ for dimension $j$ is large, the formulation is telling us that $W_j$ may take on a wide range of values. We do not want to penalize dimension as much, preferring to let the data fit out. And indeed the corresponding entry $\Sigma_W^{-1}$ will be small, as desired.
Conversely if $\sigma_j^2$ is small, there is little variance in the value of $W_j$, so $W_j \approx \mu_j$. As we penalize the magnitude of the data-fit contribution to $W_j$ more heavily.

## Alternative derivation

MAP with colored noise can be expressed as:

```
$$\mathbf{U, V} \overset{iid}{\sim} \mathcal{N}(\mathbf{0,I}) \quad (2.1)$$
$$\begin{bmatrix} \mathbf{Y} \end{bmatrix} = \begin{bmatrix} \mathbf{R}_Z & \mathbf{XR}_W \\ 0 & \mathbf{R}_W \end{bmatrix} \begin{bmatrix} \mathbf{U} \\ \mathbf{V} \end{bmatrix} \quad (2.2)$$
```

where $\mathbf{R}_Z$ and $\mathbf{R}_W$ are relationships with $W$ and $Z$, respectively. Note that the $\mathbf{R}$ appears twice because our model assumes $\mathbf{Y} = \mathbf{XR} + \text{noise}$, so if $\mathbf{W} = \mathbf{R}_W\mathbf{V}$, then we must have $\mathbf{Y} = \mathbf{XR}_W\mathbf{V} + \text{noise}$.

We want to find the posterior $W | \mathbf{Y}$. The formulation makes it relatively easy to find the posterior of $Y$ conditioned on $\mathbf{W}$ (see below), but not vice-versa. So let's pretend instead

```
$$\mathbf{U', V'} \overset{iid}{\sim} \mathcal{N}(\mathbf{0,I})$$
$$\begin{bmatrix} \mathbf{W} \end{bmatrix} = \begin{bmatrix} \mathbf{A} & \mathbf{B} \\ 0 & \mathbf{D} \end{bmatrix} \begin{bmatrix} \mathbf{U'} \\ \mathbf{V'} \end{bmatrix}$$
```

Now $\mathbf{W} | \mathbf{Y} = \mathbf{y}$ is straightforward. Since $\mathbf{V}' = \mathbf{D}^{-1}\mathbf{Y}$, the conditional mean and variance of $\mathbf{W} | \mathbf{Y} = \mathbf{y}$ can be computed as:

```
$$\mathbf{E}[\mathbf{W} | \mathbf{Y} = \mathbf{y}] = \mathbf{E}[\mathbf{AU'} + \mathbf{BV}'] | \mathbf{Y} = \mathbf{y}]$$
$$\mathbf{E}[\mathbf{AU'} | \mathbf{Y} = \mathbf{y}] + \mathbf{E}[\mathbf{BD}^{-1}\mathbf{Y} | \mathbf{Y} = \mathbf{y}]$$
$$\mathbf{A}\mathbf{E}[\mathbf{U'}] + \mathbf{BD}^{-1}\mathbf{y}$$
$$\mathbf{BD}^{-1}\mathbf{y}$$
```

```
$$\text{Var}(\mathbf{W} | \mathbf{Y} = \mathbf{y}) = \mathbf{E}[(\mathbf{W} - \mathbf{E}[\mathbf{W}])(\mathbf{W} - \mathbf{E}[\mathbf{W}])^T | \mathbf{Y} = \mathbf{y}]$$
$$\mathbf{E}[(\mathbf{AU'} + \mathbf{BD}^{-1}\mathbf{Y})(\mathbf{AU'} + \mathbf{BD}^{-1}\mathbf{Y})^T | \mathbf{Y} = \mathbf{y}]$$
$$\mathbf{E}[(\mathbf{AU'})(\mathbf{U'})^T | \mathbf{Y} = \mathbf{y}]$$
$$\mathbf{AU'}(\mathbf{U'})^T\mathbf{A}^T$$
```

## 2.6. MAP WITH COLORED NOISE

```
$= \mathbf{E}[\mathbf{U}'(\mathbf{U}')^T] \mathbf{A}^T$$
= \text{Var}(\mathbf{U}')=I$$
==\mathbf{AA}^T$$
```

In both cases where we drop the conditioning on $\mathbf{Y}$, we are using fact $\mathbf{U}'$ is independent of $\mathbf{V}'$ (and independent of $\mathbf{Y} = \mathbf{DV}'$). Therefore

```
$$\mathbf{W} \mid \mathbf{y} \sim \mathcal{N}(\mathbf{BD}^{-T}\mathbf{y}, \mathbf{AA}^T)$$
```

Recall that a Gaussian distribution is completely specified by its mean and covariance matrix. We see that the covariance matrix of the joint distribution

```
$$\mathbf{E} \left[ \begin{bmatrix} \mathbf{W} \\ \mathbf{Y} \end{bmatrix} \begin{bmatrix} \mathbf{W}^T & \mathbf{Y}^T \end{bmatrix} \right] = \begin{bmatrix} \mathbf{A} & \mathbf{B} \\ 0 & \mathbf{D} \end{bmatrix} \begin{bmatrix} \mathbf{U'} \\ \mathbf{V'} \end{bmatrix} \begin{bmatrix} (\mathbf{U'})^T & (\mathbf{V'})^T \end{bmatrix} \begin{bmatrix} \mathbf{A}^T & 0 \\ \mathbf{B}^T & \mathbf{D}^T \end{bmatrix}$$
```
Wait, the OCR for the matrix expansion in the original text is very garbled. Let me reconstruct the logic based on standard Gaussian conditional properties:

Matching the terms, we can express the conditional mean and variance of $\mathbf{W} \mid \mathbf{y}$ in terms of these (cross-)covariance matrices:

$$\ $$\mathbf{BD}^{-T}\mathbf{y} = \mathbf{B}\mathbf{D}^{-1}\mathbf{y} = \Sigma_{W,Y}\Sigma_{Y}^{-1}\mathbf{y}$$
$$\Sigma_{W} = \mathbf{AA}^T + \mathbf{BB}^T$$
$$\Sigma_{Y} = \mathbf{AA}^T + \mathbf{BB}^T - \mathbf{B}\mathbf{D}^{-1}\mathbf{D}^{-T}\mathbf{B}^T$$
$$= \Sigma_{W} - \Sigma_{W,Y}\Sigma_{Y}^{-1}$$

We can then apply the same logic to the original estimator:

```
$$\mathbf{E} \left[ \begin{bmatrix} \mathbf{Y} \\ \mathbf{W} \end{bmatrix} \begin{bmatrix} \mathbf{Y}^T & \mathbf{W}^T \end{bmatrix} \right] = \begin{bmatrix} \mathbf{R}_Z\mathbf{R}_Z^T + \mathbf{XR}_W\mathbf{R}_W^T & \mathbf{XR}_W\mathbf{R}_W^T \\ \mathbf{R}_W\mathbf{R}_W^T & \mathbf{R}_W\mathbf{R}_W^T \end{bmatrix}$$
$$= \begin{bmatrix} \Sigma_{Y} & \Sigma_{Y,W} \\ \Sigma_{W,Y} & \Sigma_{W} \end{bmatrix}$$
```

Therefore after defining $\Sigma_{Z} = \mathbf{R}_Z\mathbf{R}_Z^T$, we can read out

```
$$\Sigma_{W} = \mathbf{R}_W\mathbf{R}_W^T$$
$$\Sigma_{Y} = \Sigma_{Z} + \mathbf{X}\Sigma_{W}\mathbf{X}^T$$
$$\Sigma_{W,Y} = \mathbf{X}\Sigma_{W}$$
$$\Sigma_{W,Y} = \Sigma_{W}\mathbf{X}^T$$
```

Plugging this into our estimator yields

```
$$\mathbf{w} = \mathbf{E}[\mathbf{W} \mid \mathbf{y}] = \mathbf{y}$$
$$= \Sigma_{W,Y}\Sigma_{Y}^{-1}\mathbf{y}$$
```

$$= \Sigma_{W}\mathbf{X}^T(\Sigma_{Z} + \Sigma_{W}\mathbf{X}^T)^{-1}\mathbf{y}$

One may be concerned because this expression does not take the form we expect - the inverted matrix is hitting y directly, unlike other solutions we've seen. But using the Woodbury matrix identity$^1$, it turns out we can rewrite this expression as

```
$$\mathbf{w} = (\mathbf{X}^T\Sigma_{Z}^{-1} + \Sigma_{W}^{-1})^{-1}\mathbf{X}^T\Sigma_{Z}^{-1}\mathbf{y}$$
```

which looks more familiar.

## 2.7 Summary of Linear Gaussian Statistical Models

We have seen a number of related linear models, with varying assumptions about the randomness in the observations and the weights. We summarize these below:

| Z | $\mathcal{N}(0, \mathbf{I})$ | $\mathcal{N}(0, \mathbf{\Sigma}_Z)$ |
|---|---|---|
| W | | |
| No prior | $\mathbf{w}_{OLS} = (\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y}$ | $\mathbf{w}_{WLS} = (\mathbf{X}^T\Sigma_{Z}^{-1}\mathbf{X})^{-1}\mathbf{X}^T\Sigma_{Z}^{-1}\mathbf{y}$ |
| $\mathcal{N}(0, \lambda)$ | $\mathbf{w}_{RIDGE} = (\mathbf{X}^T\mathbf{X} + \lambda\mathbf{I})^{-1}\mathbf{X}^T\mathbf{y}$ | $\mathbf{w}_{REG} = (\mathbf{X}^T\Sigma_{Z}^{-1}\mathbf{X} + \lambda\Sigma_{Z}^{-1})^{-1}\mathbf{X}^T\Sigma_{Z}^{-1}\mathbf{y}$ |
| $\mathcal{N}(0, \Sigma_W)$ | $\mathbf{w}_{MAP} = (\mathbf{X}^T\mathbf{X} + \Sigma_W^{-1})^{-1}\mathbf{X}^T\mathbf{y}$ | $\mathbf{w}_{MAP} = (\mathbf{X}^T\Sigma_{Z}^{-1}\mathbf{X} + \Sigma_W^{-1})^{-1}\mathbf{X}^T\Sigma_{Z}^{-1}\mathbf{y}$ |

> $^1$(\mathbf{A} + \mathbf{UCV})^{-1} = \mathbf{A}^{-1} - \mathbf{A}^{-1}\mathbf{U}(\mathbf{C}^{-1} + \mathbf{V}^T\mathbf{A}^{-1}\mathbf{U})^{-1}\mathbf{VA}^{-1}$

## CHAPTER 3

# Low-Rank approximation

## 3.1 Total Least Squares

Previously, we have covered Ordinary Least Squares (OLS), which assumes that the dependent variable y is noisy but the independent variables x are noise-free. We now discuss Total Least Squares (TLS), which arises in the case where we assume that x data is also corrupted by noise. Both LS methods want to get a model that produce an approximation closest to all the points, but they measure the distance differently.

![](img/99defe26aebed215976e83d281581f33_44_0.png)

The red represents vertical distance, which OLS aims to minimize. The blue represents perpendicular distance, which TLS aims to minimize. Note that all blue lines are perpendicular to the black line (hypothesis model), while all red lines are perpendicular to the x axis.

We might begin with a probabilistic formulation and fit the parameters via maximum likelihood estimation, as before. Suppose on the plane, we have a true model that we can recover from some data points:

```
$y_i = ax_i$$
```

and observe data points in the form

```
$$(x_i + z_{xi}, y_i + z_{yi})$$
```

where the noise terms are normally distributed, i.e. $z_{xi}, z_{yi} \overset{\iid}}{=} \mathcal{N}(0, 1)$.

Applying the equation (1) that comes from the true model mentioned above, we rewrite (2) in the
