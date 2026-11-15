![](bbox=[0.115, 0.095, 0.825, 0.315])

Figure 7.9 (a) Classification accuracy of the DANs and DBNs with different weight decay approaches. The connection weights are thresholded with the \(\sigma\%\) significant weights reserved and represented using single-bit integers. (b) Memory required for weight parameters of the DBN and DAN.

To achieve higher hardware efficiency, the DAN can use binary activations and binary weights. Fig. 7.9(a) also shows the influence of adopting binary activation on classification accuracy. The activations of the DAN$_B$ are thresholded and binarized using a constant 0.5. As shown in Fig. 7.9(a), the accuracy of the neural network classifier proceeded by the DAN$_B$ is significantly higher than the DBN. By adopting binary weights and activations the DANoC coprocessor can replace the complex floating-point multipliers with simple fix-point accumulators and implements the sigmoid activation function using simple threshold operations.

By adopting the sparse binary connections the DAN becomes 99.3% (\(\sigma = 20\%\)) to 99.9% (\(\sigma = 5\%\)) more memory efficient than the single-precision DBN. Fig. 7.9(b) shows the theoretical results of the memory used by the DAN and original DBN. The memory complexity of the deep neural networks increases as the number of neurons increases. The present DBNs are usually implemented using 32-bit representation; however, with sparse and binary weights, the DAN$_b$ can improve the memory efficiency by two to three orders of magnitude.

# 7.4.3 Hyperspectral remote sensing images

The second experiment applies the DAN algorithm and the DANoC system to the hyperspectral remote sensing application. Differently from visible-light images, the hyperspectral images contain information from across the electromagnetic spectrum. Fig. 7.10 shows the Pavia Center