
$\\begin{array}{l} \\left. \\pi(\\mathbf{x})q(\\mathbf{x}' \\middle| \\mathbf{x})a(\\mathbf{x}' \\middle| \\mathbf{x}) = \\pi(\\mathbf{x})q(\\mathbf{x}' \\middle| \\mathbf{x})\\min\\,\\,(1,\\frac{\\left. \\pi(\\mathbf{x}')q(\\mathbf{x} \\middle| \\mathbf{x}') \\right.}{\\left. \\pi(\\mathbf{x})q(\\mathbf{x}' \\middle| \\mathbf{x}) \\right.})\\,\\,\\,\\,\\,\\,(\\text{definition~of~}a\\,\\text{(~} \\cdot \\,\\text{|} \\cdot \\text{~)}) \\right. \\\\ \\left. \\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, = \\,\\min(\\pi(\\mathbf{x})q,(\\mathbf{x}' \\middle| \\mathbf{x}),\\pi(\\mathbf{x}')q(\\mathbf{x} \\middle| \\mathbf{x}'))\\,\\,\\,\\,\\,\\,\\,\\,\\,(\\text{multiplying~in}) \\right. \\\\ \\left. \\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, = \\,\\pi(\\mathbf{x}')q(\\mathbf{x} \\middle| \\mathbf{x}')\\,\\min\\,(\\frac{\\left. \\pi(\\mathbf{x})q(\\mathbf{x}' \\middle| \\mathbf{x}) \\right.}{\\left. \\pi(\\mathbf{x}')q(\\mathbf{x} \\middle| \\mathbf{x}') \\right.},1)\\,\\,\\,\\,\\,\\,\\,\\,\\,(\\text{dividing~out}) \\right. \\\\ \\left. \\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, = \\pi(\\mathbf{x}')q(\\mathbf{x} \\middle| \\mathbf{x}')a(\\mathbf{x} \\middle| \\mathbf{x}').\\, \\right. \\\\ \\end{array}$

撇开数学性质不谈，`MH` 中需要关注的重要部分是接受概率中的比值 π(x')/π(x)。这意味着如果提出的下一个状态比当前状态更可能，则它一定会被接受。（我们目前忽略了项 q(x | x')/q(x' | x)，该项用于确保细致平衡，并且在许多状态空间中由于对称性等于 1。）如果提出的状态比当前状态可能性更低，则其被接受的概率会成比例下降。

因此，设计提议分布的一个指导原则是确保被提出的新状态是合理可能的。吉布斯采样会自动做到这一点：它从吉布斯分布 P(Xi | $\\mathbf{\\overline{X}}\_{i}$) 中提出，这意味着生成 Xi 的任何特定新值的概率与其概率直接成比例。（练习 `13.GIBM` 要求你证明吉布斯是接受概率为 1 的 `MH` 的特例。）

另一个指导原则是确保链混合良好，这意味着有时提出对状态空间远处的大幅移动。在上面的示例中，偶尔使用 `WEIGHTED-SAMPLE` 将链在新状态中重新启动就起到了这个作用。

除了在设计提议分布时几乎完全自由外，`MH` 还有两个使其实用的额外特性。首先，后验概率 π(x) = P(x|e) 在接受计算中仅以比值 π(x')/π(x) 的形式出现，这非常幸运。直接计算 P(x | e) 正是我们试图用 `MH` 近似的计算，因此对每个样本都这样做是没有意义的！相反，我们使用以下技巧：

$\\frac{\\pi(\\mathbf{x}')}{\\pi(\\mathbf{x})} = \\frac{\\left. P(\\mathbf{x}' \\middle| \\mathbf{e}) \\right.}{\\left. P(\\mathbf{x} \\middle| \\mathbf{e}) \\right.} = \\frac{P(\\mathbf{x}',\\mathbf{e})}{P(\\mathbf{e})}\\frac{P(\\mathbf{e})}{P(\\mathbf{x},\\mathbf{e})} = \\frac{P(\\mathbf{x}',\\mathbf{e})}{P(\\mathbf{x},\\mathbf{e})}.$

该比值中的项是完整的联合概率，即贝叶斯网中条件概率的乘积。该比值的第二个有用性质是，只要提议分布在产生 x' 时仅对 x 做出局部更改，则条件概率乘积中只有少数项会不同。涉及值未发生变化的变量的所有条件概率在比值中都会抵消。因此，与吉布斯采样一样，只要状态变化是局部的，生成每个样本所需的工作量与网络的大小无关。

## 13.4.3 近似推理的编译

[图 13.17](#Chapter13-04.xhtml#fig13-17)、[图 13.18](#Chapter13-04.xhtml#fig13-18) 和 [图 13.20](#Chapter13-04.xhtml#fig13-20) 中的采样算法具有一个共同特性：它们操作的是作为数据结构表示的贝叶斯网。这似乎很自然：毕竟，贝叶斯网是有向无环图，否则还能怎样表示呢？这种方法的问题在于，访问数据结构所需的操作——例如查找节点的父节点——在采样算法运行期间会被重复数千或数百万次，而所有这些计算都是完全不必要的。

网络的结构和条件概率在整个计算过程中保持不变，因此有机会将网络编译成模型特定的推理代码，只执行该特定网络所需的推理计算。（如果这听起来很熟悉，它与 [第 9 章](#Chapter09-00.xhtml) 中逻辑程序编译所使用的思想相同。）例如，假设我们想在 [图 13.2](#Chapter13-01.xhtml#fig13-2) 的入室盗窃网络中对 `Earthquake` 变量进行吉布斯采样。根据 [图 13.20](#Chapter13-04.xhtml#fig13-20) 中的 `GIBBS-ASK` 算法，我们需要执行以下计算：

设置 `x` 中 `Earthquake` 的值，通过从 `P(Earthquake|mb(Earthquake))` 中采样

其中后者分布根据 [公式 (13.10)](#Chapter13-04.xhtml#eq13-10) 计算，重复如下：

$\\left. P(x\_{i} \\middle| mb(X\_{i})) = \\alpha\\, P(x\_{i} \\middle| parents\\text{(}X\_{i}\\text{))}{\\prod\\limits\_{Y\_{j} \\in Children(X\_{i})}\\left. P(y\_{j} \\middle| \\ parents(Y\_{j})). \\right.} \\right.$

这一计算反过来需要在贝叶斯网结构中查找 `Earthquake` 的 `parents` 和 `Children`；查找它们当前的值；使用这些值索引到相应的 `CPTs`（这些也必须从贝叶斯网中找到）；并将这些 `CPTs` 中所有适当的行相乘以形成用于采样的新分布。最后，如 [第 454 页](#Chapter13-04.xhtml#page_454) 所指出的，采样步骤本身必须构造离散分布的累积版本，然后在其中找到对应于从 [0,1] 采样的随机数的取值。

如果相反，我们编译网络，我们将获得针对 `Earthquake` 变量的模型特定采样代码，如下所示：

```
r←a uniform random sample from [0,1]
if Alarm = true
    then if Burglary = true
        then return [r < 0.0020212]
        else return [r < 0.36755]
    else if Burglary = true
        then return [r < 0.0016672]
        else return [r < 0.0014222]
```
