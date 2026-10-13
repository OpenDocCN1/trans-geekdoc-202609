
## Error under device variation

In the previous discussion, the digitized ReRAM crossbar has better programming accuracy than the analog ReRAM crossbar. [Figure 6.10](#Chapter6.html#c06_fig10) shows a 200-time Monte-Carlo simulation of a single ReRAM device programming process with different write voltage $V_{write}$, where the voltage amplitude is under Gaussian distribution on the($\mu=V_{write}$, $\sigma=0.1V_{write}$), and each column denotes a region of $\Delta V_{write}$. It is clear that the digital ReRAM crossbar (only $R_{on}$ and $R_{off}$) can achieve a better uniformity than the analog ReRAM crossbar. The accuracy comparison against device variation on ReRAM is shown in [Figure 6.11](#Chapter6.html#c06_fig11)(b). The percentage of device variation defines the maximum resistance offset, and each ReRAM device follows standard deviation. Monte-Carlo is applied in the generation of device variation. In CIFAR-10, one can observe that when the device variation (ReRAM resistance value) is more than 8%, there is a large output current error reported. For example, when the device variation reaches 29%, the digital ReRAM can have an accuracy of 87.4% with only 4% decreased compared to no variations, better than the analog one with an accuracy of 84.8% with 7.6% decreased. In MNIST, the digital ReRAM is always better even when the device variation is larger than 27%.

![image](images/PBPC0390-06-f10.jpg)

**Figure 6.10** ReRAM configuration with voltage amplitude variation following Gaussian distribution

## Error under approximation

For a precision-bit direct-truncated CNN, we use the conventional approach to train the full-precision ($N$-bit) CNN first, and then decrease the precision of all the weights in the network. The numerical experiment results of weights with different bit-widths are shown in [Figure 6.11](#Chapter6.html#c06_fig11)(b). Here, the weights in the bitwise CNN is 1 bit, whose accuracy of is not changed. In CIFAR-10, although the accuracy of the full precision ($N$-bit) can reach 92.4% in the direct-truncated CNN, the bit-width influences the accuracy a lot especially when the bit-width is smaller than $N$. For example, when the precision decreases to $k$-bit, the accuracy drops down to only about 11.8%. In MNIST, the accuracy of the direct-truncated CNN drops significantly when the bit-width is smaller than $k$-bit. The results show that the proposed bitwise CNN can perform much better than the direct-truncated CNN.

![image](images/PBPC0390-06-f11.jpg)

**Figure 6.11** (a) Accuracy comparison with analog ReRAM under device variation; (b) accuracy comparison with truncated CNN with approximation

## Scalability study

To achieve a better energy efficiency of BNN, we do the scalability study to find out the BNN parameters for both good testing accuracy and energy efficiency. We use a four-layer BNN on MNIST benchmark as a baseline (100% energy efficiency, as shown in [Table 6.6](#Chapter6.html#c06_tbl6)), and change the number of output maps of Layer 2 (CONV-2, 50) and hidden nodes of Layer 3 (FC-1, 500), as shown in [Figure 6.12](#Chapter6.html#c06_fig12)(a) and (b). For each energy-efficiency configuration, we do a 20-epoch training to make a fair comparison. When the number of hidden nodes or output maps decreases, the energy efficiency is better but it will cause higher testing error rate. To summarize the scalability study, [Figure 6.12](#Chapter6.html#c06_fig12)(c) shows that the hidden nodes of Layer 2 is more sensitive to testing accuracy. As a result, increasing the hidden nodes of Layer 2 is better for higher accuracy while decreasing the hidden nodes of Layer 3 is better for energy efficiency.

![image](images/PBPC0390-06-f12.jpg)

**Figure 6.12** Scalability study of testing error rate under different energy consumption with (a) Layer 2 output maps and (b) Layer 3 hidden nodes; (c) comparison with Layer 2 output maps and Layer 3 hidden nodes

## Performance comparison

In this section, $32\times32$ images with $32\times32$ resolution in CIFAR-10 are selected to evaluate the performance among all implementations. Parameters including binary weights, and LUT for batch normalization have been configured by the training process. The detailed comparison is shown in [Table 6.7](#Chapter6.html#c06_tbl7) with numerical results including area, system throughput, computation time and energy consumption. [Figure 6.13](#Chapter6.html#c06_fig13) shows a recognition example of CIFAR-10 data set. In the numerical experiment, every batch comprises ten images and the results are calculated in parallel. The detailed result figure is included in the supplementary file. The black square represents to the class that each image belongs.

![image](images/PBPC0390-06-f13.jpg)

**Figure 6.13** Image recognition example of CIFAR-10 data set

**Table 6.7** Performance comparison among different software and hardware implementations on CIFAR-10 BCNN

![image](images/tab6.7.jpg)

The overall power comparison among all the implementations is shown in [Table 6.7](#Chapter6.html#c06_tbl7) under the similar accuracy of 91.4% in CIFAR-10. Compared to CPU-based and GPU-based bitwise CNN, the proposed digital ReRAM-based implementation can achieve up to four-magnitude smaller power. Moreover, compared to FPGA-based and CMOS-ASIC-based conventional CNN, the digital ReRAM-based implementation is $10^3\times$ and $10^2\times$ smaller power.

In addition, we analyze the detailed power characteristics of the proposed digital ReRAM design in [Figure 6.14](#Chapter6.html#c06_fig14). First, we analyze the power distribution on convolution, batch normalization, pooling and activation, respectively. [Figure 6.14](#Chapter6.html#c06_fig14)(a) shows that 89.05% of power is consumed by convolution, while 9.17% of power is for batch normalization, and the rest only takes 1.78%. Second, we analyze the power distribution on different bitwise CNN layers in [Table 6.2](#Chapter6.html#c06_tbl2). Results in [Figure 6.14](#Chapter6.html#c06_fig14)(b) show that CONV-6 consumes the most power 25.92%, while CONV-4 and CONV-2 also consume more than 23% of the total power. In general, there is over 98% of power consumed by CONV-2 to CONV-6 layers.

![image](images/PBPC0390-06-f14.jpg)

**Figure 6.14** Power consumption of bitwise CNN for (a) different operations and (b) different layers

For the throughput performance, we use GOPS (giga operations per second) to evaluate all the implementations. The proposed digital ReRAM can achieve $10^3$ GOPS, which is $10^3\times$ and $10^2\times$ better than CPU-based and GPU-based implementations, respectively. It is also $10^2\times$ and $10\times$ better than FPGA-based and CMOS-ASIC. For energy efficiency, the digital ReRAM achieves $10^3$ TOPS/W, three-magnitude better than the CMOS-ASIC-based CNN. In area-efficiency comparison, the digital ReRAM is $10^2\times$ better than CMOS-ASIC. The digital ReRAM is the best among all the implementations on both throughput and efficiency.
