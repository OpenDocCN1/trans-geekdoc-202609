
## 8.9.3 Architecture comparison

FICaffe's performance with state-of-the-art work on AlexNet and VGG Most of the previous works in related literature are throughput oriented and use batching to improve raw throughput numbers. In contrast, FICaffe optimizes the architecture for latency-sensitive applications and does not consider batching. While batching improves the throughput, it increases the latency/image. Therefore, for fairness, we also compare processing efficiency of PEs. Efficiency represents the percentage of runtime that a PE spends in performing arithmetic computations. It also normalizes the effects of underlying FPGA platform and the chip technology node helps compare the architecture on a level field. Efficiency is calculated as

```
PE efficiency = \frac{Ops\ achieved /s/PE}{Throughput/#PEs MaxOps/PE/2\times freq} (8.27)
```

Note that latency is not directly calculated from throughout. Only a lower bound on latency can be inferred from throughput numbers. Further, we intentionally do not compare performance density which is the number of operations done per DSP per cycle, because FICaffe does not take advantage of 2\times18 multiplications on a single Stratix V DSP. This is because Intel's SDK version 16.0 (restrictions from Vendor BSP at that time) is not very effective at analyzing complex OpenCL code to use all multipliers per

### 8.9.3.1 Raw performance improvement

Stratix V GXA7 is a small-to-medium-sized FPGA with only 256 DSPs. Directly comparing the raw latency numbers with bigger chips does not give a clear idea of effectiveness of the FICaffe architecture. Therefore, in Table 8.6, we compare the latest published results for full AlexNet and VGG acceleration on this chip in [13]. We can see that FICaffe achieves more than 2\times better runtime on AlexNet and almost twice on VGG as well.

### 8.9.3.2 Comparison with state-of-the-art

From Table 8.7, we can see that FICaffe is the only design that does not take advantage of CNN-specific optimizations and input batching and is completely OpenCL based. With high flexibility, FICaffe has the best PE efficiency compared to all recent works for VGG. Works presented in [14,16] are optimized specifically to VGG and [4]

Table 8.6 Comparison of inference time/image on Stratix V GXA7

| CNN | FPGA2016 [13] | FICaffe | Speedup |
|---|---|---|---|
| AlexNet | 45.7 ms | 20.59 ms | 2.22x |
| VGG | 651.2 ms | 339 ms | 1.92x |

Table 8.7 FICaffe compared with other designs

| Framework | Precision | Platform | CNN (GOs) | Freq (MHz) | #PE*, #DSPs | #BRAMs | Throughput (GOs) | CNN specific Input batching | Latency (ms) | PE eff (%) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| ICCAD16[16] | Xilinx HLS | fixed, 16 | Kintex KU060 | VGG (30.76) | 150 | 200 | 150 | 2,833,283,000 / 1,248,940 / 354 | No | CL 1, FCL 32 / 2,084.16 | 41.6 | 70.5 |
| FPGA16[16] | RTL | fixed, 16 | Arria-G10 XI150 | VGG (30.76) | 300 | - | 3,136,1,518,518 / 19,002,713 / 645.25 | Yes | No / >47.67 | 68.8 | 62.8 |
| FCCM17[15] | OpenCL+RTL | fixed, 16 | Stratix-V G50MD | VGG (30.76) | 150 | - | 2,048,1,036,590 / 9,192,0,214 / 364.4 | No | Yes | - | 59.3 |
| FPGA17[14] | OpenCL | float, 16 | Arria-G10 XI150 | VGG (30.76) | 303 | - | 2,504,1,536,590 / 2,487,2,713 / 1,382 | Yes | CL 1, FCL 96 / >94.12 | 91.1 | |
| FPGA17[14] | OpenCL~Sys V | fixed, 8-16 | Arria-G10 XI150 | VGG (30.76) | 385 | - | 2,432,2,753,036 / 1,459,2,713 / 1,790 | Yes | No / >17.18 | 84.3 | |
| FICaffe | OpenCL | fixed, 8-16 | Stratix-V GXA7 | VGG (30.76) | 195 | - | 256,256 / 1,539,260 / 70.42 | No | No | 339 | 95.8 |

* Number of PEs mentioned are our best effort for comparison and may not report.

CNN agnostic design: Authors in [14] achieve very high throughput for VGG as they optimize their architecture for only $3\times3$ filters. Additionally, they achieve good processing efficiency without any batching in FCLs, because VGG has $20\times$ more computation than AlexNet. Effect of this is also visible in FICaffe's efficiency for VGG, but unlike [3], we achieve high efficiency without synthesizing IPs. Authors in [4] propose to reduce bandwidth requirement for both CL and FCLs, Their approach is not automated nor scalable like FICaffe, as they manually fix-filter parallelism and perform Winograd for only $3\times3$ filters. Also Gflop/s reported in [4] is not IEEE75 compliant. Like FICaffe, authors in [6] also consider integration with Caffe but only report on AlexNet and VGG. Their main contribution is systematic analysis of input-major and weight-major choices for FCLs and unfortunately, their PE efficiency is poor with batching and has very high latency/image. They use too-filter parallelism by unrolling filter size to $5\times5$. Finally, while the work presented in [5] smaller filters of $1\times1$, do not report actual number of PEs and to the best of our knowledge do not achieve efficiency either. Notice that choice of FPGA impacts the final latency. A larger FPGA with a plethora of resource always yields a better performance. To compare different architectures, one may normalize the achieved latency by available resource.

References

- [1] Mohammad Motamedi, Philipp Gysel, Venkatesh Akella, and Soheil Ghiasi. 2016. Design Space Exploration of FPGA-Based Convolutional Networks. In Design Automation Conference (ASP-DAC), 2016 21st Asia and South Pacific. IEEE, 575–580.
- [2] Mohammad Motamedi, Philipp Gysel, and Soheil Ghiasi. 2017. PLACID: A Platform for FPGA-Based Creation for DCNNs. ACM Transactions on Multimedia Computing, and Applications (TOMM) 13, 4 (2017), 62.
- [3] Chen Zhang, Peng Li, Guangyu Sun, Yijin Yuan, Binjiang Xiao, and Jason Cong. 2015. Optimizing FPGA-Based Accelerator Design for Deep Convolutional Networks. In Proceedings of the 2015 ACM/SIGDA International Symposium on Field-Programmable Gate Arrays. ACM, 161–170.
- [4] Utku Aonton, Shane O'Connell, Davor Capalija, Andrew C. Lin, and Gordon R. 2017. An OpenCL Deep Learning Accelerator on Arria-10. In Proceedings of the 2017 ACM/SIGDA International Symposium on Field-Programmable Gate Arrays (FPGA’17). ACM, New York, USA, 55–64. DOI: http://dx.org/10.1145/3200278.3021738
- [5] Yijin Guan, Hao Liang, Ningyi Xu, et al. 2017. FP-DNN: Automated Framework for Mapping Deep Neural Networks onto FPGAs With RTL-LS Hybrid Templates. In Field-Programmable Custom Computing Machines (FCCM), 2017 IEEE 25th Annual International Symposium on. IEEE, 152–159.
- [6] Chen Zhang, Zhenman Fang, Peipe Zhou, Peichen Pan, and Jason Cong. 2016. Caffeine: Towards Unidirectional Representation and Acceleration for Deep Convolutional Neural Networks. In Computer-Aided Design (ICCAD), 2016 IEEE/ACM International Conference on. 1–8.
- [7] Roberto DiCececo, Griffin Lacey, Jasmina Vasiljevic, Pach Chow, Graham Tlor, and Shawki Araebi. 2016. Caffeinated FPGAs: FPGA Framework For Convolutional Neural Networks. In Field-Programmable Technology (FPT), 2016 International Conference on. IEEE, 265–268.
- [8] Philipp Gys, Mohammad Motamedi, and Soheil Ghiasi. 2016. Restretto: Hardware-oriented approximation of convolutional neural networks. arXiv preprint arXiv:1605.06402
- [9] Alex Krizhevsky, Ilya Sutskever, and Geoffrey E. Hinton. 2012. Image Classification with Deep Convolutional Neural Networks. In Advances in Neural Information Processing Systems 25, F. Pereira, C. J. C. Burges (Eds.). Current Associates, Inc., 1097–1105. http://papers.nips.cc/paper/4824-imagenet-classification-with-convolutional-networks.pdf
- [10] Karen Simonyan and Andrew Zimmer. 2014. Very deep convolutional networks for large-scale image recognition. arXiv preprint arXiv:1409.1556.
- [11] Forrest N Ianda, Song Han, Matthew W Mosk, Khalid Ashraf, William J Dally, and Kurt Keitzer. 2016. SqueezeNet: AlexNet-level accuracy with 50x fewer parameters and <0.5 MB size. arXiv preprint arXiv:1602.07360.
- [12] Christian Stegedy, Wei Liu, Yangqing Jia, et al. 2015. Going Deeper with Convolutions. In Proceedings of the Conference on Computer Vision and Pattern Recognition, 1–9.
- [13] Naveen Suda, Vikas Chandra, Ganesh Dasika, et al. 2016. Throughput-Optimized OpenCL-based FPGA Accelerator for Large-Scale Convolutional Neural Networks. In Proceedings of the 2016 ACM/SIGDA International Symposium on Field-Programmable Gate Arrays. ACM, 16–25.
- [14] Jialang Zhang and Jing Li. 2017. Improving the Performance of OpenCL-Based FPGA Accelerator for Convolutional Neural Network. In Proceedings of the 2017 ACM/SIGDA International Symposium on Field-Programmable Gate Arrays '17. ACM, New York, USA, 25–34. doi: 10.1145/3020078.3021698.
- [15] Jintiao Qiu, Jie Wang, Song Yao, et al. 2016. Going Deeper with Embedded FPGA Platform for Convolutional Neural Network. In Proceedings of the 2016 ACM/SIGDA International Symposium on Field-Programmable Gate Arrays. ACM, 26–35.
