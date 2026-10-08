
![](img/bd21298357d8484151447cff0b2f138b_341_0.png)

Figure 10.15 – Uniform and non-uniform quantization

Quantization can be performed both post-training and during training (quantization-aware training). Post-training quantization takes a trained model, quantizes the weights, and regenerates a quantized model. Quantization-aware training involves fine-tuning a full precision model. During training, the higher precision real numbers are reduced to lower precision numbers.

Quantization support is natively available in DL frameworks, such as PyTorch and TensorFlow. For example, PyTorch supports both forms of quantization via its torch.quantization package. TensorFlow supports quantization through the tf.lite package.

## Pruning (also known as sparsity)

Pruning is another network compression technique that eliminates some of the model weights and neurons that do not impact model performance to reduce the size of the model to make inference faster. For example, weights that are close to zero or redundant can usually be removed.

Pruning techniques can be classified into static and dynamic pruning. Static pruning takes place offline before the model is deployed, while dynamic pruning is performed during runtime. Here, we will discuss some of the key concepts and approaches for static pruning.

## Advanced ML Engineering

Static pruning mainly consists of three steps:

1. Parameter selection for pruning targeting.
2. Pruning the neurons.
3. Fine-tuning or retraining if needed. Retraining may improve the model performance of the pruned neural network.

There are several approaches for selecting the parameters for static pruning, including the magnitude-based approach, the penalty-based approach, and dropout removal:

- *Magnitude-based approach*: It is widely accepted that large model weights are more important than small model weights. So, one intuitive way to select weights for pruning is to look at zero-value weights or the weights within a absolute threshold. The magnitude of the neural network activation layer can also be used to determine if the associated neurons can be removed.
- *Penalty-based approach*: In the penalty-based approach, the goal is to modify the loss function or add additional constraints so some weights are forced to become zeros or near zeros. The weights that are zeros or close to zeros can then be pruned. An example of the penalty-based approach is using LASSO to shrink the weights of features.
- *Dropout removal*: Dropout layers are used in deep neural network training as regularizers to avoid overfitting. While dropout layers are useful in training, they are not useful for inference and can be removed to reduce the number of parameters without impacting the model's performance.

DL frameworks, as TensorFlow and PyTorch, provide APIs for pruning models. For example, you can use the tensorflow_model_optimization package and the prune_low_magnitude API for magnitude-based pruning. PyTorch provides pruning support via its torch.nn.utils API.

## Graph and operator optimization

In addition to hardware acceleration and model optimization, there are additional optimization techniques that focus on the execution optimization of the computational graph, as well as hardware-specific operator and tensor optimization.

## Graph optimization

Graph optimization focuses on reducing the number of operations that are performed in computational graphs to speed up inference. Multiple techniques are used for optimization, including operator fusion, dead code elimination, and constant folding.

Operator fusion combines multiple operations in a subgraph into a single operation to improve latency. In a typical execution of a subgraph with multiple operations, system memory is accessed for read/write to transfer data between operations, which is an expensive task. Operator fusion reduces the number of memory accesses, as well as optimizes the overall computations since the computations are now happening in a single kernel without intermediate results being saved to memory. This approach also reduces the memory footprint by a smaller number of operations being performed. The following diagram shows the concept of operator fusion:

![](img/bd21298357d8484151447cff0b2f138b_343_0.png)

Figure 10.16 - Graph operator fusion

In the preceding diagram, the **matrix multiplication, add,** and **ReLU** operators are being fused into a single operator for execution in a single kernel to reduce memory access and the time needed to start multiple kernels.

Constant folding is the process of evaluating constants at compile time instead of runtime to speed up processing during runtime. For example, the following expression, A can be assigned to a value of 300 at compile time instead of being dynamically calculated at runtime, which requires a more computational cycle: $A = 100 + 200$. Dead code elimination removes the code that does not affect the program's results. This ensures that the program doesn't waste computation on useless operations.

## Operator optimization

Operator optimization (also known as tensor optimization) focuses on hardware-specific optimization for a specific model. Different hardware devices have different memory layouts and computational units and as such, hardware-specific optimization is often required to take full advantage of the hardware architecture. Multiple techniques have been developed for operator optimization for different hardware devices, including the following:

- Nested parallelism, which takes advantage of the GPU memory hierarchy and enables data reuse across threads through shared memory regions.
- Memory latency hiding, which overlaps the memory operation with computation to maximize memory and compute resources.

While graph optimization, operator optimization, and model optimization address different areas of optimizations, they are often combined to provide end-to-end optimization.

## Model compilers

Manually optimizing end-to-end performance is non-trivial. Adding the dimensions of multiple ML frameworks and a wide range of target hardware devices for optimization makes this a very challenging problem. To simplify the optimization process for different ML frameworks and different devices, several open source and commercial products have been developed. We will briefly talk about a few such packages in this section.

### TensorFlow XLA

TensorFlow Accelerated Linear Algebra (XLA) is a DL compiler for TensorFlow. It compiles a TensorFlow graph into a sequence of execution kernels specifically optimized the model. XLA transforms the original TensorFlow graph into an intermediate representation (IR) before performing several optimizations on the IR, such as operator fusion for faster computation. The output from the optimization step is used for generating hardware-specific code that optimizes the performance of the different target hardware devices, such as CPUs and GPUs. XLA is used at Google in production for many accelerators.

### PyTorch Glow

PyTorch Glow is a DL compiler for multiple DL frameworks. Similar to XLA, it also uses an IR to represent the original computational graph to perform optimizations. Unlike XLA, PyTorch Glow uses two layers of IRs. The first layer is used for performing domain-specific optimizations such as quantization, while the second IR layer is used for memory-related optimization such as memory latency hiding. After the second IR optimization, target device-dependent code is generated for running the models on different devices.

### Apache TVM

Apache Tensor Vital Machine (TVM) is an open source compiler framework for model optimization. It optimizes and compiles models built with different frameworks, such as PyTorch and TensorFlow, for target CPUs, GPUs, and specialized hardware devices for accelerated performance. TVM supports optimization at different levels, including graph optimization and operator optimization targeting specific hardware. It also comes with a runtime for executing the compiled models.

One key feature of TVM is AutoTVM, which uses ML to search for the optimal sequences of code execution for different hardware devices. This ML-based search algorithm can significantly outperform baseline benchmarks by using vendor-provided optimization libraries as cuDNN. This ML-based approach also enables efficient compilation scaling for a large number of hardware devices.

### Amazon SageMaker Neo

Amazon SageMaker Neo is the model compiling feature in SageMaker. It mainly uses Apache TVM as the underlying compiler library. With SageMaker Neo, you can take a model that's trained in different ML/DL frameworks such as TensorFlow and PyTorch, choose the target processors such as Intel, Apple, ARM, and Nvidia, and then SageMaker Neo compiles an optimized model for the target hardware. Neo also provides a runtime library for each target platform to load and execute the compiled model. SageMaker Neo is a managed offering, so you don't need to manage the underlying infrastructure and processes for model compilation and deployment.
