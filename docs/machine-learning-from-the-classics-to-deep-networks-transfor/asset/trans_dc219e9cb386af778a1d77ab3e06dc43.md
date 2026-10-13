

## 数学推导

$$
\sigma_{\eta}^2 H H^T = \sigma_{\eta}^2 (H - X^\dagger)(H - X^\dagger)^T + \sigma_{\eta}^2 (X^T X)^{-1}
$$

其中 $X^\dagger$ 是相应的伪逆矩阵，定义见公式 [(6.4)](#Chp006_249-291_B9780443292385000123.xhtml#deq11)。

因为 $\sigma_n^2 (H - X^\dagger)(H - X^\dagger)^T$ 是半正定矩阵（附录 A），其迹非负（问题 [6.1](#Chp006_249-291_B9780443292385000123.xhtml#o0010)），所以我们有

$$
\text{trace}\{\sigma_n^2 H H^T\} \ge \text{trace}\{\sigma_n^2 (X^T X)^{-1}\}
$$

回顾公式 [(6.7)](#Chp006_249-291_B9780443292385000123.xhtml#deq18)，我们已经证明了

$$
\text{trace}\{\Sigma_{\hat{\theta}}\} \ge \text{trace}\{\Sigma_{\hat{\theta}_{LS}}\} \tag{6.11}
$$

然而，回顾线性代数中迹的性质（附录 A），我们有

