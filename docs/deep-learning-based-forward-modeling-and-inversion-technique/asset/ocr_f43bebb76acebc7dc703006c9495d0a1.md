# Reconstruction of Thermophysical Parameters Based on Deep Learning 133

![](bbox=[0.257, 0.163, 0.742, 0.413])

# FIGURE 4

The inversion performance of the network for 2D temperature related thermal conductivity.

where $M$ and $N$ are the total number of temporal and spatial grids, $k_{real}$ and $k_{pred}$ are the real and predicted values of the corresponding thermal conductivity. In fact, the ultimate relative error rate is 1.03% for the temperature-related scenario and 2.65% for spatial-related case. Additionally, a series of stochastically chosen specimens from the spatial-dependent data are exhibited in Figure 4.15, where (a) represents the temperature by the detectors while, (c) and (d) are the real, predicted and error of the conductivity. The result has tested the mighty prediction ability of the framework. Furthermore another merit of the network is that a fully trained network can get the inferential field almost in real time. Actually, to predict 1000 samples, the proposed framework only needs 1.732 s, which exceeds traditional iteration algorithms in computing speed.

# 4.5.2 3D Cases

# 4.5.2.1 DL Framework

Enlightened by the aforementioned iteration algorithm, a DL architecture on the basis of a non-linear mapping module (NMM) is developed to resolve the IHC. As demonstrated in Figure 4.16, the module is a feedback neural network [40, 41] consisting of four layers: an input fully connected layer, two hidden layers and an output layer. Here, the input layer is composed of $N_d 	imes N_t$ nodes where the output layer includes $N_s$ nodes, indicating the number of solving points. Assuming that $T$ is the input temperature vector, the output