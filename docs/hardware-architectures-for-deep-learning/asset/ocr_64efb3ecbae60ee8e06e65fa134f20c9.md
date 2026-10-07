# Hardware architectures for deep learning

![](bbox=[0.173, 0.085, 0.826, 0.473])

Figure 2.15 FPGA device architecture

# 2.3.1 Model compression

The first step in the design of a hardware architecture is selecting the data format and bit precision of the numbers, and if needed, a model compression strategy. This step determines the required computational elements, the memory requirements, and ultimately the performance and throughput of the system.

Parameter compression can significantly reduce the memory footprint and computational complexity of the inference computations. Several methods have been proposed for neural network model compression. These methods are generally classified into parameter reduction and parameter quantization approaches. The former approach reduces the number of parameters needed to represent the model, while the latter reduces the number of bits needed to represent model parameters.

The pruning technique reduces the number of parameters by removing (i.e., setting to zero) unnecessary weight connections. After training, model parameters with an absolute value below some threshold are removed. Then, the sparse model is retrained using the remaining connections. The retained model may be pruned and retrained again in order to achieve the desired level of sparsity.

Pruning is a well-studied method in feedforward and convolutional neural networks. Using this technique, Han et al. demonstrated 9× and 13× reduction in number of parameters for two well-known convolutional networks [19]. Building upon this approach, Han et al. also proposed a hardware-friendly pruning method,