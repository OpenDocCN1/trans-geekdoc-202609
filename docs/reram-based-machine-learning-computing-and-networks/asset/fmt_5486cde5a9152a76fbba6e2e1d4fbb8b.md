
With varied ![image](images/ch08_si372.gif) and ![image](images/ch08_si373.gif), it can be observed from [Figure 8.10](#Chapter8.html#c08_fig10) that the performance degradation is more susceptible to resistance variation of LRS, while less sensitive on variation of HRS. In practice, the HRS variation ![image](images/ch08_si374.gif) is approximately ![image](images/ch08_si375.gif) [301], and LRS variation ![image](images/ch08_si376.gif) roughly ![image](images/ch08_si377.gif) [301]. The real-world ![image](images/ch08_si378.gif) is annotated in [Figure 8.10](#Chapter8.html#c08_fig10) and it can be concluded that the proposed Boolean embedding on ReRAM crossbar is robust against ReRAM device variations when on/off ratio is high (![image](images/ch08_si422.gif)). To further suppress the performance degradation, material engineering [302] and verification programming method [301] can help achieve higher LRS uniformity.

# Chapter 9

**Conclusions: wrap-up, open questions and challenges**

## 9.1 Conclusion

To conclude, this book has shown a thorough study on resistive random-access memory (ReRAM)-based nonvolatile in-memory architecture towards machine learning applications from circuit level, to architecture level, and all the way to system level.

For the circuit level, on the one hand, we use non-volatile memory (NVM)-SPICE to simulate matrix–vector multiplication acceleration by binary ReRAM crossbar. By programming all the elements of a matrix into ReRAM resistance in the crossbar array, we can use crossbar wordline voltages to represent another matrix, and the multiplication result can be denoted by the merging current on bitlines. In this mapping scheme, both ReRAM resistance and crossbar I/O are in binary format so that the computation accuracy can be guaranteed. Simulation results show that the proposed architecture has shown ![image](images/ch09_si1.gif) faster speed, ![image](images/ch09_si2.gif) better energy efficiency and ![image](images/ch09_si3.gif) smaller area when compared to the same design by complimentary metal oxide semiconductor (CMOS)-based application specific integrated circuit (ASIC). On the other hand, we use a Verilog-A model to build an ReRAM-based voltage-controlled oscillator circuit in Cadence. In a coupled network by ReRAM-based oscillator, the simulation results can be fitted as L2-norm calculation. Compared to traditional CMOS-based oscillator circuit, it has a much simpler structure with smaller area and better energy efficiency.

For the architecture level, we have developed a distributed in-memory architecture (XIMA) and three-dimensional (3D) CMOS-ReRAM architecture. For XIMA, we use both ReRAM crossbar for data storage and computing engine. We use a data block and logic block to form a data–logic pair, and all the pairs are located distributively. As a result, the communication bandwidth can be significantly improved because the computing engine only accesses the data from pairs. To achieve the in-memory computing, we design a control bus in each data–logic pair for communication among processor, data and logic block. In addition, communication protocol between processor and control bus is redefined for the in-memory computing implementation. For 3D CMOS-ReRAM architecture, we developed two schemes: single-layer and multilayer. The single-layer architecture uses ReRAM via connecting the top-layer wordlines and bottom-layer bitlines. All the other CMOS logics are implemented in the bottom layer as well. The multilayer architecture uses through silicon via (TSV) connecting the first-layer ReRAM-based data buffer, the second-layer ReRAM-based logic computing and the third-layer CMOS. Such a 3D architecture can significantly improve the throughput as well as the area efficiency for the hybrid ReRAM/CMOS computing system.

For the system level, for the XIMA, we have accelerated three machine learning algorithms. The learning and inference procedures of single-layer feedforward neural network (SLFN) have been optimized and partially mapped on the passive binary ReRAM crossbar. In addition, we mapped the binary convolutional neural network on both passive array and One Selector One ReRAM array with different mapping schemes. Moreover, L2-norm gradient-based learning and inference are also implemented on an ReRAM network with both crossbar and coupled oscillators. For 3D CMOS-ReRAM architecture, we also mapped the optimized SLFN algorithm. All the operations in learning and inference stages are implemented so that it can achieve the online learning. In addition, tensorized neural network is mapped on both single-layer and multilayer accelerators with different mapping scheme. For all the machine learning algorithms mapped on XIMA and 3D CMOS-ReRAM accelerator, we evaluate their performance in device, architecture and system levels. All the implementations show higher throughput, bandwidth and parallelism with better energy efficiency.

## 9.2 Future work

Based on the above works, there are a few potential future works to enhance this research.

The first potential work is to validate some designs discussed. In this work, we explore the binary ReRAM crossbar as well as oscillator network in device and circuit level by simulation. However, the ReRAM devices in the array are not fully uniform so that the mapping scheme may not be applied in a large crossbar array. In addition, sneak path and thermal effect in the ReRAM crossbar will also occur the inaccuracy during computing. As for the XIMA, this work only simulates a few groups of control bus design, but in the real implementation, there will be thousands of control bus blocks so it is also necessary to optimize all these designs.

The second potential work is to realize neuromorphic computing by the ReRAM network. This work only explores the artificial neural network implementations in the ReRAM-based architecture. All of these algorithms are originally designed for CMOS-based computing systems such as CPU, GPU, CMOS-ASIC and FPGA. The ReRAM-based architecture can perform analog-value computing operations, which is widely applied in neuromorphic applications. For example, it is easier to implement spike-timing-dependent plasticity-based synapse programming algorithm and also spiking neural networks on ReRAM compared to CMOS-ASIC or FPGA. It is possible to explore an ReRAM-based neuromorphic computing system with simpler structure and better scalability than the state-of-the-art works.

# References

[1] Cukier K. Data, data everywhere. The Economist. 2010 Feb.

[2] International Data Corporation. Digital Universe Study. Dell EMC. 2011.

[3] White T. O'Reilly Media Inc; 2012.

[4] Zaharia M, Chowdhury M, Franklin MJ, *et al*. Spark: Cluster computing with working sets. In: USENIX Conference on Hot Topics in Cloud Computing; 2010.

[5] Apache Flink. Apache Flink: Scalable batch and stream data processing. [http://flink.apache.org/](http://flink.apache.org/). Online.

[6] Carbone P, Fóra G, Ewen S, *et al*. Lightweight asynchronous snapshots for distributed dataflows. CoRR. 2015;abs/1506.08603.

[7] Saha B, Shah H, Seth S, *et al*. ApacheTez: A unifying framework for modeling and building data processing applications. In: ACM SIGMOD International Conference on Management of Data; 2015.

[8] Akidau T, Bradshaw R, Chambers C, *et al*. The Dataflow model: A practical approach to balancing correctness, latency, and cost in massive-scale, unbounded, out-of-order data processing. Proc VLDB Endow. 2015;8(12): 1792–1803.

[9] LeDell E. High performance machine learning in R with H2O. In: ISM HPC on R Workshop; 2015.

[10] Xing EP, Ho Q, Dai W, *et al*. Petuum: A new platform for distributed machine learning on big data. In: ACM SIGKDD International Conference on Knowledge Discovery and Data Mining; 2015.

[11] Bakshi K. Considerations for big data: Architecture and approach. In: IEEE Aerospace Conference; 2012.
