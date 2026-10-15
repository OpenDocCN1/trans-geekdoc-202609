
| SMP || 153.474 || 213.961 || 1214.223 || — || — || — || — || — || — || — || — || — || — || — || — || — |

| SMP-PG || 167.077 || 214.115 || 555.102 || 1.234 || — || — || — || — || — || — || — || — || — || — || — || — |

| HY || 41.067 || 3.143 || 315.671 || — || 0.041 || 0.003 || 0.810 || — || 0.547 || 0.074 || 10.453 || — || 16.168 || 20.954 || 339.713 || — |

| HY-PG || 3.293 || 0.125 || 1.211 || 0.464 || 0.469 || 0.019 || 1.619 || 0.044 || 0.816 || 0.079 || 3.898 || 0.064 || 32.905 || 34.464 || 256.029 || 0.642 |

| HY, P[S]\=1 || 16.168 || 6.108 || 339.713 || — || 0.041 || 0.003 || 0.810 || — || 1.165 || 0.098 || 22.266 || — || 8.949 || 11.037 || 173.698 || — |

| HY-PG, P[S]\=1 || **17.731** || **6.019** || **120.913** || 0.642 || **0.896** || **0.040** || **2.277** || 0.044 || **1.223** || **0.099** || **4.695** || 0.247 || **8.338** || **11.091** || **128.696** || 0.642 |

### 3.4.7 Summary

Motivated by the analyses showing that a significant amount of energy can be saved by designing a specialized memory design, the *DESCNet* SPM architecture is proposed. Different architecture designs are explored to minimize the off-chip memory accesses while efficiently feeding the data to the hardware accelerator executing CapsNets inference at high throughput. Its application-driven memory power management unit further reduces the leakage power. To enable the CapsNets deployment on even smaller resource- and memory-constrained edge devices, low-precision computations can be enabled by weight and feature map quantization, as demonstrated in [Section 3.5](#chapter3.xhtml#sec3_5).

## 3.5 Q-Capsnets: a Specialized Framework for Quantizing Capsnets

CapsNets require intense computations and are difficult to be deployed in their original form on resource-constrained edge devices. This section presents *Q-CapsNets*, the first specialized framework for quantizing CapsNet models, to enable their efficient edge implementations. We evaluate our framework for several benchmarks. On the DeepCaps for the CIFAR10 dataset, the framework reduces the memory footprint by 6.2×, with only 0.15% accuracy loss. Our methodology is desirable for employing CapsNet inference at the edge, because it significantly reduces the computational workload and the CapsNet memory footprint, with minimal accuracy loss.

### 3.5.1 System Overview

Reducing the wordlength of weights and feature maps is extremely important for improving the energy efficiency. A too short wordlength lowers the accuracy of the CapsNets. It is typically an undesired outcome from the end-user perspective. To find an efficient tradeoff between the memory footprint, the energy consumption, and the classification accuracy, we propose the novel Q-CapsNets framework (see [Figure 3.46](#chapter3.xhtml#fig3_46)). It explores different layer-wise and operation-wise arithmetic precisions to obtain the quantized version of a given CapsNet, with maximum accuracy tolerance and memory budget specified as constraints to the framework. Our approach optimizes in particular the dynamic routing, a peculiar feature of the CapsNets involving iterative and computationally expensive operations, with a significant impact on the energy consumption.

![Figure 3.46: An overview of our quantization framework.](images/fig3_46.jpg)

[Figure 3.46:](#chapter3.xhtml#b3fig3_46) An overview of our quantization framework.

**In this section, our novel contributions are:**

*   We propose a specialized framework for systematically quantizing CapsNets, given a certain accuracy tolerance (compared to the full-precision CapsNet) and a certain memory budget for storing the weights.

*   Since an expensive part of CapsNets is the dynamic routing process, we further specialize in the search for the numerical precision for the operations of the dynamic routing. *A key advantage of using our framework*, compared to traditional DNN quantization methods, is that, as we will demonstrate in our experiments, *the number of bits for routing capsules can be further reduced* compared to the wordlengths of the other operations.

*   We test our framework on the CapsNet model \[[236](#refbib.xhtml#refbib236)\] on the MNIST and Fashion-MNIST datasets, and on the DeepCaps model \[[220](#refbib.xhtml#refbib220)\] on the MNIST, FashionMNIST, and CIFAR10 datasets. For the latter dataset, the memory footprint is reduced by 6.2× with an accuracy loss of 0.15%.

### 3.5.2 Analysis of Area and Energy Consumption for Reduced Wordlength

Our overarching goal is to deploy CapsNets at the edge. The floating-point representation is abandoned by adopting a lighter fixed-point representation. Such a wordlength reduction of the weights and activations of a CapsNet for computing the inference lightens the memory storage requirements. It might also significantly impact the energy consumption of the computational units. Therefore, we analyze energy consumption and area footprint of a MAC unit, which is the basic block of specialized CapsNet accelerators like the CapsAcc, and of hardware blocks that perform computationally complex operations, i.e., *squash* and *softmax*, which are needed during the CapsNet inference. Moreover, we design different versions of a MAC unit, a softmax module, and a squash module, varying their wordlength. We synthesize them in a 45nm CMOS technology with the Synopsys Design Compiler tool to measure their area and energy consumptions. [Figure 3.47](#chapter3.xhtml#fig3_47) shows that *the area and energy consumption of MAC units quadratically decrease w.r.t. the wordlength*. Such analyses motivate us to focus on minimizing the wordlength to reduce the energy consumption. The results shown in [Figure 3.48](#chapter3.xhtml#fig3_48) are obtained by varying the number of fractional bits while keeping a single bit for the integer part. As expected, *the softmax and the squash functions require more energy and area than a simple MAC operation*. The dependence on energy consumption and area footprint is related quadratically to the number of fractional bits. This effect further motivates us to reduce the number of bits used to execute the various operations of the CapsNet architectures.

![Figure 3.47: Energy consumption and area footprint for a fixed-point MAC unit with different wordlengths.](images/fig3_47.jpg)

[Figure 3.47:](#chapter3.xhtml#b3fig3_47) Energy consumption and area footprint for a fixed-point MAC unit with different wordlengths.

![Figure 3.48: Energy consumption and area footprint for fixed-point modules performing (a) the softmax and (b) the squash operations with different wordlengths.](images/fig3_48.jpg)

[Figure 3.48:](#chapter3.xhtml#b3fig3_48) Energy consumption and area footprint for fixed-point modules performing **(a)** the softmax and **(b)** the squash operations with different wordlengths.

### 3.5.3 Rounding Schemes

A fixed-point number has an integer part *QI* and a fractional part *QF*. Hence, it can be written as ⟨*Q**I**. *Q**F*⟩. The total number of bits, i.e., the wordlength *N*, is computed as *N**I** + N**F**, which is the sum between the bits of the integer part and the fractional part. A fixed-point representation has precision *ϵ* = 2^( − *N**F*)**, and its corresponding range of representable numbers, in a two's complement format, is \[ − 2^(*N**I** − 1), 2^(*N**I** − 1) − 2^( − *N**F**)].

The *rounding operation* converts a floating-point or a large fixed-point number into a fixed-point number with shorter wordlength. Next, we present the most common rounding schemes.

The **Truncation (TRN)** simply removes all the extra digits from the fractional part, i.e., *x*[*q*] = ⌊*x*⌋. If we assume uniformly distributed numbers, the truncation introduces a negative average error (bias), defined as *x*[*q*] − *x*.
