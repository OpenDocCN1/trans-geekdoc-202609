| Methods | Indian Pines | Salinas | Pavia Center | Pavia University |
|---|---|---|---|---|
| DAN + neural network | **90.90** ±0.06 | _95.52_ ±0.03 | **99.59** ±0.23 | **96.72** ±0.12 |
| DBN + neural network | _90.31_ ±0.17 | **96.02** ±0.13 | _99.50_ ±0.13 | _95.89_ ±0.08 |
| PCA + linear regression | 66.76 ±0.16 | 93.14 ±0.07 | 99.13 ±0.03 | 93.48 ±0.07 |
| PCA + naive Bayes | 62.11 ±0.21 | 90.35 ±0.10 | 96.06 ±0.09 | 83.2 ±0.13 |
| PCA + decision tree | 68.18 ±0.16 | 89.32 ±0.08 | 97.57 ±0.05 | 88.78 ±0.02 |
| PCA + SVM | 68.77 ±0.23 | 93.35 ±0.22 | 99.16 ±0.05 | 93.3 ±0.15 |
| ICA + linear regression | 68.26 ±0.16 | 93.51 ±0.07 | 99.32 ±0.03 | 93.69 ±0.07 |
| ICA + naive Bayes | 66.41 ±0.21 | 93.44 ±0.10 | 99.38 ±0.07 | 85.94 ±0.09 |
| ICA + decision tree | 59.71 ±0.18 | 90.47 ±0.09 | 96.02 ±0.05 | 87.87 ±0.13 |
| ICA + SVM | 68.26 ±0.22 | 93.51 ±0.22 | 99.32 ±0.28 | 93.3 ±0.21 |

remote sensing applications, the lack of labeled training data degrades the performance of supervised approaches.

With algorithm-level and hardware-level optimization, the DANoC coprocessor achieves competitive performance with the state-of-the-art hardware implementations [27–29,45]. In our hardware experiments, the performance of the DANoC system is estimated using the number of multiplications required in a standard Deep Belief Network. Two versions of DANoC systems are implemented using the Zynq7Z020 and Zynq7100 FPGA devices. As shown in Table 7.4, the low-cost Zynq7Z020 DANoC achieves high performance of 615 to 841 giga-operations-per-second-per-watt, which allows the DANoC chip to process 31.2 to 53.9 thousand hyperspectral samples per second. The peak performance achieved by the Zynq7100 DANoC chip is 2077 effective giga-operations-per-second, which is the state-of-the-art among the latest FPGA-based hardware implementations (Table 7.5). The high performance is achieved at less than 2