

# 建议方法

一种基于深度学习的心血管诊断检测（CADD）用于疾病概率预测，提出了一种精确的AI模型，能够依据患者的临床参数可靠地区分心血管感染。建议的方法基于以下步骤：

1. 包括异常值移除、缺失值替换和不平衡类别处理。
2. 基于权重的特征重要性进行特征选择。
3. 分类。

随后训练模型，并使用训练好的模型进行预测。我们的主要目标是在降低特征/计算复杂度的同时获得更好的结果。本研究旨在通过多层次方法减少心血管并发症。[图 1](#ch11.xhtml#fig11_1) 展示了用于构建高效数据分析和适应度数据分析模型的 `HSBCFS-DCNN` 结构。

![图 1. LSTM-卷积神经网络 (CNN) 的建议架构。](images/fig11_1_B.jpg)

[图 1. LSTM-卷积神经网络 (CNN) 的建议架构。](#ch11.xhtml#R_fig11_1)

## 3.1 心脏数据预处理

收集各种记录，并对心脏数据进行预处理。该数据集包含 303 份患者记录，其中有 6 个缺失值。在从数据集中移除这六条记录后，对剩余的 297 份患者记录进行了预处理。特定数据集属性可使用多类变量和二分类进行分类。心脏病可使用多类变量进行评估。已确定心肌梗死患者的数值。

或者，将患者的心脏病评分设为零，表示其健康。在数据预处理过程中，映射被转换为检测值。预处理了 297 份患者记录，其中 137 份显示值为 1，表明存在心脏病。与没有心脏病的 160 条记录相比，剩余的 160 条记录值为 0。数据集通过去除缺失值和标准差（SD）并通过最小-最大值进行缩放来进行预处理。

```
Algorithm
Initialization
Evaluate μ&β from the values of the heart disease dataset
If a[uv] is missing values the
S(tu,v) = √(∑(μ_u + β_v)²)
X̂ = (X - Minimum) / (Maxi - Mini)
Set a_uv = μ_u + β_v
Start with non-singular evaluates Σ̂&Δ̂
Calculate X̂ᴴX⁻¹ + X̂ + S(Σ̂⁻¹)
Update the evaluation of μ&β
Optimize(Q) in relation to Δ⁻¹ to get Δ̂
Step(Δ): Calculate Δ̂Xᴴ(X)⁻¹ + F(X⁻¹)
Step (Σ)
Obtain updated estimates μ&β
Optimize (Q) in relation to ∑⁻¹ to get Σ̂
Repeat steps
Reduce the missing data
```

上述计算描述了一个通过筛选值来减少属性维度的预处理阶段。每条记录包含多个代表患者信息的属性。

## 3.2 基因模式社会蜘蛛缓解优化 (GPS²oR)

