# CNN agnostic accelerator design 181

Ristretto [8], which is an automated CNN-approximation tool that explores different quantization schemes and can be used to compress and fine-tune learned models. Caffe's tool-set is written in python with pyc interfacing and only requires Caffe's prototxt and caffodel as inputs. First, Ristretto is used to analyze and generate static or dynamic fixed-point quantization schemes for each layer. The quantization results are used to generate modified CNN weights which are transferred once to FPGA board DRAMs. A parser extracts layer attributes from the prototxt which are used by architecture optimizer along the quantization results from Ristretto. It generates optimized hardware and software configuration, tiling factors and the required host and device library files. Following this, the OpenCL compiler takes over and generates the FPGA binary. Finally, the same binary can be used to accelerate specific or multiple networks accordingly.

# 8.9 Performance evaluation

To verify the computation model, we implement FICaffe on a DE5-Net board with a Stratix V GXA7 FPGA, 4 GB DDR3 DRAM @ 800 MHz and PCI-E Gen3 x8 interface with the host PC. Our host is a 6-Core Intel's Xeon CPU E5-2603 v3 @ 1.60 GHz, with 16 GB RAM. Intel's OpenCL SDK v16.0 is used to synthesize the libraries. The board uses the PCI-E port along with an external power supply.

# 8.9.1 Optimizer results

# 8.9.1.1 Latency estimation model

Table 8.3 shows of total estimated cycles and its distribution for each stage along with actual number of cycles by Intel's OpenCL SDK Profiler for different layers of GoogleNet*. It can be observed that layers of size 3 x 3 and have enough computation to avoid any intermediate memory stalls with a small overhead. FCL and FCLs with 1 x 1 filter, in contrast, are memory bound as the total_cycles is dominated by mem_ldst_cycles of stage 4. Due to our restructuring of FCLs, all memory stays only in weight cycles and N_iter becomes 1 for FCLs

Table 8.3 Estimated vs measured execution cycles for chosen GoogleNet layers (<Tn,Tm,Tr,Tp)= 4, 48, 13)

| Filter | Size | Stage 1 | Stage 2 | Stage 3 | Stage 4 | Stage 5 | Total (8.24) | Measured % Error |
|---|---|---|---|---|---|---|---|---||
| CL (7 x 7 x 3, 2) | 56 × 56 | 8,050 | 1,123 | 1,229,312 | 78,214 | 784 | 1,239,269 | 1,240,217 | 0.07 |
| CL (5 x 5 x 32, 1) | 28 × 28 | 608 | 1,146 | 313,600 | 28,128 | 364 | 315,718 | 324,062 | 2.56 |
| CL (3 x 3 x 96, 1) | 28 × 28 × 128 | 510 | 1,856 | 508,032 | 122,062 | 364 | 510,762 | 526,101 | 2.92 |
| CL (1 x 1 × 192, 1) | 28 × 28 × 128 | 420 | 138 | 37,632 | 93,294 | 364 | 94,216 | 98,136 | 3.99 |
| FCL (1,024 × 1,000) | | | 1 | 10,731 | 5,376 | | 1 | 16,109 | 16,085 | 0.15 |

*We separate versions of library files with the same structure but synthesized as task parallel interest of author instantiating profiling counters.