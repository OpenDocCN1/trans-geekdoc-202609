

# 混合方法 – 分变式分类 ■ 283

得到的交叉熵损失函数给出：

```python
$L(w) = \sum_{k=1}^{N}\sum_{t=1}^{K} y_{kt} \cdot \log o_{kt}, \quad (23.12)$
```

## 23.3 SPSA 优化器

同步扰动随机近似（Simultaneous Perturbation Stochastic Approximation, SPSA）优化器执行随机梯度近似（https://www.jhuapl.edu/SPSA/），无论优化问题的维度如何，它只需要两次损失函数的测量 [13]。其目标是找到：

```python
$w^{*} = \arg_{w} \min L(w) \quad (23.13)$
```

使用梯度算子：

```python
$\nabla = \begin{bmatrix} \frac{\partial}{\partial w_{1}}, & \frac{\partial}{\partial w_{2}}, & \dots, & \frac{\partial}{\partial w_{D}} \end{bmatrix}^{T}$
```

```python
$g(w) = \nabla L(w) = \begin{bmatrix} \frac{\partial L}{\partial w_{1}}, & \frac{\partial L}{\partial w_{2}}, & \dots, & \frac{\partial L}{\partial w_{D}} \end{bmatrix}^{T}$
```

SPSA 使用迭代过程，$\tau$ 表示从 $\tau=1$ 开始的迭代：

```python
$w_{\tau+1} = w_{\tau} - \eta_{\tau} \cdot \hat{g}(w_{\tau}) \quad (23.14)$
```

其中 $\eta_{\tau}$ 是随 $\tau$ 减小的学习率，$\hat{g}(w_{\tau})$ 是梯度 $\hat{g}(w_{\tau})$ 的估计，公式为：

```python
$\hat{g}_{\tau} = \frac{L(w_{\tau} + c_{\tau} \cdot \Delta_{\tau}) - L(w_{\tau} - c_{\tau} \cdot \Delta_{\tau})}{2c_{\tau} \cdot \Delta_{\tau}} \quad (23.15)$
```

$\Delta_{\tau}$ 是随机扰动向量，$c_{\tau}$ 是一个随 $\tau$ 减小的极正数。SPSA 方法中每次迭代所需的损失函数测量次数为 2，与维度无关。带有随机搜索方向的SPSA并不遵循梯度路径，而是对其进行近似。在单个量子分类器上使用变分分类器时，SPSA 是最推荐的选择，因为它可以在存在噪声的情况下使用。

## 23.4.1 Qiskit 变分量子分类器

Qiskit 实现了可以嵌入经典学习任务的变分分类器（VQC）。在这个简单的 qiskit 示例中，我们创建了 10 个二维训练数据点和 5 个测试数据点，每个类包含 2 个。我们使用了与之前相同的分类电路。按照使用交叉熵的算法要求，我们对标签进行了热热编码（hot encode）。然后，我们使用回调函数设置了我们的经典优化器和 VQC 算法。我们绘制了随优化步骤变化的代价函数，

# 284 基于 Qiskit 的量子人工智能

```python
from qiskit.utils import algorithm_globals
algorithm_globals.random_seed = 3142

import numpy as np
np.random.seed(algorithm_globals.random_seed)

from qiskit_machine_learning.datasets import ad_hoc_data
TRAIN_DATA, TRAINING_LABELS, TEST_DATA, TEST_LABELS = (
    ad_hoc_data(training_size=10,
    test_size=5,
    gap=0.3,
    onehot=False)
)

from qiskit.circuit.library import ZZFeatureMap, TwoLocal
FEATURE_MAP = ZZFeatureMap(feature_dimension=2, reps=2)
VAR_FORM = TwoLocal(2, ['rz', 'rz'], 'cz', reps=2)
AD_HOC_CIRCUIT = FEATURE_MAP.compose(VAR_FORM)

from sklearn.preprocessing import OneHotEncoder
encoder = OneHotEncoder()
training_labels_oh = encoder.transform(TRAIN_LABELS.reshape(-1, 1)).toarray()
test_labels_oh = encoder.transform(TEST_LABELS.reshape(-1, 1)).toarray()

from qiskit.algorithms.optimizers import SPSA

class OptimizerLog:
    """用于存储优化器的中间结果"""
    def __init__(self):
        self.evaluations = []
        self.parameters = []
        self.costs = []
    def update(self, evaluation, parameter, cost, _stepsize, _accept):
        """保存中间结果。优化器传递五个值
        但我们忽略了后两个."""
        self.evaluations.append(evaluation)
        self.parameters.append(parameter)
        self.costs.append(cost)
```

```python
# initial_point = np.random.random(VAR_FORM.num_parameters)
initial_point = np.array([0.3200227, 0.6506368, 0.55995053,
0.96656228, 0.38243769, 0.94030904,
0.82271449, 0.26810137, 0.61076489,
0.82301609, 0.11789148, 0.29667125])
```

```python
from qiskit_machine_learning.algorithms.classifiers import VQC
log = OptimizerLog()
vqc = VQC(feature_map=FEATURE_MAP,
ansatz=VAR_FORM,
loss='entropy')
```

![](img/52faec2d621d75e53089d939bb234a82_311_0.png)

图 23.2 随优化步骤变化的代价函数收敛于局部极值。

```python
optimizer=SPSA(callback=log.update),
initial_point=initial_point
```

vqc.fit(TRAIN_DATA, training_labels_oh)

```python
import matplotlib.pyplot as plt
fig = plt.figure()
plt.plot(log.evaluations, log.costs)
plt.xlabel('Steps')
plt.ylabel('Cost')
plt.show()
```

我们绘制了随优化步骤变化的代价函数，可以看到它开始收敛于极值，见图 23.2。最后，我们通过评分对训练好的 VQC 分类器进行测试。

```python
# score ==准确率
vqc.score(TEST_DATA, test_labels_oh)
```

评分表示平均准确率，它决定了测试集的真实值，在我们的案例中得分为 0.9。

## 结论

我们以量子人工智能（QAI）结束了这段旅程。量子计算机是利用叠加和纠缠等量子力学现象的计算机。量子优势基于与 Grover's 算法和相位估计算法相关的两个原理。量子计算仍处于早期阶段，在实现 QAI 之前，仍有许多必须克服的技术挑战。然而，对于量子计算而言，竞赛已经开始，几年前的科学梦想正变为现实。你现在正处于量子计算研究的前沿。

## 24.1 结语

基于量子门模型的量子计算基于加速计算的原理，这些原理导致了量子优势：

- Grover s算法可以对给定数量的解实现平方级的加速搜索。
- 量子傅里叶变换（QFT）可以确定波的周期，或作为相位估计算法的基础。
- 变分分类器可以在极高维空间上计算经典计算机无法求解的函数。

大多数机器学习算法都受到输入问题的影响 [1]。对于稀疏数据，高效的数据准备是可能的 [39]。然而，输入问题尚未解决，理论速度分析通常会忽略这个问题 [94]，尽管它是数据编码的主要瓶颈。

量子优越性意味着可编程量子设备可以解决经典计算机在任何可行时间内无法解决的问题。当足够的比特可用时，量子计算机将占据主导地位。

## 24.2 延伸阅读

关于量子计算不容错过的书籍 [72] 和 [47]。

