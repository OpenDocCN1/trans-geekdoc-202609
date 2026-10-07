

## 8.9.3 架构比较

FICaffe 在 AlexNet 和 VGG 上的性能与先进工作的对比。相关文献中的大多数工作是以吞吐量为目的，并使用批处理（batching）来提高原始吞吐量数字。相比之下，FICaffe 为延迟敏感型应用优化了架构，并且没有考虑批处理。虽然批处理提高了吞吐量，但它增加了单图像的延迟。因此，为了公平起见，我们还比较了处理单元（PE）的效率。效率代表 PE 执行算术计算的运行时间百分比。它还归一了底层 FPGA 平台和芯片工艺节点的影响，有助于在同一水平上比较架构。效率计算公式如下：

```
PE efficiency = \frac{Ops\ achieved /s/PE}{Throughput/#PEs MaxOps/PE/2\times freq} (8.27)
```

注意，延迟并不是直接从吞吐量计算出的。只能从吞吐量数字中推导出延迟的下限。此外，我们刻意没有比较性能密度（即每个 DSP 每个周期执行的操作数），因为 FICaffe 没有利用单个 Stratix V DSP 上的 2×18 法。这是因为 Intel 的 SDK 16.0 版本（受当时厂商 BSP 的限制）在分析复杂的 OpenCL 代码以使用所有乘器方面非常有效。

### 8.9.3.1 原始性能提升

Stratix V GXA7 是一个中小型 FPGA，仅有 256 个 DSP。将原始延迟数字与更大的芯片直接对比并无法看出 FICaffe 架构的有效性。因此，在表 8.6 中，我们比较了 [13] 中在该芯片上全 AlexNet 和 VGG 加速的最新发布结果。我们可以看到 FICaffe 在 AlexNet 上的运行时间提升了 2 倍以上，在 VGG 上也几乎快了一倍。

### 8.9.3.2 与先进技术的比较

从表 8.7 可以看出，FICaffe 是唯一没有利用 CNN 特有优化和输入批处理且完全基于 OpenCL 的设计。具有高度灵活性，FICaffe 与所有最近的 VGG 工作相比具有最佳 PE 效率。[14,16] 中的工作是专门针对 VGG 优化的。

表 8.6 Stratix V GXA7 上的推理时间比较

| CNN | FPGA2016 [13] | FICaffe | 加速 |
|---|---|---|---|
| AlexNet | 45.7 ms | 20.59 ms | 2.22x |
| VGG | 651.2 ms | 339 ms | 1.92x |

表 8.7 FICaffe 与其他设计的比较

| 框架 | 精度 | 平台 | CNN (GOs) | 频率 (MHz) | #PE* | #BRAMs | 吞吐量 (GOs) | CNN 特有批处理 | 延迟 (ms) | PE 效率 (%) |
|---|---|---|---|---|---|---|---|---|---|
| | | | | | | | | | |
| ICCAD16[16] | Xilinx HLS | fixed, 16 | Kintex KU060 | VGG (30.76) | 150 | 200 | 150 | 2,833,283,000 / 1,248,940 / 354 | No | CL 32 / FCL 96 / >94.12 | 41.6 | 70.5 |
| FPGA16[16] | RTL | fixed, 16 | Arria-G10 XI150 | VGG (30.76) | 300 | - | 3,136,518,518 / 1,002,713 / 645.25 | Yes | No / >47.67 | 68.8 | 62.8 |
| FCCM17[15] | OpenCL+RTL | fixed, 16 | Stratix-V G50MD | VGG (30.76) | 150 | - | 2,048,136,590 / 9,192,014 / 364.4 | No | Yes | - | 59.3 |
| FPGA17[14] | OpenCL | float, 16 | Arria-G10 XI150 | VGG (30.76) | 303 | - | 2,504,153,590 / 2,487,213 / 1,382 | Yes | CL 1, FCL 96 / >94.12 | 91.1 | |
| FPGA17[14] | OpenCL Sys V | fixed, 8-16 | Arria-G10 XI150 | VGG (30.76) | 385 | - | 2,432,753,036 / 1,459,213 / 1,790 | Yes | No / >17.18 | 84.3 | |
| FICaffe | OpenCL | fixed, 8-16 | Stratix-V GXA7 | VGG (30.76) | 195 | - | 256,256 / 1,539,260 / 70.42 | No | No | 339 | 95.8 |

* 提到的 PE 数量是我们的为了比较进行的尝试，可能未报告。

CNN 无关设计：[14] 中的作者为 VGG 实现了极高的吞吐量，因为他们仅针对 $3\times3$ 卷积核优化了架构。此外，他们在 FCL 中不使用任何批处理的情况下实现了良好的处理效率，因为 VGG 的计算量比 AlexNet 多 20 倍。这种影响在 FICaffe 的 VGG 效率中也是可见的，但与 [3] 不同，我们在没有合成 IP 的情况下实现了高效率。[4] 中的作者建议减少 CL 和 FCL 的带宽需求，他们的方法不像 FICaffe 那样自动化或可扩展，因为他们手动固定了滤波器并行，并仅对 $3\times3$ 卷积核执行 Winograd。此外，[4] 中报告的 Gflop/s 不符合 IEEE 标准。像 FICaffe 一样，[6] 中的作者也考虑了与 Caffe 的集成，但只报告了 AlexNet 和 VGG。他们的主要贡献是对 FCL 的输入优先（input-major）和权重优先（weight-major）选择的系统分析，不幸的是，他们的 PE 效率在批处理时很差，且单图像延迟很高。他们通过将滤波器尺寸展开到 $5\times5$ 使用了多滤波器并行。最后，虽然 [5] 展示的工作使用了更小的 $1\times1$ 卷积核，但并未报告实际 PE 数量，且据我们所知，也没有实现效率。注意，FPGA 的选择影响最终延迟。拥有大量资源的较大 FPGA 总是产生更好的性能。为了比较不同的架构，可以根据可用资源对所得延迟进行归一化。

参考文献

- [1] Mohammad Motamedi, Philipp Gysel, Venkatesh Akella, and Soheil Ghiasi. 2016. Design Exploration of Convolutional Networks. In Design Automation (DAC), Asia and South Pacific. IEEE, 575–580.
- [2] Mohammad Motamedi, Philipp Gysel, and Soheil Ghiasi. 2017. PLID: FPGA-based Creation for Deep Learning. ACM Transactions on Multimedia (TOMM) 13, 4.
- [3] Chen Zhang, Peng Li, Guangyu Xiao, Yijin Yan, and Jason Cong. 2015. Optimizing FPGA-based Accelerator for Convolutional Networks. In Proceedings of the 2015 ACM/SIGDA International Symposium on Field-Programmable Arrays. ACM, 16–25.
- [4] Naveen Suda, Vikas Chandra, Ganesh Dasika, et al. 2016. Throughput-Optimized OpenCL-based FPGA Accelerator for Large-Scale Convolutional Networks. In Proceedings of the 2016 ACM/SIGDA International Symposium on Field-Programmable Arrays '17. ACM, New York, USA, 25–34. doi: 10.1145/3020078.3021698.
- [5] Yijin Guan, Hao Liang, Yang Xu, et al. 2017. FP-DNN: Automated Mapping Deep Neural Networks onto FPGAs with Templates. In Computer-Aided Design (ICCAD), IEEE, 1–8.
- [6] Chen Zhang, Griffin Fang, Peichen Pan, and Jason Cong. 2016. Caffe: Unidirectional Representation of Deep Networks. In Computer-Aided Design (ICCAD), IEEE, 1–8.
- [7] Roberto DiCe, Griffin Lacey, Jasmina Vasilvic, Graham Chow, and Shawki Araebi. 2016. Caffe: FPGA Framework for Convolutional Networks. In Field-Programmable Technology (FPT), 25th International Conference. ACM, 26–35.
- [8] Philipp Gys, Mohammad Motamedi, and Soheil Ghiasi. 2016. Hardware-oriented approximation of convolutional networks. arXiv preprint:1605.0642.
- [9] Alex Krizhevsky, Ilya Sutskever, and Geoffrey E. Hinton. 2012. Image Classification with Deep Convolutional Networks. In Advances in Neural Information Systems 25, F. Pereira, C. J. Burges (Eds.). Current Associates, Inc., 1097–1105. http://papers.nips.cc/paper/4824-imagenet-classification-with-convolutional-networks.pdf
- [10] Karen Simonyan and Andrew Zimmer. 2014. Very deep convolutional networks for large-scale image recognition. arXiv preprint:1409.1556.
- [11] Forrest N Ianda, Song Han, Matthew W Mosk, Khalid Ashraf, William J Dally, and Kurt Keitzer. 2016. SqueezeNet: AlexNet-level accuracy with 50x fewer parameters and <0.5 MB size. arXiv preprint:1602.07360.
- [12] Christian Stegedy, Wei Liu, Yangqing Jia, et al. 2015. Going Deeper with Convolutions. In Proceedings of the Conference on Computer Vision and Pattern Recognition, 1–9.
- [13] Naveen Suda, Vikas Chandra, Ganesh Dasika, et al. 2016. Throughput-Optimized OpenCL-based FPGA Accelerator for Large-Scale Convolutional Neural Networks. In Proceedings of the 2016 ACM/SIGDA International Symposium on Field-Programmable Arrays. ACM, 16–25.
- [14] Jialang Zhang and Jing Li. 2017. Improving the Performance of OpenCL-Based FPGA Accelerator for Convolutional Neural Network. In Proceedings of the 2017 ACM/SIGDA International Symposium on Field-Programmable Arrays '17. ACM, New York, USA, 25–34. doi: 10.1145/3020078.3021698.
- [15] Jintiao Qiu, Jie Wang, Song Yao, et al. 2016. Going Deeper with Embedded FPGA Platform for Convolutional Neural Network. In Field Computing Machines (FCCM), ACM, 26–35.

