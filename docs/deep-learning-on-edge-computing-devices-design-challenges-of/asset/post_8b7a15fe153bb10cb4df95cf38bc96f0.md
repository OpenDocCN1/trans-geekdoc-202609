
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

Table 7.4 Performance of the DANoC hardware prototype.

| Data sets | Number of pipelines | Throughput (thousand samples per second) | Effective performance (GOPS/watt) | Single chip performance (GOPS) | Number of pipelines | Throughput (thousand samples per second) | Effective performance (GOPS/watt) | Single chip performance (GOPS) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| MNIST | 5 | 60.1 | 774 | 381 | 25 | 300.5 | 992 | 1903 |
| Indian Pines | 1 | 31.2 | 615 | 237 | 5 | 156.0 | 714 | 1185 |
| Salinas | 1 | 31.2 | 615 | 238 | 5 | 156.0 | 714 | 1189 |
| Pavia Center | 4 | 53.8 | 833 | 407 | 20 | 215.2 | 1073 | 2036 |
| Pavia University | 4 | 53.9 | 841 | 415 | 20 | 215.6 | 1079 | 2077 |
| Robot Car (sign/road) | 3/3 | 52.5/75.2 | 677 | 319 | 15/15 | 262.5/376.0 | 879 | 1593 |

*表格分为左右两部分：左侧为 Zynq7Z020 @ 410–495 mw，右侧为 Zynq7100 @ 1760–1930 mw*

| Author | Type | Platform | Speed (GOPS) | Power (mw) | Precision |
| :--- | :--- | :--- | :--- | :--- | :--- |
| This work | FPGA | Zynq7Z020 | 415 | 495 | fix 1 |
| | FPGA | Zynq7100 | 2077 | 1930 | fix 1 |
| Sanmi [27] | FPGA | Kintex7350 | - | - | fix12 |
| Zhang [28] | FPGA | Virtex7 | 612 | 18610 | fix32 |
| Gokhale [29] | FPGA | Zynq7Z045 | 227 | 4000 | fix16 |
| Li [45] | FPGA | StratixV | 410 | 1114 | fix 16 |
| Du [46] | layout | 65 nm | 194 | 320 | fix16 |
| Pham [47] | layout | 45 nm SOI | 320 | 600 | fix1 |
| Cavigelli [48] | silicon | 65 nm | 196 | 510 | fix12 |
| Andri [49] | silicon | 65 nm | 423 | 153 | fix1 |

watts of chip-level power consumption, which is orders of magnitude more efficient than CPU- and GPU-based solutions.

### 7.4.4 Real-time analysis of video images

Besides the remote sensing applications, which are our primary motivation, we also evaluate the DANoC hardware for real-time video processing. In this experiment a DANoC hardware prototype is mounted on a toy robot car for automatic driving (Fig. 7.12). The robot car has two 640–480 video cameras connected with the hardware board via respective USB ports. One camera is used to track the road, and the other is used to recognize 12 traffic signs. The video streams are captured and thresholded as binary frames using software running on the ARM host processors. Then the image frames are split as 16-16 (road) and 32-32 (traffic sign) windows with 8-pixel step size, and the images are arranged as binary streams and routed to the DANoC coprocessor for feature extraction and classification. The classification results are then sent back to the host processor to automatically control the toy robot car.

Two types of DAN pipelines are implemented in the DANoC coprocessor for recognizing the traffic signs and the road. Each pipeline uses two Sparse Neural Cores to implement a stacked DAN and one core to implement the neural network classifier. Eight video clips recorded with different light conditions and camera angles are used to train and test the DAN algorithm offline. An experiment shows that the DANoC coprocessor achieves 98.2% correct rate for recognizing 12 traffic signs and 98.9% correct rate for recognizing the road. The performance of the DANoC system is estimated using the number of multiplications required in a standard Deep Belief Network of the same configuration.

![](img/5fa4874adaccc5ede04575a2e9e5662a_145_0.png)

Figure 7.12 A self-driving robot car equipped with a DANoC hardware prototype. The robot car has two cameras; one is used to track the road (left), and the other is used to recognize the traffic signs (right). Two types of deep neural networks are integrated in the DANoC, which achieve 98.2% correct rate for recognizing 12 traffic signs and 98.9% correct rate for recognizing the road. The Zynq7100-based DANoC coprocessor achieves the state-of-the-art peak performance of 1593 GOPS and is able to process 67 frames of 640-480 video in real time.

The Zynq7Z020 DANoC with six pipelines of deep neural networks achieves 319 giga-operations-per-second with 478-mw power consumption. The high-performance Zynq7100-based DANoC could integrate up to 30 pipelines in single FPGA chip, which enables it to process 67 frames in real-time with the peak performance of 1593 effective giga-operations-per-second.

## References

- [1] X. Zhou, S. Li, F. Tang, S. Hu, Z. Lin, L. Zhang, DaNoC: An efficient algorithm and hardware codesign of deep neural networks on chip, IEEE Transactions on Neural Networks and Learning Systems 29 (7) (2017) 3176–3187.
- [2] G. Hinton, L. Deng, D. Yu, G.E. Dahl, A.-r. Mohamed, N. Jaitly, A. Senior, V. Vanhoucke, P. Nguyen, T.N. Sainath, et al., Deep neural networks for acoustic modeling in speech recognition: The shared views of four research groups, IEEE Signal Processing Magazine 29 (6) (2012) 82–97.
- [3] G.E. Hinton, R.R. Salakhutdinov, Reducing the dimensionality of data with neural networks, Science 313 (5786) (2006) 504–507.
- [4] Y. Chen, X. Zhao, X. Jia, Spectral–spatial classification of hyperspectral data based on deep belief network, IEEE Journal of Selected Topics in Applied Earth Observations and Remote Sensing 8 (6) (2015) 2381–2392.
- [5] O. Vinyals, S.V. Ravuri, Comparing multilayer perceptron to deep belief network tandem features for robust ASR, in: Proceedings of IEEE International Conference on Acoustics, Speech and Signal Processing, 2011, pp. 4596–4599.
- [6] L.P. Maguire, T.M. McGinnity, B. Glackin, A. Ghani, A. Belatreche, J. Harkin, Challenges for large-scale implementations of spiking neural networks on FPGAs, Neurocomputing 71 (1–3) (2007) 13–29.
- [7] N. Lopes, B. Ribeiro, An evaluation of multiple feed-forward networks on GPUs, International Journal of Neural Systems 21 (01) (2011) 31–47.
- [8] S. Himavathi, D. Anitha, A. Muthuramalingam, Feedforward network implementation in FPGA using layer multiplexing for effective resource utilization, IEEE Transactions on Neural Networks 18 (3) (2007) 880–888.
- [9] S. Draghici, On the capabilities of neural networks using limited precision weights, Neural Networks 15 (3) (2002) 395–414.
- [10] J.L. Holi, J.-N. Hwang, Finite precision error analysis of neural network hardware implementations, IEEE Transactions on Computers 42 (3) (1993) 281–290.
- [11] S. Gupta, A. Agrawal, K. Gopalakrishnan, P. Narayanan, Deep learning with limited numerical precision, in: Proceedings of International Conference on Machine Learning, 2015, pp. 1737–1746.
- [12] M. Yuan, Y. Lin, Model selection and estimation in regression with grouped variables, Journal of the Royal Statistical Society: Series B (Statistical Methodology) 68 (1) (2006) 49–67.
- [13] M. Ranzato, Y.-L. Boureau, Y. LeCun, et al., Sparse feature learning for deep belief networks, Advances in Neural Information Processing Systems 20 (2007) 1185–1192.
- [14] H. Lee, C. Ekanadham, A. Ng, Sparse deep belief net model for visual area V2, in: Proceedings of International Conference on Neural Information Processing Systems, vol. 20, 2007, pp. 873–880.
- [15] N.-N. Ji, J.-S. Zhang, C.-X. Zhang, A sparse-response deep belief network based on rate distortion theory, Pattern Recognition 47 (9) (2014) 3179–3191.
- [16] S. Abramson, D. Saad, E. Marom, Training a network with ternary weights using the CHIR algorithm, IEEE Transactions on Neural Networks 4 (6) (1993) 997–1000.
- [17] F. Aviol, E. Mayoraz, A constructive training algorithm for feedforward neural networks with ternary weights, in: Proceedings of European Symposium on Artificial Neural Networks, vol. 94, 1994, pp. 123–128.
- [18] S. Han, J. Pool, J. Tran, W.J. Dally, Learning both weights and connections for efficient neural networks, in: Proceedings of International Conference on Neural Information Processing Systems, vol. 1, 2015, pp. 1135–1143.
- [19] W. Chen, J. Wilson, S. Tyree, K. Weinberger, Y. Chen, Compressing neural networks with the hashing trick, in: Proceedings of International Conference on Machine Learning, 2015, pp. 2285–2294.
- [20] S. Han, H. Mao, W.J. Dally, Deep compression: Compressing deep neural networks with pruning, trained quantization and Huffman coding, arXiv:1510.00149 [abs].
- [21] M. Courbariaux, I. Hubara, D. Soudry, R. El-Yaniv, Y. Bengio, Binarized neural networks: Training deep neural networks with weights and activations constrained to +1 or -1, arXiv:1602.02830 [abs].
- [22] M. Rastegari, V. Ordonez, J. Redmon, A. Farhadi, XNOR-Net: ImageNet classification using binary convolutional neural networks, in: Proceedings of European Conference on Computer Vision, 2016, pp. 525–542.
- [23] J.M. Alvarez, M. Salzmann, Learning the number of neurons in deep networks, in: Proceedings of International Conference on Neural Information Processing Systems, 2016, pp. 2270–2278.
- [24] W. Pan, H. Dong, Y. Guo, DropNeuron: Simplifying the structure of deep neural networks, arXiv:1606.07326 [abs].
