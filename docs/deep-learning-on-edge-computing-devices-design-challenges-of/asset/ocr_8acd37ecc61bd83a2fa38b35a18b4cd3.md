![](bbox=[0.18, 0.09, 0.76, 0.42])

Figure 7.3 Empirical distributions of the connection weights and the activations of a two-layer DAN. Diagrams (a) and (b) show the distributions of \(w_{ij}\) for the first and second layers, respectively. (c) and (d) showing the distributions of \(p(h_j=1|\mathbf{v})\) subtracted by the constant sigmoid (\(b_j\)). It is worth noting that for the DAN, the second-layer weights and activations seem sparser than the first layer.

Fig. 7.3 illustrates these two properties. Two deep neural networks of the same configuration (784-800-800) are built to select the features from the MNIST dataset. It seems that most DAN weights are close to zero, which are much sparser than the DBN weights. Meanwhile, by subtracting the constant vector \(\delta(\mathbf{b})\) the output activations of the AdaRBMs become notably sparser than the standard RBM (Fig. 7.3(c,d)). It is worth noting that, as shown in Fig. 7.3(b), the weight parameters become sparser in the second layer than in the first layer. It seems that the sparse activations of the first layer make the second-layer connection weights sparser.

# 7.3 Near-memory computing architecture

The DANoC system is an efficient, high-throughput, and scalable hardware prototype of the Deep Adaptive Network built using off-the-shelf FPGA devices. The basic building block of the hardware is a Sparse Neural Core (SNC) featuring an efficient Sparse-Mapping-Memory (SMM) based architecture. Fig. 7.4 shows an example of the cross-bar SMM designed to