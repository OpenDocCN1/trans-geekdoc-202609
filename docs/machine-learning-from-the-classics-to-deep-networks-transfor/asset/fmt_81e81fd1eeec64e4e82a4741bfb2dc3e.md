
### 扩散模型训练算法步骤

4.  **前向过程采样**：
    $$
    \mathbf{x}_t = \sqrt{\bar{\alpha}}_t \mathbf{x}_0 + \sqrt{1 - \bar{\alpha}_t} \boldsymbol{\epsilon}
    $$
    在时间步 $t$ 生成带噪样本（公式 19.59）。

5.  **神经网络预测**：
    $$
    \boldsymbol{\epsilon}_{\boldsymbol{\theta}}(\mathbf{x}_t, t) = f_{\boldsymbol{\theta}}(\mathbf{x}_t)
    $$
    输出神经网络对噪声的预测。

6.  **计算梯度**：
    $$
    \Delta \boldsymbol{\theta} = \nabla_{\boldsymbol{\theta}} \|\boldsymbol{\epsilon} - \boldsymbol{\epsilon}_{\boldsymbol{\theta}}(\mathbf{x}_t, t)\|^2
    $$
    计算参数梯度。

7.  **参数更新**：
    $$
    \boldsymbol{\theta}_{\text{new}} = \boldsymbol{\theta}_{\text{old}} - \mu \Delta \boldsymbol{\theta}
    $$
    使用学习率 $\mu$ 更新参数。

*   **Until Convergence**（直到收敛）

---

### 采样过程（反向过程）

训练通过任意反向传播类算法执行。一旦训练完成并获得最优参数 $\boldsymbol{\theta}^*$，即可通过反向过程生成样本。反向路径采样的核心围绕公式 (19.61) 及其重参数化展开，得到：

$$
\mathbf{x}_{t-1} = \boldsymbol{\mu}_{\boldsymbol{\theta}^*}(\mathbf{x}_t, t) + \sigma_t \mathbf{z}
$$

(19.71)
