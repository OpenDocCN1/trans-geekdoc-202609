
matrix, and so these output terms be computed independently of one another.

- 3. The model parameter values are fixed and known at run-time. This opens up the opportunity for various compression schemes and quantization approaches, which reduce the amount and size of the parameters in memory.
- 4. In addition to the number of computations being fixed, the order in which they are performed, and thus the order in which data is accessed, can be fixed. Having a predictable data-access pattern allows memory operations to be optimized, either through the interface to off-chip DRAM or in the properties of on-chip SRAM.

Once an architecture is developed, the process of designing digital hardware involves writing in a hardware description language (HDL) to describe the structure and behavior of a circuit. Unlike most software languages, which describe a sequential procedure to be executed by a CPU, an HDL adopts a concurrent model of computation, i.e., describes operations being done in parallel. The process of writing and testing HDL can be both difficult and time-consuming, requiring a special skill set and domain knowledge. Because of this, designing custom hardware to accelerate inference carries a nonrecurring engineering cost. Additionally, once an ASIC has been fabricated, its design and functionality is fixed. Any modification to the design requires a full re-fabrication cycle and replacement of existing devices, which can be expensive.

Field-programmable gate arrays (FPGAs) present a solution to hardware design that offers more flexibility than an ASIC. These devices contain a large, interconnected array of programmable units, which can be reconfigured to implement complex digital circuits. These programmable units are given different names in products, among them configurable logic blocks (CLBs) the most common. They also contain memory (RAM) and multiply-add units (also known as DSP units) that are connected to the CLBs. The architecture of a typical FPGA is shown in Figure 2.15. While they offer lower energy efficiency and performance than ASICs, they still significantly outperform CPUs and GPUs in energy efficiency (and in some cases performance). In a prior work, it has been shown that the FPGA-based hardware accelerator for a speech recognition application achieved 43× and 197× better speed and energy efficiency, respectively, than a CPU implementation and 3× and 14× better speed and energy efficiency, respectively, than a GPU implementation [17].

The rest of this chapter will present a survey on some recent custom hardware accelerators for the LSTMs model.

## 2.3 Hardware implementation of LSTMs

Several previous studies have addressed the problem of implementing LSTM network inference in a hardware-friendly manner. Complete solutions to this problem should address three issues: reduce the amount of data and parameters by compressing the model, optimize the dataflow for the hardware platform, and finally optimize the memory usage.

## Hardware architectures for deep learning

![](img/e6e752b99eb1621488c89445a57e2a86_65_0.png)

Figure 2.15 FPGA device architecture

### 2.3.1 Model compression

The first step in the design of a hardware architecture is selecting the data format and bit precision of the numbers, and if needed, a model compression strategy. This step determines the required computational elements, the memory requirements, and ultimately the performance and throughput of the system.

Parameter compression can significantly reduce the memory footprint and computational complexity of the inference computations. Several methods have been proposed for neural network model compression. These methods are generally classified into parameter reduction and parameter quantization approaches. The former approach reduces the number of parameters needed to represent the model, while the latter reduces the number of bits needed to represent model parameters.

The pruning technique reduces the number of parameters by removing (i.e., setting to zero) unnecessary weight connections. After training, model parameters with an absolute value below some threshold are removed. Then, the sparse model is retrained using the remaining connections. The retained model may be pruned and retrained again in order to achieve the desired level of sparsity.

Pruning is a well-studied method in feedforward and convolutional neural networks. Using this technique, Han et al. demonstrated 9× and 13× reduction in number of parameters for two well-known convolutional networks [19]. Building upon this approach, Han et al. also proposed a hardware-friendly pruning method,

## Hardware acceleration for recurrent neural networks

called load-balance aware pruning [17]. This method facilitates the distribution of the processing workload by constraining regions of the parameter matrices to contain an equal number of nonzero connections. After pruning, the memory footprint of the model parameters is reduced using sparse encoding methods, such as compressed sparse column (CSC) or compressed sparse row (CSR). Some accelerators have been designed to operate directly on sparse encoded models and efficiently skip zero-valued connections [17,18].

Singular value decomposition (SVD) is another technique for reducing the number of model parameters. By keeping just the largest values, the dimensionality of parameter matrices can be reduced while maintaining an acceptable level of accuracy. In [20], SVD is applied to a fully connected layer of a convolutional network and achieved a compression rate of 7x with only a 0.04% loss in prediction accuracy. In [21], this technique is applied to a five-layer LSTM for speech processing and reduced the model size by 3x with only a 0.5% loss in prediction accuracy. An advantage of this approach is that it does not require special encoding (and consequently memory) to store the compressed model; this translates to simplified accelerator architecture because the parameter structure does not have to be decoded.

A common technique to quantify parameters is weight sharing. With this, a small number of effective weight values are identified using k-means clustering. The cluster. After training, similar weights are identified using [19]. The centroid of a cluster is then chosen to be the shared weight value. The quantized model can then be retrained using only the shared weights. This technique allows parameter matrices to be stored as indices into the shared weight codebook, thus reducing the memory footprint. For example, weight sharing with 32 shared weights requires only 5 bits to enable on-chip parameter storage in their hardware accelerator for fully connected layers [18]. A benefit to this approach is that it does not restrict the datatype of the actual weights; high-precision datatypes be used for computation with minimal storage requirements.

Another quantization technique is binary (+1 or -1, this method constrains all weight values during training requiring only a single bit to represent. An extension of this technique applies the same quantization on layer activations. Various approaches have been proposed for training a neural network with binary weights and activations [22–24]. The approach detailed in [24] was applied to an LSTM for text prediction and resulted in better performance and performance efficiency with negligible loss in prediction accuracy, compared with that of the full-precision model. Binarization comes with significant advantages for hardware implementation. In a weight-only binary scheme, multiplication is reduced to a two’s complement operation, thus eliminating the need for expensive hardware multipliers. Weight and activation binary simplify hardware implementation further, requiring only XNOR and bit-count operations in place of multiplicity accumulations. In both schemes, model parameter size is drastically reduced.

For many deployed deep learning applications, both time and power consumption is off-chip memory access. Han et al. propose a three-stage model compression and quantization method that dramatically reduces the
