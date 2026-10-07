# 180 Hardware architectures for deep learning

fashion. The shift register collects pooling filter width number of pixels and computes partial pools using a compressor or adder. Partial pooled values are stored into on-chip memory in row major sequence and read back when next set of partial pools is generated for that pooling filter, until the complete filter is processed. 8.9 also shows the computation sequence for pooling. As convolution filters, filters can also overlap, which means partial pools are shared between multiple pooled pixels. To process the incoming OFM without stalls, we simultaneously compute all $n_{OV}$ overlapping filters. Partial pool computed in current cycle with previous $n_{OV}$ partial pools from BRAM are used to compute new partial pools and stored in BRAM in parallel. Therefore, processing $Tm$ pixels can result in high-on bandwidth and logic resource requirements for pooling. Hence, we process a factor of $Tp$ pixels every cycle. Since OFM pixels are produced every $K_R 	imes K_C$ convolution cycles, as long as $Tm/Tp$ is lower than that, there will be no pooling overhead. If convolution is $1 	imes 1$, we compute pooling as a separate layer as it is not possible to hiding latency.

# 8.7.5 Other layers

We plug the layer from Load/Store OFM kernel to use the already present data redirection logic as shown in Figure 8.7(b). Other layers like normalization, scaling or element-wise layers are plugged in a similar way. Apart from that we concatenate filters for free by setting interleaving size of OFMs in DRAMs to be the total width of concatenated channels. For each new concatenated layer, an offset is created by number of channels of the previous layer. This allows us to implement even level nested branched networks creating support for even more network architectures.

# 8.8 Caffe integration

FICaffe is an extension to the widely used deep learning framework Caffe. The fully automated acceleration flow is shown in Figure 8.10. FICaffe's flow includes

![](bbox=[0.09, 0.675, 0.92, 0.905])

Figure 8.10 FICaffe end-to-end acceleration flow