# ## 2.1 Magma GEMM Stencil structure

The developed autotuning approach is based on the well-known MAGMA GEMM kernel. The original kernel implementation has been described in [12] and is characterized by an extensive GPU kernel parameter space. Algorithm 1 shows the pseudo-code of the kernel. The kernel has 11 parameters - two of the kernel parameters are only relevant for calculations in complex number space. Therefore the kernel parameter space is reduced to nine relevant kernel parameters - the parameters are described in the following:

*Blocksizes* The Blocksizes BLK\_M, BLK\_N and BLK\_K define how many elements a Threadblock will calculate.

*Threadblock dimensions* The Threadblock dimensions DIM\_X and DIM\_Y determine the size of the Threadblock, which calculates a block on the result matrix.

*Subdimensions* The Subdimensions DIM\_XA, DIM\_XB, DIM\_YA and DIM\_YB determine how the Shared Memory(SMEM) is filled.

# **Algorithm 1: GEMM Kernel Algorithm (simplified)**

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

# ## 2.2 Reducing search space

To reduce the search time for finding optimal kernel parameter sets in the first step it is necessary to eliminate parameter sets, which with respect to the underlying GPU hardware layout are not possible and possibly lead to an unstable behaviour of the kernel execution. The following parameters are reduced:

**prelimitations** We started with reducing the viable threadcounts respectively the threadblock dimensions. The threadblock dimensions(DIM\_X, DIM\_Y) can only be 8, 16 or 32 resulting in 64, 256, 512 or 1024 threads. The GPU manufacturer NVIDIA recommends using a minimum of 64 threads [20], which is the lower limit we are applying, the upper limit is given by the hardware specification of the GPU. Other configurations will not map onto the GPU hardware.