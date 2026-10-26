
## Deep Learning Toolkits

- They are adopted differently in different domains
- For example

![](img/cb490ed30bca4eda5fbba81c52a2c173_202_0.png)

Vision

NLP

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

## Deep Learning Toolkits: Symbolic and Imperative

- Symbolic vs. imperative programming
  - Symbolic: write symbols to assemble the networks first, evaluate later
  - Imperative: immediate evaluation

```
A = Variable('A')
B = Variable('B')
C = B * A
D = C + Constant(1)
# compiles the function
f = compile(D)
d = f(A=np.ones(10), B=np.ones(10)*2)
```

Symbolic

```
import numpy as np
a = np.ones(10)
b = np.ones(10) * 2
c = b * a
d = c + 1
```

Imperative

![](img/cb490ed30bca4eda5fbba81c52a2c173_204_0.png)

## Deep Learning Toolkits

- Symbolic
  - Good
    - easy to optimize (e.g. batching, parallelization, kernel fusion) for developers
    - More efficient
  - Bad
    - The way of programming might be counter-intuitive
    - Harder to debug for user programs
    - Less flexible: you need to write symbols before actually doing anything
- Imperative:
  - Good
    - More flexible: write one line, evaluate/execute one line
    - Easy to program and easy to debug: because it matches the way we use in most programming languages
  - Bad
    - Less efficient
    - More difficult to optimize

## Outline

- Deep Learning as Dataflow Graphs
- Auto-differential Libraries
- **Static and Dynamic Neural Networks**
- Dynamic Declaration and DyNet
- Cavs

## Program an NN = Assemble a Dataflow Graph?

- Define a neural network
  - Define operations and layers: fully-connected? Convolution? Recurrent?
  - Define the data I/O: what data to read? Where?
  - Define a loss function/optimization objective: L2 loss? Softmax? Ranking Loss?
  - Define an optimization operator: SGD, Momentum, Adam, etc.
  - Connect operations, data I/O, loss functions and optimizer as a full dataflow graph, which is the representation of the neural network

Auto-differential Libraries then take over

- Build forward dataflow graph and backward gradient flow graphs automatically
- Perform training and apply updates

## Summary: Static Declaration

- Users build a dataflow graph
- Frameworks analyze and optimize the graph
  - Automatically derive the backward graph
  - Incorporate some optimization if desired
- Perform training iteratively (via SGD)

Perform graph-level optimization over D (optionally)

/* (a) static declaration */
// all samples must share one graph
declare a static data flow graph 𝒟.
for t = 1 → T:
  read the tth data batch {x_i^t}_{i=1}^K.
  batched computation: 𝒟({x_i^t}_{i=1}^K).

## Summary: Static Declaration

- Static Declaration *seems to be* a dominant choice for programming deep learning models
  - Good for **static** workflows: define once, run for arbitrary batches/data
  - Easy to parallelize/batching for a fixed graph
  - Easy to optimize: a lot of off-the-shelf optimization techniques for graph

## Introduction to Dynamic Neural Networks

- Deep Learning has been applied on more structured data
- The neural network compute following a data-dependent structure, in order to encode the structure information
  - Sequences, Trees, Graphs
- E.g. Recurrent Neural Networks and their variants
  - Sequence RNN in machine translation, video understanding
  - Tree RNN in sentence parsing and sentiment analysis
  - GraphRNN in social network/image segmentation

![](img/cb490ed30bca4eda5fbba81c52a2c173_211_0.png)

## Dynamic Neural Networks

- The dynamics of the NNs come from multiple dimensions
  - Variably sized inputs
  - Variably sized outputs
    - e.g. in machine translation, input/output sentences have different length across samples
  - Variably structured inputs/outputs
    - e.g. in image segmentation/social network, input and output are differently structured graphs.
  - Nontrivial inference algorithms
    - e.g. in graph NNs, the inference path is dependent on the structure of the input data
- The NN architecture used to handle structured data would change with the input sample
  - i.e. *Dynamic Neural networks*

## Static Declaration for Dynamic Dataflow Graphs

- They are very commonly adopted, but are they good?
  - Unable to express structures beyond sequences
  - Usually yield unnecessary (extra) computation, which wastes computational resources
- More problems
  - Difficulty in expressing complex flow-control logic
  - Complexity of the computation graph implementation
  - Difficulty in debugging

## Outline

- Deep Learning as Dataflow Graphs
- Auto-differential Libraries
- Static Declaration and Dynamic Neural Networks
- **Dynamic Declaration and DyNet**
- Cavs

![](img/cb490ed30bca4eda5fbba81c52a2c173_215_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_217_0.png)

## Dynamic Declaration

- Static Declaration vs. Dynamic Declaration
  - Move the graph declaration and construction (and optimization) from outside of the loop to inside the loop
  - Perform single instance training because it is hard to batch

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

## Dynamic Declaration: Existing Frameworks

- Dynamic Declaration
  - Imperative (instance evaluation)
    - Chainer (Preferred Networks Inc.), PyTorch (Facebook)
  - Symbolic (Lazy evaluation): **DyNet (Petuum Inc.)**

![](img/cb490ed30bca4eda5fbba81c52a2c173_218_0.png)

## Introducing DyNet

- Designed for dynamic deep learning workflow, e.g.

## Words

![](img/cb490ed30bca4eda5fbba81c52a2c173_219_0.png)

## Sentences

![](img/cb490ed30bca4eda5fbba81c52a2c173_219_1.png)

## Phrases

![](img/cb490ed30bca4eda5fbba81c52a2c173_219_2.png)

## Documents

This film was completely unbelievable.
The characters were wooden and the plot was absurd.
That being said, I liked it.

![](img/cb490ed30bca4eda5fbba81c52a2c173_220_0.png)

## DyNet is Optimized for Dynamic Declaration

- Key Ingredients
  - Separate parameter declaration and graph construction
  - Declare trainable parameters and construct models first
  - Construct computation graphs
  - Conclusion: Define parameter once, but define graphs dynamically depending on inputs → therefore making the graph construction lighter-weight

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

## Outline

- Deep Learning as Dataflow Graphs
- Auto-differential Libraries
- Static Declaration and Dynamic Neural Networks
- Dynamic Declaration and DyNet
- **Cavs**

![](img/cb490ed30bca4eda5fbba81c52a2c173_223_0.png)

## Dynamic Declaration: Advantages

- Dynamic declaration has one major advantages
  - Flexibility: it can express *arbitrarily dynamically structured* networks by declaring as many as dataflow graphs as the number of training data

```
/* (b) dynamic declaration */
for t = 1 → T:
    read the tth data batch {xᵢᵗ}ᵢ₌₁ᴷ.
    for k = 1 → K:
        declare a data flow graph Dᵢᵗ for xᵢᵗ.
        single-instance computation: Dᵢᵗ(xᵢᵗ).
```
