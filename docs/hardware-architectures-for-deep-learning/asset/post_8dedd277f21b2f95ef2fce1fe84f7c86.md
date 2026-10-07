
## 140 Hardware architectures for deep learning

For fully connected layers where there is no filter reuse, this prediction-based optimization means that not all weight bits are loaded from off-chip memory, improving energy efficiency.

The lossless prediction-based architecture showed an average 1.8x and 1.6x speedup over zero-activation skipping scheme Cnvlin and precision reduction scheme stripes, respectively, without the need of retaining the network.

### 6.4.5.3 SparseNN

There are other works using prediction to exploit output sparsity. SparseNN [33] deploys a lightweight runtime predictor for the output activation sparsity on the fly. The predictor is based on truncated singular value decomposition (SVD) to decompose weight matrix into two low-rank matrices. The computation complexity is smaller as compared to the original feedforward, also insignificant to the bypassed computations.

### 6.4.5.4 CompEnd

CompEnd [34] re-encodes the weights with inverted two's complement so that MSB has a positive weight and all others have negative weight. Multiplications are processed serially. MSBs are computed first, as the computation progresses, the bit serial sum goes negative By checking the sign inversion in the intermediate results of the bit serial sum, this scheme can detect negative results before finishing the calculation of all bits. The advantage is that the off-line weight encoding removes the need of weight reordering as in SnaPEA.

### 6.4.6 Supporting value sparsity

#### 6.4.6.1 Bit-pragmatic

Realizing multiplication as a sequence of shift and add operations allows zero bit positions. Bit-pragmatic [35] showed that this approach reduces the effectual computation demand, dramatically. It also devises a modified version of DaDianNao tile architecture, Pragmatic tile, to take advantage of this observation. The high-level organization of baseline and the modified tiles are shown in Figure 6.16. The baseline consists of multiple IPUs that perform inner product operations. As the operands, all the IPs share the same vector of activations from NBin but receive their own

![](img/e6e752b99eb1621488c89445a57e2a86_165_0.png)

Figure 6.15 The trend of the sum of bit-serial products with inverted two's complement weight encoding [34]

![](img/e6e752b99eb1621488c89445a57e2a86_166_0.png)

Figure 6.16 The tile structure of (a) DaDainNao vs. (b) Pragmatic tile [35]

vector of weights from SB. The results are accumulated to the appropriate output neurons in the NBout. Bit-pragmatic modifies this tile as follows: (1) It represents input value received from NBin into a series of 4-bit nonzero bit positions. Every cycle it broadcasts one of such offset values to the IPs. (2) It replaces the multiplier in the IP with shift units. Every such unit left the weight values according to its corresponding offset value. (3) Since shift logic is smaller than a multiplier, more shift-based IPs are accommodated into one tile. However, naively replicating the number of causes increases in SB bandwidth requirements. This is because in the naive approach, more IPs are added for more output channels and each output channel has its own weight. Pragmatic tile mitigates the bandwidth requirement by adding IPs for each neuron of the same output channels. As a result, multiple IPs can now share the same weight vector. Thus, there is no need for more weight bandwidth. However, the IPs sharing the same weights requires different input vectors. Therefore, Pragmatic tile linearly increases NBin bandwidth to deliver appropriate inputs to every IP in each cycle. Notice that NBin bandwidth is much smaller than SB bandwidth in the baseline tile, due to input sharing, it makes a better candidate for bandwidth expansion.

According to [35], Pragmatic tile can outperform DaDianNao [36] by 2.6× at the cost of 35% area overhead.

#### 6.4.6.2 Laconic architecture

Sharify et al. leverage value sparsity and propose laconic tile that improves Bit-prmatic with two proposals [37].

- Instead of using the offset in the 2's complement presentation, they use modified booth to reduce the number of effectual bit position.
- Based on the observation that weight values are distributes around zero, they apply values sparsity to weight as well.

A laconic tile is comprised of multiple laconic PEs, each of which performing as an inner product using low-precision units; Figure 6.17 shows the structure of a laconic PE. There is one low-precision unit per vector position that independently computes the multiplication of a pair of an activation and its corresponding weight. Since both activations and weights are represented in modified booth format, the low-precision units only perform exponents addition along determining the

![](img/e6e752b99eb1621488c89445a57e2a86_167_0.png)

Figure 6.17 Laconic PE's pipeline [37]

sing, iteratively. For any possible results of exponent addition, laconic PE keeps a counter that gets updated if any of the low-precision unit output matches its value. Once all the low-precision operations are done, the counters are shifted and added to the final result. Laconic tile can outperform a dense tile by 2.3x in terms of performance and 3x in terms of energy efficiency, on average.

### 6.5 Conclusion

In this chapter, we have reviewed the potential of sparsity to boost the performance and energy efficiency of DNN accelerators. We first identified four sparse methods: (1) activation, (2) weight, (3) output and (4) value sparsity. We reviewed software techniques to prune a network. Finally, we went over some prior works that leverage different methods of sparsity.

### References

- [1] Hennessy JL, and Patterson DA. A new golden age for computer architecture. Communications of the ACM. 2019;62(2):48–60.
- [2] Shan Tang. List of AI Chips; 2019. Available from https://github.com/basim/AI-Chip.
- [3] Deloitte. Hitting the Accelerator: The Next Generation of Machine Learning: 2018. Available from https://www.deloitte.com/content/dam/Deloitte/global/infographics/technology/nextgen-learning-report.pdf.
- [4] Han S, Pool J, Narang S, et al. Dense-sparse training for deep networks. arXiv preprint:1607.04381.
- [5] Jouppi NP, Young C, Patil N, et al. Datacenter performance analysis of a tensor processing unit. In: 2017 ACM/IEEE 44th International Symposium on Computer Architecture (ISCA). IEEE; 2017, p. 1–12.
- [6] Hemsoth N. Facebook Opening Bell for AI Hardware Makers; 2018. Available from https://www.plat.com/2018/09/13/facebook-opening-bell-ai-hardware-makers/.
- [7] Krizhev A, Sutskever I, and Hinton GE. ImageNet classification with deep convolutional networks. In: Advances in Neural Processing Systems; 2012, p. 1097–1110. Available from http://www.proceedings.com/17756.html.
- [8] Xu B, Wang N, Chen T, and Li, M. Empirical evaluation of rectified activations in a convolutional network. arXiv preprint:1505.08533.
- [9] Le Y, Denker JS, and Solla SA. Optimal brain gain. In: Advances in Information Processing Systems; 1990, p. 598–605. Available from https://dl.acm.org/citation.cfm?id=10923.10298
- [10] Han S, Mao H, and Dally WJ. Deep compression: Compressing neural network with pruning, training quantization and Huffman coding. arXiv preprint:1510.00149.
- [11] Zhu, MH, and Gupta S. To Prune, or Not to Prune: Exploring the Efficacy of Pruning for Model Compression. arXiv preprint:1710.01878.
- [12] Changino S, Sandler M, and Zhmoginov A. The Proof of Sparsity in Convolutional Neural Networks. ICLR. 2017. Available from https://arxiv.org/abs/1702.06257.
- [13] Han S, Pool J, Tran J, et al. Learning weights and Connections for Efficient Neural Network. In: Cortes C, Lawrence ND, Lee DD, et al., editors. Advances in Neural Information Systems 28: 2015. p. 1135–1143. Available from https://dl.acm.org/citation?id=2969366
- [14] Wen W, Wu C, Wang Y, et al. Learning Structured Sparsity in Deep Neural Networks. In: Lee DD, Sugiyama M, Luxembourg UV, et al., editors. Neural Information Processing Systems 29: 2016. p. 2074–2082. Available from https://dl.acm.org/citation?id=3157329
- [15] Narang S, Undersander E, and Diamos G. Block-sparse recurrent neural networks. arXiv preprint:1711.02782.
- [16] Kang H. Accelerator-aware pruning for convolutional neural networks. In IEEE Transactions on Circuits and Video for Technology. IEEE; 2019.
- [17] Yu J, Lukehafer A, Palframan D, et al. Customizing DNN pruning to the underlying hardware parallelism. In: Proceedings of the 44th International Symposium on Computer Architecture. ISCA'17; 2017.
- [18] Liu Z, Sun M, Zhou T, et al. Rethinking the value of network pruning. In: International Conference on Learning Representations; 2019. Available from https://openreview.net/forum?id=rlnB3CSyn.
- [19] Delmas A, Judd P, Stuart DM, et al. Bit-tact: Exploiting ineffectual computations in neural networks: Which, why, and how. arXiv preprint:1803.3688.
- [20] Chen Y, Emery J, and S Visser: A spatial architecture for energy-efficient dataflow for neural networks. In: ACM SIGARCH Computer Architecture News. vol. 44. IEEE Press; 2016, p. 367–379.
- [21] Rhu M, O'Connor M, Chatterjee N, et al. Compressing DMA engine: Leveraging activation sparsity for training deep neural networks. In: 2018 IEEE International Symposium on High Performance Computer Architecture (HPCA). IEEE; 2018. p. 78–91.
- [22] Parashar A, R Mukkar, A, et al. SCNN: An accelerator for compressed-sparse convolutional neural networks. 2017 ACM/IEEE 44th International Symposium on Computer Architecture (ISCA). IEEE; 2017, p. 27–40.
- [23] Albericio J, Judd P, Hetherington T, et al. Cnvulin: Ineffectual-neuron-free deep neural network computing. ACM SIGARCH Computer Architecture News. 2016;44(3):1–13.
- [24] Nvidia. 2018. NVIDIA Deep Learning Accelerator. Available from: http://nvla.org/primer.html
