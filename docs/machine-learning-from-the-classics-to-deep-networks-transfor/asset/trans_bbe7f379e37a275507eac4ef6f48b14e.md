

## 2. 计算期望

为了计算 $\mathbb{E}[\|\mathbf{y} - \Phi\boldsymbol{\theta}\|^2]$，定义 $\boldsymbol{\psi} := \mathbf{y} - \Phi\boldsymbol{\theta}$，并利用前述原理计算 $\mathbb{E}[\boldsymbol{\psi}^T\boldsymbol{\psi}]$，从而得到（问题 [12.5](#Chp012_583-634_B9780443292385000184.xhtml#o0100)）：

$$
B := \mathbb{E}[\|\mathbf{y} - \Phi\boldsymbol{\theta}\|^2] = \|\mathbf{y} - \Phi\boldsymbol{\mu}_{\boldsymbol{\theta}|\mathbf{y}}^{(j)}\|^2 + \text{trace}\{\Phi\boldsymbol{\Sigma}_{\boldsymbol{\theta}|\mathbf{y}}^{(j)}\Phi^T\}.
\tag{12.49}
$$

### 1. 因此，

$$
\mathcal{Q}\left( \alpha,\beta;\alpha^{(j)},\beta^{(j)} \right) = \frac{N}{2}\ln\beta + \frac{K}{2}\ln\alpha - \frac{\beta}{2}B - \frac{\alpha}{2}A - \left( \frac{N}{2} + \frac{K}{2} \right)\ln(2\pi).
\tag{12.50}
$$

### M步：计算

