
最突出的 DL 编译器（在框架内置图优化器之外）是 TVM、XLA、Glow、PlaidML 以及各种 MLIR 方言（MLIR 是一个编译器基础设施，支持各种 IR 或方言以及编译器传递）。这些编译器用 C/C++ 编写，以实现速度和可移植性。虽然 TVM 是今天最成熟的编译器，但所有编译器仍处于起步阶段，在工业界的采用有限。随着 DL 硬件浪潮开始进入市场，这在未来几年可能会发生变化，从而增加对稳健编译器的市场需求。[表 9.1](#19_Chapter09.xhtml#tab9-1) 提供了除默认框架编译器之外的主要 DL 编译器各自关键特性的汇总。其他较少见的编译器有 taco、Tensor Comprehension、DLVM、Weld 和 Diesel。[第 9.4 节](#19_Chapter09.xhtml#sub9-4)–[第 9.9 节](#19_Chapter09.xhtml#sub9-9) 讨论了这些编译器及其在工业界的采用情况。

虽然 DL 编译器旨在支持多个前端框架，但它们通常由与现有框架相关的团队开发，该团队首先专注于该框架。特别是，XLA 和 MLIR 方言与 TensorFlow，Glow 与 PyTorch，以及 TVM 与 MXNet。尽管如此，编译器正在扩展其前端支持。

Grappler（TensorFlow 的内置图优化器）、PyTorch JIT、XLA HLO 和 Glow 编译器力求通过目标无关的优化来优化用户程序带来的低效。它们依赖于原始库（如 cuDNN、MIOpen、oneDNN 或 Eigen）或另一个编译器进行目标相关的优化。PlaidML、各种 MLIR 方言和 TVM 支持目标无关和相关的优化以及后端代码生成。

在本章的其余部分，我们回顾 DL 框架，特别关注具有内置图优化器和调度器以执行计算图的 TensorFlow 和 PyTorch。我们还更详细地描述了流行的 DL 编译器。

## 9.1 框架

DL 库或框架为程序员提供定义、训练和部署模型的工具。框架抽象了许多数学和实现细节。例如，它们包含相对于代价函数对模型求导（计算其梯度）的函数或模块，因此程序员无需编写梯度计算代码。虽然不同框架的计算性能因所利用的优化技术而异，但跨框架训练的模型的统计性能本质上是相同的；它们实现了本质上相同的数学算法。

框架将程序编译为图并优化该图。节点使用 C++、CUDA 实现，或使用原始库中可用的预编译目标特定实现。框架还可能使用 DL 编译器来提高执行效率。

最受欢迎的框架是 Google 开发的 TensorFlow 和 Facebook 开发的 PyTorch，两者均用 C++ 编写并具有 Python 包装器。TensorFlow 是工业界最受欢迎的框架，在学术界排名第二。PyTorch 是学术界最受欢迎的框架，在工业界排名第二，并且是增长最快的框架 \[Lor19\]。其他在工业界使用但（基于 Google Trends）在其开发公司之外采用有限的框架有 Apache MXNet、PaddlePaddle 和 Flax/JAX。Amazon（与华盛顿大学、卡内基梅隆大学合作）开发了 MXNet，百度开发了 PaddlePaddle，Google 开发了 Flax/JAX（主要用于研究）。Flax 在 JAX 之上提供高级函数，JAX 是一个 JIT 编译器，使用 Autograd 和 XLA 进行微分并在 CPU、TPU 和 GPU 上执行 NumPy 代码 \[Jax20\]。NumPy 是 Python 的一个库，用于多维张量运算。

TensorFlow 和 PyTorch 提供两种编程范式：命令式编程和声明式（符号式）编程。命令式编程在运行时执行计算，而声明式程序将程序中各种表达式的定义与执行分离。Gluon 和标准前端 MXNet 分别也采用了这些范式。

在本节的其余部分，我们提供了各种框架的简史和采用情况。我们讨论命令式和声明式编程风格及其权衡，以及动态和静态编程。

### 9.1.1 简史与采用情况

框架的受欢迎程度是其可用性和社区支持的一个指标，包括教程数量、可用 GitHub 仓库和讨论论坛。过去几年，开发了许多框架（大多数不再积极维护），例如（按字母顺序）BigDL、Caffe、Caffe2、Chainer、CNTK、CoreML、CXXNET、Dark-Net、DL4J、DSSTNE、DyNet、fast.ai、IDLF、JAX/Flax、Kaldi、Keras、Lasagne、MXNet/Gluon、neon、ONNX RT、PaddlePaddle、PyTorch、Singa、TensorFlow、Theano 和 Torch。

Theano 由蒙特利尔学习算法研究所（MILA）开发，是学术界第一个被广泛采用的框架。Caffe 后来由加州大学伯克利分校开发，并在市场上迅速采用，主要用于计算机视觉任务。几年间，Caffe 是工业界最受欢迎的框架。TensorFlow 发布后不久，TensorFlow 和 Keras（TensorFlow 及其他现已弃用的框架的包装器）就占据了领先地位。Theano 和 Caffe 已不再受支持。Kaldi 是一个用于语音识别研究的 C++ 工具包（支持 DL 和 ML 算法），在该社区中已取得了一些成功，持续数年。

其他超大规模公司试图复制 TensorFlow 的成功：微软使用 CNTK 后来使用 ONNX RT，亚马逊使用 DSSTNE 后来使用 MXNet/Gluon，百度使用 PaddlePaddle。唯一其他广泛的成功是 Facebook 的 PyTorch。今天，市场大多已整合为 TensorFlow 和 PyTorch，MXNet、PaddlePaddle 和 ONNX RT 分别遥遥落后于第三、第四和第五。

### 9.1.2 编程风格：命令式与声明式

ML 库提供两种编程风格：命令式，其中表达式立即执行；声明式，其中程序员首先构建数据流图，然后整个图被优化和执行。TensorFlow v1（没有 v0）采用声明式编程风格设计，PyTorch v0 采用命令式编程风格设计。TensorFlow v2 和 PyTorch v1 为程序员提供这两种风格。

命令式程序在程序执行时执行每个计算。这被称为 `define-by-run` 或动态图，因为模型或图在运行时动态定义，或被称为 `eager execution`，因为程序渴望在程序员请求检查输出时立即计算和评估表达式。供参考，大多数用 Python 编写的代码都是命令式的。

Chainer 于 2015 年采用了命令式编程。PyTorch v0、TensorFlow v2 和 Gluon 后来遵循了 Chainer 的方法。在这些框架中实现函数的（命令式）代码具有相似的特征。

声明式程序首先抽象地（符号地）定义一个函数，没有实际的数值计算。然后程序使用实际的张量值编译和运行。这被称为 `graph programming` 或 `define-and-run`，因为图首先被定义然后执行，或被称为 `lazy execution`，因为程序等待图构建完成并且只执行依赖的表达式，或被称为 `symbolic programming`，因为变量是符号，直到执行时才具有数值。
