
## Hardware architectures for deep learning

- 2.2 Hardware acceleration for RNN inference 37
- 2.2.1 Software implementation 37
- 2.2.2 Hardware implementation 38
- 2.3 Hardware implementation of LSTMs 39
- 2.3.1 Model compression 40
- 2.3.2 Datatype and Quantization 44
- 2.3.3 Memory 46
- 2.4 Conclusion 48
- References 48

## 3 Feedforward neural networks on massively parallel architectures 53

Reza Hojatab, Ahmad Khonsari, Mehdi Modarresi, and Masoud Daneshtalab

- 3.1 Related work 55
- 3.2 Preliminaries 57
- 3.3 ClosNN, a customized Clos for neural network 59
- 3.4 Collective communications on ClosNN 60
- 3.5 ClosNN customization and area reduction 62
- 3.6 Folded ClosNN 65
- 3.7 Leaf switch optimization 67
- 3.8 Scaling to larger NoCs 67
- 3.9 Evaluation 68
- 3.9.1 Performance comparison under synthetic traffic 69
- 3.9.2 Performance evaluation under realistic workloads 70
- 3.9.3 Power comparison 71
- 3.9.4 Sensitivity to neural network size 72
- 3.10 Conclusion 73
- References 73

## Part II Deep learning and approximate data representation 77

## 4 Stochastic-binary convolutional neural networks with deterministic bit-streams 79

M. Hassan Najafi, S. Rasoul Faraji, Bingzhe Li, David J. Lilja, and Kia Bazargan

- 4.1 Overview 79
- 4.2 Introduction 79
- 4.3 Background 81
- 4.3.1 Stochastic computing 81
- 4.3.2 Deterministic low-discrepancy bit-streams 82
- 4.3.3 Convolutional neural networks 84
- 4.4 Related work 84
- 4.5 Proposed hybrid binary-bit-stream design
- 4.5.1 Multiplications and accumulation
- 4.5.2 Handling negative weights
- 4.6 Experimental results
- 4.6.1 Performance comparison
- 4.6.2 Cost comparison
- 4.7 Summary

Acknowledgment
References

## 5 Binary neural networks

Najmeh Nazari and Mostafa E. Salehi

- 5.1 Introduction
- 5.2 Binary neural networks
- 5.2.1 Binary and ternary weights for neural networks
- 5.2.2 Binarized and ternized neural networks
- 5.3 BNN optimization techniques
- 5.4 Hardware implementation of BNNs
- 5.5 Conclusion
- References

## Part III Deep learning and model sparsity

## 6 Hardware and software techniques for sparse deep neural networks

Ali Shaafee, Liu Liu, Lei Wang, and Joseph Hassoun

- 6.1 Introduction
- 6.2 Different types of sparsity methods
- 6.3 Software approach for pruning
- 6.3.1 Hard pruning
- 6.3.2 Soft pruning, structural sparsity, and hardware concern
- 6.3.3 Questioning pruning
- 6.4 Hardware support for sparsity
- 6.4.1 Advantages of sparsity for dense accelerator
- 6.4.2 Supporting activation sparsity
- 6.4.3 Supporting weight sparsity
- 6.4.4 Supporting both weight and activation sparsity
- 6.4.5 Supporting output sparsity
- 6.4.6 Supporting value sparsity
- 6.5 Conclusion
- References

## x Hardware architectures for deep learning

## 7 Computation reuse-aware accelerator for neural networks

Hoda Mahdiani, Alireza Khadem, Ali Yasoubi, Azam Ghanbari, Mehdi Modarresi, and Masoud Daneshtalab

- 7.1 Motivation
- 7.2 Baseline architecture
- 7.2.1 Computation reuse support for weight redundancy
- 7.2.2 Computation reuse support for input redundancy
- 7.3 Multicore neural network implementation
- 7.3.1 More than K weights per neuron
- 7.3.2 More than N neurons per layer
- 7.4 Experimental results
- 7.5 Conclusion and future work
- References

## Part IV Convolutional neural networks for embedded systems

## 8 CNN agnostic accelerator design for low latency inference on FPGAs

Sachin Kumawat, Mohammad Metamed, and Soheil Ghiasi

- 8.1 Introduction
- 8.2 Brief review of efforts on FPGA-based acceleration of CNNs
- 8.3 Network structures and operations
- 8.3.1 Convolution
- 8.3.2 Inner product
- 8.3.3 Pooling
- 8.3.4 Other operations
- 8.4 Optimizing parallelism sources
- 8.4.1 Identifying independent computations
- 8.4.2 Acceleration strategies
- 8.5 Computation optimization and reuse
- 8.5.1 Design control variables
- 8.5.2 Partial sums and data reuse
- 8.5.3 Proposed loop coalescing for flexibility with high efficiency
- 8.6 Bandwidth matching and compute model
- 8.6.1 Resource utilization
- 8.6.2 Unifying off-chip and on-chip memory
- 8.6.3 Analyzing runtime
- 8.7 Library design and architecture implementation
- 8.7.1 Concurrent architecture
- 8.7.2 Convolution engine
- 8.7.3 Restructuring fully connected layers
- 8.7.4 Zero overhead pooling
- 8.7.5 Other layers
- 8.8 Caffe integration 180
- 8.9 Performance evaluation 181
- 8.9.1 Optimizer results 181
- 8.9.2 Onboard runs 182
- 8.9.3 Architecture comparison 185
- References 187

## 9 Iterative convolutional neural network (ICNN): an iterative CNN solution for

Katay Neshat, Houman Homay, Avesta

- 9.1 Motivation 191
- 9.2 Background 194
- 9.3 Iterative CNN 195
- 9.4 Case study: 196
- 9.4.1 AlexNet 199
- 9.4.2 Sequential training 200
- 9.5 Training 200
- 9.5.1 Parallel training 203
- 9.5.2 Complexity analysis 204
- 9.6 Visualization 204
- 9.6.1 Spiking neurons 208
- 9.6.2 Context-aware 209
- 9.7 Contextual 211
- 9.7.1 Spiking layers 211
- 9.7.2 Dynamic deadline 212
- 9.8 Policies for 212
- 9.8.1 Real-time applications 213
- 9.8.2 Thresholding policy 214
- 9.9 Implementation for 216
- 9.9.1 Fixed percentage 217
- 9.9.2 Context-aware pruning 218
- 9.10 Results for 218
- 9.10.1 Run-time 219
- 9.10.2 Overall accuracy 222
- 9.11. Summary 229
- 9.12. Conclusions 229
- References 229

## Hardware architectures for deep learning

## Part V Deeplearning on analog accelerators

## 10 Mixed-signal neuromorphic design for streaming signal processing 235

Sandeep Bande, Federico Corradi, Jan Stuijt, Siebren Schaafsma, and Frank Cathoor

- 10.1 Introduction 236
- 10.2 Related work 237
- 10.2.1 Mixed-signal neuromorphic architectures 237
- 10.2.2 Biomedical signal processing for ECG 240
- 10.3 NeuRAM3 mixed-signal neuromorphic platform 241
- 10.3.1 Analog neural components including local array 242
- 10.3.2 Global synapse communication network with TFT-based switches 242
- 10.3.3 NeuRAM3 mixed-signal neuromorphic platform FPGA architecture 246
- 10.4 ECG application mapping on non-scaled neuromorphic instance 248
- 10.4.1 ECG classification and overall setup 248
- 10.4.2 ECG signal compression and encoding in spikes 249
- 10.4.3 Recurrent spiking neural network 252
- 10.4.4 Recurrent neural network implemented in VLSI spiking neurons 252
- 10.4.5 Training LiF classifiers 254
- 10.4.6 VLSI implementation of the recurrent neural network 256
- 10.5 Results and discussion 257
- 10.5.1 Classification accuracy 257
- 10.5.2 Discussion on results for ECG application 258
- 10.5.3 NeuRAM3 hardware platform results 259
- 10.6 Summary and conclusions 260

Acknowledgments
260
References 261
