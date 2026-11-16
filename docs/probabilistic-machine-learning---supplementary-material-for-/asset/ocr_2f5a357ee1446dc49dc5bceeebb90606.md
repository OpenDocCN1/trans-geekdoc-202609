![](bbox=[0.302, 0.093, 0.697, 0.268])

Figure 6.3: Robust PCA applied to some frames from a surveillance video. First column is input image. Second column is low-rank background model. Third model is sparse foreground model. Last column is derived foreground mask. From Figure 1 of [Bou+17]. Used with kind permission of Thierry Bouwmans.

Finally, if we define \( u_t = (1/\rho)y_t \) and \( \lambda = 1/\rho \), we can now write this in a more general way:

```
\( x_{t+1} = \text{prox}_{\lambda \mathcal{L}_s}(z_t - u_t) \) (6.62)
\( z_{t+1} = \text{prox}_{\lambda \mathcal{L}_r}(x_{t+1} + u_t) \) (6.63)
\( u_{t+1} = u_t + x_{t+1} - z_{t+1} \) (6.64)
```

This is called the **alternating direction method of multipliers** or **ADMM** algorithm. The advantage of this method is that the different terms in the objective (along with any constraints they may have) are handled completely independently, allowing different solvers to be used. Furthermore, the method can be extended to the stochastic setting as shown in [ZK14].

# 6.1.6.1 Example: robust PCA

In this section, we give an example of ADMM from [PB+14, Sec. 7.2].

Consider the following **matrix decomposition problem**:

```
\(\text{minimize}_{\mathbf{X}_{1:J}} \sum_{j=1}^J \gamma_j \phi_j(\mathbf{X}_j) \text{ s.t. } \sum_{j=1}^J \mathbf{X}_j = \mathbf{A}\) (6.65)
```

where \(\mathbf{A} \in \mathbb{R}^{m \times n}\) is a given data matrix, \(\mathbf{X}_j \in \mathbb{R}^{m \times n}\) are the optimization variables, and \(\gamma_j > 0\) are trade-off parameters.

For example, suppose we want to find a good least squares approximation to \(\mathbf{A}\) as a sum of a low rank matrix plus a sparse matrix. This is called **robust PCA** [Can+11], since the sparse matrix can handle the small number of outliers that might otherwise cause the rank of the approximation to be high. The method is often used to decompose surveillance videos into a low rank model for the static background, and a sparse model for the dynamic foreground objects, such as moving cars or people, as illustrated in Figure 6.3. (See e.g., [Bou+17] for a review.) RPCA can also be used to remove small “outliers”, such as specularities and shadows, from images of faces, to improve face recognition.

We can formulate robust PCA as the following optimization problem:

```
\(\text{minimize } ||\mathbf{A} - (\mathbf{L} + \mathbf{S})||_F^2 + \gamma_L ||\mathbf{L}||_* + \gamma_S ||\mathbf{S}||_1\) (6.66)
```

which is a sparse plus low rank decomposition of the observed data matrix. We can reformulate this to match the form of a canonical matrix decomposition problem by defining \(\mathbf{X}_1 = \mathbf{L}\), \(\mathbf{X}_2 = \mathbf{S}\) and \(\mathbf{X}_3 = \mathbf{A} - (\mathbf{X}_1 + \mathbf{X}_2)\), and then using these loss functions:

```
\(\phi_1(\mathbf{X}_1) = ||\mathbf{X}_1||_*, \, \phi_2(\mathbf{X}_2) = ||\mathbf{X}_2||_1, \, \phi_3(\mathbf{X}_3) = ||\mathbf{X}_3||_F^2\) (6.67)
```