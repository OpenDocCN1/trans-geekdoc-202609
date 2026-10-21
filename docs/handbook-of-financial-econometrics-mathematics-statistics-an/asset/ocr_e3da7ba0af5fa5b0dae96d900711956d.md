frequency. At least 60% executing time reduction on this calibration is obtained under the Matlab computational environment. This finding enables the disclosure of an instant market change so that a real-time surveillance for financial markets can be established for either trading or risk management purposes.

# Keywords

GPU • Parallel computing • Matlab • Computational finance • Implied volatility • High frequency data.

# 39.1 Introduction

The central processing unit (CPU) contains multiple and powerful cores. Each CPU core is optimally designed for serial processing. In contrast, the graphic processing unit (GPU) may consist of hundreds or thousands of cores. These cores are highly structured for parallel processing. See a pictorial comparison of the structure between CPU and GPU in Figure 39.1.

In comparison to the longer history of CPU, GPU is a new and revolutionary device to accelerate computational performance. First manufactured by Nvidia in 1999, GPU was designed for computer graphics rendering. After Nvidia launched GPU’s low-end programming language — Compute Unified Device Architecture (CUDA) in 2006, scientists and engineers have found that many heavy computational tasks can be significantly improved by GPUs.

GPU computing refers to the use of CPU together with GPU for fast computation by offloading parallel portions of the numerical algorithm to the GPU, while serial portions of the algorithm to the CPU. When a computational task is massively paralleled, the cooperative GPU computing may

![](bbox=[0.22, 0.65, 0.8, 0.88])

Figure 39.1: Comparison of the number of cores on a CPU system and a GPU system. Resource: Nvidia.