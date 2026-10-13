

### 3. 感知机算法步骤

*   **i = 1**

*   **Repeat**；每次迭代对应一个 epoch。

    1.  **counter = 0**；统计每个 epoch 的更新次数。

    2.  **For** `n = 1, 2, …, N`，**Do**；对于每个 epoch，所有样本呈现一次。

        1.  **If** (`y[n] * x[n]^(T) * θ^((i−1)) ≤ 0`) **Then**

        2.  `θ^((i)) = θ^((i−1)) + μ * y[n] * x[n]`

        3.  `i = i + 1`

        4.  `counter = counter + 1`

    3.  **End For**

*   **Until** `counter = 0`

一旦感知机算法运行并收敛，我们就得到了相关神经元/感知机的突触权重 `θ[i]`（`i = 1, 2, …, l`）以及偏置项 `θ[0]`。这些现在可用于对未知模式进行分类。图 18.2A 展示了基本神经元元素的相应架构。特征 `x[i]`（`i = 1, 2, …, l`）被施加到输入节点。依次地，每个特征乘以相应的突触（权重），然后将偏置项加到它们的线性组合上。该操作的结果随后通过一个称为 *activation* 函数的非线性函数 `f`。根据非线性的形式，会出现不同类型的神经元。在更经典的 McCulloch–Pitts 神经元中，激活函数是 Heaviside 函数，即：

```
f(z) = { 1,  if z > 0
       { 0,  if z ≤ 0
``` (18.5)

通常，求和运算和非线性运算会合并，以在相应的图中形成一个 *node*，从而得到图 18.2B 所示的架构。在后续内容中，术语 neuron 和 node 将交替使用，后者表示大型网络中的一个神经元。

![Figure 18.2 (A) In the basic neuron/perceptron architecture the input features are applied to the input nodes and are weighted by the respective weights that define the synapses. The bias term is then added on their linear combination and the result is pushed through the nonlinearity. In the McCulloch–Pitts neuron, the output fires a 1 for patterns in class ω1 or a zero for class ω2. (B) The summation and nonlinear operation are merged together for graphical simplicity.](images/B978044329238500024X/gr002.jpg)

**Figure 18.2** (A) 在基本神经元/感知机架构中，输入特征被施加到输入节点，并由定义突触的相应权重加权。然后将偏置项加到它们的线性组合上，结果通过非线性函数。在 McCulloch–Pitts 神经元中，对于类别 ω1 中的模式输出激发 1，对于类别 ω2 中的模式输出 0。(B) 为了图形简洁，求和和非线性运算合并在一起。

因此，一个（人工）神经元的基本模型包含 (a) 一个线性组合器、(b) 一个阈值（偏置）和 (c) 一个非线性函数的级联。注意，由于非线性函数的存在，神经元的输出指示了输入模式来源的类别。对于 Heaviside 非线性函数，来自类别 `ω[1]` 的模式输出为 1，来自类别 `ω[2]` 的模式输出为 0。

### Remarks 18.1

