
3. `设计空间探索 (DSE)`，用于自动获得我们 *DESCNet* 记忆体架构中不同关键参数的 Pareto 最优值。它在内存、面积和能耗之间利用权衡，同时利用 CapsNet 推理各步骤的不同处理行为。

4. `面向应用的记忆体功率管理`：它利用加速器的结构参数、CapsNet 推理的处理流以及与记忆体的接口，设计分区级电源门，以降低静态功耗。

5. `硬件实现与评估`：在 45 nm CMOS 技术中，使用 Synopsys 工具和 CACTI‑P 的 ASIC 设计流程，对包含集成 *DESCNet* 记忆体的完整 CapsNet 架构进行硬件实现与评估。我们对 CapsNet 的芯片内存架构共 15 233 种可能配置以及 DeepCaps 的 215 693 种配置进行面积和能耗评估，并将其与 CapsAcc 记忆体设计进行对比。

![Figure 3.23: Overview of our DESCNet Memory Design Methodology.](images/fig3_23.jpg)

[Figure 3.23:](#chapter3.xhtml#b3fig3_23) Overview of our *DESCNet* Memory Design Methodology.

### 3.4.2 Required Architectural Modification and Key Research Question

To overcome the limitation of having large on‑chip memory in the baseline CapsAcc architecture ([Figure 3.24a](#chapter3.xhtml#fig3_24)) and toward real‑world edge implementations, we employ a modified CapsNet hardware architecture that features a memory hierarchy consisting of an on‑chip SPM and an off‑chip DRAM, as shown in the blue boxes of [Figure 3.24b](#chapter3.xhtml#fig3_24), respectively.

![Figure 3.24: Architectural view of the CapsNet inference accelerator. (a) Baseline architecture in CapsAcc. (b) Modified architecture for this work with off‑chip and on‑chip memory partitioning, which is more practical for embedded implementations.](images/fig3_24.jpg)

[Figure 3.24:](#chapter3.xhtml#b3fig3_24) Architectural view of the CapsNet inference accelerator. **(a)** Baseline architecture in CapsAcc. **(b)** Modified architecture for this work with off‑chip and on‑chip memory partitioning, which is more practical for embedded implementations.

Such a design can generalize the problem for diverse applications and CapsNet architectures. However, considering such a memory hierarchy, the challenge then lies in designing and managing the on‑chip memory such that (i) the off‑chip memory accesses are minimized, (ii) the reuse of intermediate data and weights stored in the on‑chip memory is exploited at the maximal, and (iii) the unnecessary parts of the on‑chip memory can be power‑gated in some scenarios of varying memory accesses without reducing the performance of CapsNets processing. These problems have not been studied for the CapsNets hardware yet. *Toward this, we aim at investigating the following key questions when determining the memory sizes and the communication between off‑chip and on‑chip memories.*

1. `How` to minimize the off‑chip memory accesses to reduce energy consumption? Every data is read from or written to the off‑chip memory only once, while used once or multiple times in the on‑chip memory.

2. `How` to keep the latency and throughput *similar/close* to the case of having all the memory on‑chip, i.e., hiding the off‑chip latency as much as possible? *This can be guaranteed by prefetching the data to the on‑chip memory to mask the off‑chip memory latency, assuming that the on‑chip memory is large enough to contain all the necessary data.*

3. `How` to minimize the on‑chip SPM size to reducing the leakage? What would be the appropriate design tradeoffs?

4. `How` can we design efficient power‑gating for the on‑chip SPM to save the leakage power for the unused sectors?

5. `Can` we exploit the unique processing and data reuse characteristics of CapsNets to optimize the corresponding memory access profiles?

Since the above‑discussed challenges can pose contradicting requirements and constraints, in‑depth analyses of the resource requirement and usage patterns of CapsNets processing are needed before making appropriate design decisions, which we discuss in the following [Section 3.4.3](#chapter3.xhtml#sec3_4_3).

### 3.4.3 Resource Analysis of CapsNet Inference

First, we investigate Google's CapsNet architecture \[[236](#refbib.xhtml#refbib236)\] which performs MNIST \[[118](#refbib.xhtml#refbib118)\] classification, using the architectural organization presented in [Figure 3.24b](#chapter3.xhtml#fig3_24). We analyze the performance and the on‑chip memory requirements for different operations of the CapsNet inference, showing their on‑chip read and write accesses. Afterward, we analyze the DeepCaps \[[220](#refbib.xhtml#refbib220)\] for the CIFAR10 \[[112](#refbib.xhtml#refbib112)\] classification, showing that the accumulators have the highest contributions in memory usage and accesses. Meanwhile, the energy breakdown analysis shows the respective contributions of the accelerator and the memories. Our experiments obtain the same classification accuracy as for the CapsNet on the MNIST dataset and for the DeepCaps on the CIFAR10 dataset, i.e., 99.67% and 92.74%, respectively.

#### 3.4.3.1 Performance and Memory Analyses for the Google's CapsNet on the MNIST Dataset

**Memory Usage Analysis:** In [Figure 3.25](#chapter3.xhtml#fig3_25), we analyze the on‑chip memory requirements for each operation of the CapsNet inference. The dashed lines represent their maximum values. Note, unique operations (like *ClassCaps, Sum, Squash, Update* and *Softmax*) of Google's CapsNet \[[236](#refbib.xhtml#refbib236)\] inference mapped onto the *CapsAcc* accelerator exhibit different memory utilization profiles compared to when mapped to a memory architecture designed for the traditional DNNs like the TPU \[[100](#refbib.xhtml#refbib100)\]. The overall size can be chosen by the operation that requires the largest amount of memory (i.e., the *PrimaryCaps* layer). For this configuration, the on‑chip SPM is composed of the data, weight and accumulator memories. This analysis unleashes the available optimization potential for improving the memory energy efficiency when designing a specialized memory architecture for CapsNet accelerators.

![Figure 3.25: Memory utilization of Google's CapsNet inference, mapped on a specialized CapsNet accelerator (*CapsAcc*) and TPU. The bars represent the on‑chip memory usage. The dashed lines show the maximum requirement.](images/fig3_25.jpg)

[Figure 3.25:](#chapter3.xhtml#b3fig3_25) Memory utilization of Google's CapsNet inference, mapped on a specialized CapsNet accelerator (*CapsAcc*) and TPU. The bars represent the on‑chip memory usage. The dashed lines show the maximum requirement.

**Performance Analysis:** [Figure 3.26a](#chapter3.xhtml#fig3_26) presents the execution time (i.e., number of clock cycles) of different operations involved in the CapsNet inference. Note that the dynamic routing operations contribute to more than half of the execution time of the complete CapsNet inference. Overall, the performance is 116 frames‑per‑second (FPS) for the CapsAcc accelerator. Suppose we combine the results of [Figures 3.25](#chapter3.xhtml#fig3_25) and [3.26a](#chapter3.xhtml#fig3_26). In that case, we notice that, potentially, a significant amount of leakage energy can be saved by the power‑gating part of the on‑chip memory when the utilization is below 100%. We leverage this observation to develop an application‑specific power management policy for memories of the CapsNet Accelerators, as discussed in [Section 3.4.4](#chapter3.xhtml#sec3_4_4).

![Figure 3.26: Clock cycles for different inference operations in (a) CapsNet for the MNIST dataset; (b) DeepCaps for the CIFAR10 dataset.](images/fig3_26.jpg)

[Figure 3.26:](#chapter3.xhtml#b3fig3_26) Clock cycles for different inference operations in (**a**) CapsNet for the MNIST dataset; (**b**) DeepCaps for the CIFAR10 dataset.
