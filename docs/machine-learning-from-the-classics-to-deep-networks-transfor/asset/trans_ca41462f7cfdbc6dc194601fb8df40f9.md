
$$
\widehat{\mathbf{s}}_{\mathbf{\theta}_{\ast}}(\mathbf{x}_{t},t,y) = \mathbf{s}_{\mathbf{\theta}_{\ast}}(\mathbf{x}_{t},t,\varnothing) + \gamma\left( \mathbf{s}_{\mathbf{\theta}_{\ast}}(\mathbf{x}_{t},t,y) - \mathbf{s}_{\mathbf{\theta}_{\ast}}(\mathbf{x}_{t},t,\varnothing) \right),
$$

其中 $\gamma > 0$ 是引导尺度常数。换句话说，神经网络的输出被进一步外推至 $\mathbf{s}_{\mathbf{\theta}_{\ast}}(\mathbf{x}_{t},t,y)$ 的方向，并远离 $\mathbf{s}_{\mathbf{\theta}_{\ast}}(\mathbf{x}_{t},t,\varnothing)$。如果两边同时取负号，并乘以该时间步对应的标准差，则公式 [(19.85)](#Chp019_997-1102_B9780443292385000251.xhtml#deq168) 可以等价地用相应的 $\boldsymbol{\epsilon}_{\boldsymbol{\theta}}$ 估计值来表示，以替代 $\mathbf{s}_{\boldsymbol{\theta}}$。注意，若 $\gamma = 0$，公式 [(19.85)](#Chp019_997-1102_B9780443292385000251.xhtml#deq168) 退化为无条件模型；若 $\gamma = 1$，则与标准类条件模型一致。

公式 [(19.85)](#Chp019_997-1102_B9780443292385000251.xhtml#deq168) 的解释依赖于公式 [(19.83)](#Chp019_997-1102_B9780443292385000251.xhtml#deq165)。公式 [(19.85)](#Chp019_997-1102_B9780443292385000251.xhtml#deq168) 涉及公式 [(19.83)](#Chp019_997-1102_B9780443292385000251.xhtml#deq165) 中真实对应项的近似梯度，前提是我们使用一个*隐式*分类器，

$$
q^{(i)}(y|\mathbf{x}_{t}) \propto \left( \frac{q(\mathbf{x}_{t}|y)}{q(\mathbf{x}_{t})} \right)^{\gamma}.
$$

注意，根据贝叶斯法则，
