
## 深度学习工具包

- 它们在不同领域的应用方式不同
- 例如

![](img/cb490ed30bca4eda5fbba81c52a2c173_202_0.png)

视觉

自然语言处理

## 国家社会科学基金项目资金预算表

项目名称：基于大数据的宏观经济分析模型研究

| 序号 | 开支内容 | 金额（元） | 备注 |
| --- | --- | --- | --- |
| 1 | 资料费 | 30000 | 图书、文献购置 |
| 2 | 数据采集费 | 20000 | 问卷设计与发放 |
| 3 | 差旅费 | 15000 | 实地调研交通住宿 |
| 4 | 会议费 | 10000 | 学术研讨会议 |
| 5 | 专家咨询费 | 10000 | 咨询专家劳务 |
| 6 | 劳务费 | 25000 | 科研助理及学生劳动 |
| 7 | 印刷出版费 | 5000 | 成果打印与出版 |
| 8 | 其他支出 | 5000 | 办公耗材等 |
| 合计 |  | 105000 |  |

## 深度学习工具包：符号式与命令式

- 符号式 vs. 命令式编程
  - 符号式：先编写符号组装网络，后续再求值
  - 命令式：立即求值

```
A = Variable('A')
B = Variable('B')
C = B * A
D = C + Constant(1)
# compiles the function
f = compile(D)
d = f(A=np.ones(10), B=np.ones(10)*2)
```

符号式

```
import numpy as np
a = np.ones(10)
b = np.ones(10) * 2
c = b * a
d = c + 1
```

命令式

![](img/cb490ed30bca4eda5fbba81c52a2c173_204_0.png)

## 深度学习工具包

- 符号式
  - 优点
    - 易于开发者优化（例如批处理、并行化、核融合）
    - 更高效
  - 缺点
    - 编程方式可能违反直觉
    - 用户程序更难调试
    - 灵活性较差：需要在实际执行任何操作之前先编写符号
- 命令式：
  - 优点
    - 更灵活：写一行，执行一行
    - 易于编程且易于调试：因为它符合我们在大多数编程语言中的使用方式
  - 缺点
    - 效率较低
    - 更难优化

## 大纲

- 深度学习作为数据流图
- 自动微分库
- **静态和动态神经网络**
- 动态声明与 DyNet
- Cavs

## 编程一个神经网络 = 组装一个数据流图？

- 定义神经网络
  - 定义操作和层：全连接？卷积？循环？
  - 定义数据输入输出：读取什么数据？从哪里读取？
  - 定义损失函数/优化目标：L2 损失？Softmax？排序损失？
  - 定义优化算子：SGD、Momentum、Adam 等。
  - 将操作、数据输入输出、损失函数和优化器连接成完整的数据流图，即神经网络的表示

自动微分库随后接管

- 自动构建前向数据流图和反向梯度流图
- 执行训练并应用更新

## 总结：静态声明

- 用户构建数据流图
- 框架分析并优化图
  - 自动推导反向图
  - 如需则加入某些优化
- 通过迭代方式进行训练（通过 SGD）

在 D 上执行图级优化（可选）

/* (a) static declaration */
// all samples must share one graph
declare a static data flow graph 𝒟.
for t = 1 → T:
  read the tth data batch {x_i^t}_{i=1}^K.
  batched computation: 𝒟({x_i^t}_{i=1}^K).

## 总结：静态声明

- 静态声明*似乎是*编程深度学习模型的主导选择
  - 适用于**静态**工作流：定义一次，可运行任意批次/数据
  - 对固定图易于并行化/批处理
  - 易于优化：图有很多现成的优化技术

## 动态神经网络简介

- 深度学习已应用于更结构化的数据
- 神经网络计算遵循数据依赖的结构，以便编码结构信息
  - 序列、树、图
- 例如循环神经网络及其变体
  - 机器翻译、视频理解中的序列 RNN
  - 句子解析和情感分析中的树 RNN
  - 社交网络/图像分割中的 GraphRNN

![](img/cb490ed30bca4eda5fbba81c52a2c173_211_0.png)

## 动态神经网络

- 神经网络的动态性来自多个维度
  - 可变大小的输入
  - 可变大小的输出
    - 例如在机器翻译中，不同样本的输入/输出句子的长度不同
  - 可变结构的输入/输出
    - 例如在图像分割/社交网络中，输入和输出是结构不同的图。
  - 非平凡的推理算法
    - 例如在图神经网络中，推理路径取决于输入数据的结构
- 用于处理结构化数据的神经网络架构会随着输入样本而变化
  - 即*动态神经网络*

## 动态数据流图的静态声明

- 它们被广泛采用，但它们好吗？
  - 无法表达序列之外的结构
  - 通常会产生不必要的（额外）计算，浪费计算资源
- 更多问题
  - 表达复杂流程控制逻辑困难
  - 计算图实现的复杂性
  - 调试困难

## 大纲

- 深度学习作为数据流图
- 自动微分库
- 静态声明和动态神经网络
- **动态声明和 DyNet**
- Cavs

![](img/cb490ed30bca4eda5fbba81c52a2c173_215_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_217_0.png)

## 动态声明

- 静态声明 vs. 动态声明
  - 将图的声明和构建（以及优化）从循环外部移至循环内部
  - 执行单实例训练，因为难以批处理

```
/* (a) static declaration */
// all samples must share one graph
declare a static data flow graph 𝒟.
for t = 1 → T:
    read the tth data batch {xᵢᵗ}ᵢ₌₁ᴷ.
    batched computation: 𝒟({xᵢᵗ}ᵢ₌₁ᴷ).
```

```
/* (b) dynamic declaration */
for t = 1 → T:
    read the tth data batch {xᵢᵗ}ᵢ₌₁ᴷ.
    for k = 1 → K:
        declare a data flow graph 𝒟ᵗᵢ for xᵢᵗ.
        single instance computation: 𝒟ᵢᵗ(xᵢᵗ)
```

## 动态声明：现有框架

- 动态声明
  - 命令式（实例求值）
    - Chainer (Preferred Networks Inc.)、PyTorch (Facebook)
  - 符号式（延迟求值）：**DyNet (Petuum Inc.)**

![](img/cb490ed30bca4eda5fbba81c52a2c173_218_0.png)

## 介绍 DyNet

- 专为动态深度学习工作流设计，例如

## 单词

![](img/cb490ed30bca4eda5fbba81c52a2c173_219_0.png)

## 句子

![](img/cb490ed30bca4eda5fbba81c52a2c173_219_1.png)

## 短语

![](img/cb490ed30bca4eda5fbba81c52a2c173_219_2.png)

## 文档

这部电影完全不可信。
角色呆板，情节荒谬。
话虽如此，我还是喜欢它。

![](img/cb490ed30bca4eda5fbba81c52a2c173_220_0.png)

## DyNet 针对动态声明进行了优化

- 关键要素
  - 分离参数声明和图构建
  - 先声明可训练参数并构建模型
  - 构建计算图
  - 结论：参数定义一次，但图根据输入动态定义 → 因此使图构建更轻量

```
model = dy.Model()

pW = model.add_parameters((20,4))
pb = model.add_parameters(20)

dy.renew_cg()
x = dy.inputVector([1,2,3,4])
W = dy.parameter(pW) # convert params to expression
b = dy.parameter(pb) # and add to the graph

y = W * x + b
```

![](img/cb490ed30bca4eda5fbba81c52a2c173_222_0.png)

## 大纲

- 深度学习作为数据流图
- 自动微分库
- 静态声明和动态神经网络
- 动态声明与 DyNet
- **Cavs**

![](img/cb490ed30bca4eda5fbba81c52a2c173_223_0.png)

## 动态声明：优势

- 动态声明有一个主要优势
  - 灵活性：它可以通过声明与训练数据数量一样多的数据流图来表达*任意动态结构化*的网络

```
/* (b) dynamic declaration */
for t = 1 → T:
    read the tth data batch {xᵢᵗ}ᵢ₌₁ᴷ.
    for k = 1 → K:
        declare a data flow graph Dᵢᵗ for xᵢᵗ.
        single-instance computation: Dᵢᵗ(xᵢᵗ).
```
