# 10.3.5  MAP estimation

In Sec. 10.2.7 we discussed the benefits of ℓ₂ regularization for binary logistic regression. These benefits hold also in the multi-class case. However, there is also an additional, and surprising, benefit to do with **identifiability** of the parameters, as pointed out in [HTF09, Ex.18.3]. (We say that the parameters are identifiable if there is a unique value that maximizes the likelihood; equivalently, we require that the NLL be *strictly convex*.)

To see why identifiability is an issue, recall that multiclass logistic regression has the form

$$p(y=c\mid \mathbf{x},\mathbf{W})=\frac{\exp(\mathbf{w}_c^{\mathsf{T}}\mathbf{x})}{\sum_{k=1}^{C}\exp(\mathbf{w}_k^{\mathsf{T}}\mathbf{x})}\tag{10.81}$$

where **W** is a $C\times C$ weight matrix. We can arbitrarily define $\mathbf{w}_c=\mathbf{0}$ for one of the classes, say $c=C$, since $p(y=C\mid\mathbf{x},\mathbf{W})=1-\sum_{c=1}^{C-1}p(y=c\mid\mathbf{x},\mathbf{w})$. In this case, the model has the form

$$p(y=c\mid \mathbf{x},\mathbf{W})=\frac{\exp(\mathbf{w}_c^{\mathsf{T}}\mathbf{x})}{1+\sum_{k=1}^{C-1}\exp(\mathbf{w}_k^{\mathsf{T}}\mathbf{x})}\tag{10.82}$$

If we don’t “clamp” one of the vectors to some constant value, the parameters will be unidentifiable.

However, suppose we don’t clamp $\mathbf{w}_c=\mathbf{0}$, so we are using Equation 10.81, but we add ℓ₂ regularization by optimizing

$$\mathrm{PNLL}(\mathbf{w})=-\sum_{n=1}^{N}\log p(y_n\mid\mathbf{x}_n,\mathbf{W})+\lambda\sum_{c=1}^{C}\lVert\mathbf{w}_c\rVert_2^2\tag{10.83}$$

At the optimum we have $\sum_{c=1}^{C}\hat{w}_{cj}=0$ for $j=1:D$, so the weights automatically satisfy a sum-to-zero constraint, thus making them uniquely identifiable.

To see why, note that at the optimum we have

$$\nabla\mathrm{NLL}(\mathbf{w})+2\lambda\mathbf{w}=\mathbf{0}\tag{10.84}$$

$$\sum_n(\mathbf{y}_n-\boldsymbol{\mu}_n)\otimes\mathbf{x}_n=\lambda\mathbf{w}\tag{10.85}$$

Hence for any feature dimension $j$ we have

$$\lambda\sum_c w_{cj}=\sum_n\sum_c(y_{nc}-\mu_{nc})x_{nj}=\sum_n\left(\sum_c y_{nc}-\sum_c\mu_{nc}\right)x_{nj}=\sum_n(1-1)x_{nj}=0\tag{10.86}$$

Thus if $\lambda>0$ we have $\sum_c\hat{w}_{cj}=0$, so the weights will sum to zero across classes for each feature dimension.

# 10.3.6  Maximum entropy classifiers

Recall that the multinomial logistic regression model can be written as

$$p(y=c\mid\mathbf{x},\mathbf{W})=\frac{\exp(\mathbf{w}_c^{\mathsf{T}}\mathbf{x})}{Z(\mathbf{w},\mathbf{x})}=\frac{\exp(\mathbf{w}_c^{\mathsf{T}}\mathbf{x})}{\sum_{c'=1}^{C}\exp(\mathbf{w}_{c'}^{\mathsf{T}}\mathbf{x})}\tag{10.87}$$