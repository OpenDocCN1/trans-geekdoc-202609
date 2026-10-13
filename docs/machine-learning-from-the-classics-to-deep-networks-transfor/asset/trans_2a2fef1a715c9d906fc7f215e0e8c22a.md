

### 在白噪声存在下 LS 估计量是 BLUE

最佳线性无偏估计量（BLUE）的概念是在 [4.9.1](#Chp004_119-175_B978044329238500010X.xhtml) 节中结合 *Gauss–Markov* 定理引入的。令 $\widehat{\mathbf{\theta}}$ 表示任意其他 *线性* 无偏估计量，假设满足

$$\mathbb{E}[\boldsymbol{\eta}\boldsymbol{\eta}^{(T)}] = \sigma_{\eta}^2 \mathbf{I}.$$

那么，由于线性假设，该估计量将对观测到的输出随机变量具有线性依赖关系，即

$$\widehat{\mathbf{\theta}} = H\mathbf{y},\quad H \in \mathbb{R}^{l \times N}.$$

将证明此类估计量的方差永远不可能小于 LS 估计量的方差，即

