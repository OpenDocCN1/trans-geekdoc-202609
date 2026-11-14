
However, those algorithms runtime depend heavily on the input data. Most of the computational time in DLNN is consumed by the convolution step, which is based on a general matrix multiplication (GEMM). In order to accelerate the computational time for DLNN different highly optimized GEMM implementations for Graphic Processing Units (GPUs) have been presented in the last years [1]. In order to achieve a high computational throughput, most of these approaches are based on a hardware specific software kernel implementation of the GEMM algorithm. Usually the different hardware dependent kernel parameters are tuned manually, which involves expertise about the specific GPU architecture. Furthermore the performance of the GEMM kernel is strongly affected by the shape of the input data processed. Different data sizes have a huge impact on the computational runtime of the GEMM kernel due to the different memory layouts of the GPU accelerators.

In order to achieve a maximum performance the parameters of the GEMM algorithm have to be tuned hardware and task specific. In the last years, several autotuning approaches of GEMM kernel parameters have been proposed [2] - the basic idea is to automatically tune a limited number of essential GPU kernel parameters in order to achieve a maximum performance. Usually the approaches do not take into account the size and shape of the given input data, which yields to varying computational runtimes.

The motivation of the presented work is to develop an autotune procedure for GPU based GEMM kernels, which takes into account a comprehensive set of kernel parameters and varying shapes of the data in the input task.

Proposed autotuning solutions such as [2] usually require a lot of computational runtime to find an optimal kernel parameter set. The kernel parameter space e.g. in the MAGMA GEMM kernel [4] is very large and therefore restrictions are made to reduce the search space for the kernel parameters followed by a brute search mechanism. This usually results in high search times for the kernel parameters to be set.

## 1.2 Related Work

Well known autotuning concepts like the Automated Tuned Linear Algebra Software Project (ATLAS) [5] or the Optimized Sparse Kernel Interface (OSKI) [6] focus on the optimization of CPU calculations. There are only a few approaches, which introduce concepts for autotuning GPU kernel parameters [7]. The approaches focus only on a small number of tuning parameters and therefore the achieved performance cannot be reasonably compared to the proposed approach in this work. In order to achieve optimal performance a comprehensive set of GPU kernel parameters have to be taken into account.

In literature there are several more autotuning approaches such as [8, 9]. While the work presented in [8] focuses on 3D TFT, the approach in [9] focuses on sparse matrices and optimizing the GPU kernel based on a statistical model. The concepts presented in [10] and [11] focus on automatic generating GPU kernel code and autotune over different generated kernels. Since the generated code is not optimized with respect to the underlying GPU architecture, usually the performance of these concepts is not optimal.

The presented work in this contribution is based on the well-known MAGMA GEMM kernel. The software implementation is characterized by an extensive GPU kernel parameter space. The MAGMA GEMM kernel has already been investigated in several autotuning approaches [2, 12–16]. The original kernel implementation has been described in [12] and a first autotune concept [13]. With the introduction of the NVIDIA Fermi GPU architecture, the kernel implementation has been revised [14] and an autotuning procedure has been presented in [2]. The approach is characterized by a huge search space for the GPU kernel parameters in conjunction with a brute-force parameter search mechanism, which leads to a high computational effort for finding optimal kernel parameters. With respect to small GEMM operations, in [15, 16] approaches for batched GEMM operations have been presented and [17] describes the utilization of the MAGMA GEMM kernel in machine learning procedures. The autotuning approach presented in [18] focuses on energy efficiency of the GPU while processing GEMM operations.

Most of the presented state-of-the-art work is based on a brute-force approach for determining the optimal GEMM kernel parameters. This usually leads to a huge parameter search space and therefore most of the approaches use a parameter combination pre-elimination step in order to reduce the computational effort. The different heuristics for reducing the search space can possibly dismiss optimal kernel parameter combinations. With respect to these suppositions, the presented work focuses on defining optimal heuristics to reduce the search space in combination with a Simulated Annealing (SA) procedure to find efficiently optimal performing GEMM kernel parameters.

## 2 Solution

Optimal GPU kernel parameters strongly rely on the underlying GPU hardware architecture, the memory layout and the input data size. Different settings lead to different optimal parameter combinations. Therefore the resulting search space for finding the optimal parameter combination can be enormous. Tuning the parameters by hand is impractical, since it has to be redone for every GPU architecture and every set of input data size again. With respect to these suppositions in the following sections we present a two-step autotuning approach for GPU-based GEMM algorithms. In the first step the kernel parameter search space is pruned by several heuristic performance criteria, keeping good performing parameter combinations for a set of different use cases. In the second step based on a modified Simulated Annealing (SA) algorithm the remaining parameter sets are further processed in order to find the best kernel parameter combinations with respect to the GPU architecture and task specific data layout out.

In the following sections, the proposed autotuning approach is presented. In section 2.1, a short overview of the MAGMA GEMM kernel is given; in section 2.2 we explain the developed heuristics for reducing the search space and in section 2.3 the SA approach is introduced.

### 2.1 Magma GEMM Stencil structure

The developed autotuning approach is based on the well-known MAGMA GEMM kernel. The original kernel implementation has been described in [12] and is characterized by an extensive GPU kernel parameter space. Algorithm 1 shows the pseudo-code of the kernel. The kernel has 11 parameters - two of the kernel parameters are only relevant for calculations in complex number space. Therefore the kernel parameter space is reduced to nine relevant kernel parameters - the parameters are described in the following:

- **Blocksizes**: The Blocksizes BLK\_M, BLK\_N and BLK\_K define how many elements a Threadblock will calculate.
- **Threadblock dimensions**: The Threadblock dimensions DIM\_X and DIM\_Y determine the size of the Threadblock, which calculates a block on the result matrix.
- **Subdimensions**: The Subdimensions DIM\_XA, DIM\_XB, DIM\_YA and DIM\_YB determine how the Shared Memory (SMEM) is filled.

### Algorithm 1: GEMM Kernel Algorithm (simplified)

```
Data: Matrix A [M x K], Matrix B [K x N], Matrix C [M x N], alpha,
beta
Result: C=A x B * alpha C + beta * B
load $A_t$ and $B_t$ to SMEM;
for $i \leftarrow 0$ to $K step BLK\_K$ do
  $A_{t+1}$ and $B_{t+1}$ to regs;
  for $i \leftarrow 0$ to $BLK\_K$ do
    load $A_t$ and $B_t$ to REG;
    $C_{temp}=A_t * B_t$
  load $A_{t+1}$ and $B_{t+1}$ to SMEM;
C = $C_{temp}$ * alpha + beta
```

### 2.2 Reducing search space

To reduce the search time for finding optimal kernel parameter sets in the first step it is necessary to eliminate parameter sets, which with respect to the underlying GPU hardware layout are not possible and possibly lead to an unstable behaviour of the kernel execution. The following parameters are reduced:

- **prelimitations**: We started with reducing the viable threadcounts respectively the threadblock dimensions. The threadblock dimensions(DIM\_X, DIM\_Y) can only be 8, 16 or 32 resulting in 64, 256, 512 or 1024 threads. The GPU manufacturer NVIDIA recommends using a minimum of 64 threads [20], which is the lower limit we are applying, the upper limit is given by the hardware specification of the GPU. Other configurations will not map onto the GPU hardware.
