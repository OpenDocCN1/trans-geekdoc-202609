
We consider two representative types of network layouts in the experiments. We call them *bucket-shaped* networks and *cone-shaped* networks respectively for ease of discussion. In a "bucket-shaped" network, all layers contain an identical number of nodes. These networks usually appear in stand-alone classifiers, generative models, and reinforcement learning. In a "cone-shaped" network, a hidden layer has no more nodes than its previous layer. These networks learn compressed features and representation as each layer introduces information loss in a controlled manner.

[Table 6.3](#9783110785937_066530.xhtml#b_9783110785944-006_tab_003) shows the test cases we designed using network layouts similar to those in real-world applications. We test two activation functions–rectifier linear function (`relu`) and the hyperbolic tangent function (`tanh`)–for each layout. Due to the alignment requirement of our hardware platform, we round the size of each layer to the next multiple of 32. We also produce challenging test cases for each application by linearly scaling the size of all layers. Specifically, the design of test cases is as follows.

*   **Bucket-shaped networks:**
    The experiments with "bucket-shaped" networks include 12 test cases. Test cases `B0` and `B1` correspond to the network structure for reinforcement learning in [\[276\]](#backmatter-001.xhtml#b_9783110785944-010_ref_276). The network has 2 hidden layers with 200 nodes in each layer. Test cases `B2` and `B3` correspond to a study of traffic-flow prediction [\[454\]](#backmatter-001.xhtml#b_9783110785944-010_ref_454). The network with the largest layer size contains 3 layers of hidden nodes with 400 nodes in each layer. Test cases `B4` and `B5` correspond to the network in the generative adversarial networks in [\[23\]](#backmatter-001.xhtml#b_9783110785944-010_ref_023). The network contains 4 hidden layers with 512 nodes in each layer. Test cases `B6`–`B11` are challenging versions for `B0`–`B5`, where the layer size of each case is 8 times that of the original version.

*   **Cone-shaped networks:**
    The experiments with "cone-shaped" networks include 8 test cases. Test cases `C0` and `C1` correspond to the stacked autoencoder in [\[713\]](#backmatter-001.xhtml#b_9783110785944-010_ref_713). The network has two hidden layers containing 400 and 225 hidden nodes, respectively. Test cases `C2` and `C3` correspond to the denoising autoencoder for speech data recognition in [\[221\]](#backmatter-001.xhtml#b_9783110785944-010_ref_221). The network contains two hidden layers, one with 1000 nodes and another with 500. Test cases `C4`–`C7` are challenging versions for `C0`–`C3`, where the layer size of each case is 4 times that of the original version.

We use randomly generated data and network parameters to test the efficiency of the system. Assuming that the function evaluation procedure takes the same time for different inputs, the total execution time for each backpropagation process is independent of the data distribution and the network parameters. In other words, given the same data size, the total execution time should stay unchanged regardless of the data source. As a result, using randomly generated data and network parameters facilitates experiments with various data sizes without affecting observations. The number of data instances for each test case is 220. In each test case, we calculate the gradient with respect to 100 sets of weights.

### 6.1.5.2 Results and Discussion

[Table 6.3](#9783110785937_066530.xhtml#b_9783110785944-006_tab_003) records the experimental results. In this table, the benchmark column records the numbers of data instances; the `CPU-1T`, `CPU-4T`, and `CPU-8T` columns contain the execution times in seconds for the corresponding implementation. The `SU` columns give the speedup of the FPGA implementation over the CPU with 1 thread, 4 threads, and 8 threads, respectively.

The architecture discussed in this contribution is faster than the CPU system in all but one test case. In the tests with bucket-shaped networks, the architecture achieves up to a 9.4, 5.4, and 5.2 times speedup compared with the software reference on 1, 4, and 8 threads. In the tests with cone-shaped networks, the architecture achieves up to a 7.8, 4.6, and 4.7 times speedup compared with the software reference on 1, 4, and 8 threads. In addition to the overall speed advantage of the architecture, we have the following additional observations:

1.  The software implementation scales poorly with the number of threads. The software running 4 threads achieves only around 2 times speedup against a single thread. The speed advantage on 8 threads over 4 threads is insignificant. In test cases `B10` and `B11`, the software running on 8 threads is even slower than when running on 4 threads.

2.  The software is more sensitive to the selection of the activation function than the architecture. With the same network layout, the software tends to be faster with the rectifier linear function than with the hyperbolic tangent function. The speed advantage is especially significant when the software runs on 4 and 8 threads. This observation confirms the speed advantage of the rectifier linear function on CPUs [\[255\]](#backmatter-001.xhtml#b_9783110785944-010_ref_255). By contrast, the architecture on FPGA evaluates any activation using the same number of commands. Therefore, the execution time of the architecture for a given layout is independent of the activation function.

3.  The experimental implementation achieves slightly higher speedup with larger networks that carry more network parameters. For instance, in the experiments with bucket-shaped networks with the `tanh` function, the speedup over 8 threads rises from 2.2 to 5.2 while the layer size expands from 224 to 4096. An exception of the observation is that architecture achieves high speedup against a single CPU thread in test case `B0`. A possible reason for the exception is that artifacts such as memory initialization for both software and hardware take significant time when the network is small. In this case, the comparison is less reliable than it is in other tests.

**Tab. 6.3** Execution time (seconds) and speedup.

| ID | Layers | Activation | CPU-1T | CPU-4T | CPU-8T | FPGA | SU-1T | SU-4T | SU-8T |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| B0 | 224x2 | tanh | 0.285 | 0.219 | 0.155 | 0.071 | 4.0 | 3.1 | 2.2 |
| B1 | 224x2 | relu | 0.181 | 0.104 | 0.090 | 0.071 | 2.5 | 1.5 | 1.3 |
| B2 | 416x3 | tanh | 0.731 | 0.356 | 0.274 | 0.105 | 7.0 | 3.4 | 2.6 |
| B3 | 416x3 | relu | 0.521 | 0.202 | 0.162 | 0.104 | 5.0 | 1.9 | 1.6 |
| B4 | 512x4 | tanh | 1.020 | 0.504 | 0.430 | 0.138 | 7.4 | 3.7 | 3.1 |
| B5 | 512x4 | relu | 0.786 | 0.320 | 0.235 | 0.137 | 5.7 | 2.3 | 1.7 |
| B6 | 1792x2 | tanh | 4.102 | 2.493 | 2.109 | 0.615 | 6.7 | 4.1 | 3.4 |
| B7 | 1792x2 | relu | 3.715 | 2.163 | 1.820 | 0.615 | 6.0 | 3.5 | 3.0 |
| B8 | 3328x3 | tanh | 21.758 | 13.120 | 13.176 | 2.576 | 8.4 | 5.1 | 5.1 |
| B9 | 3328x3 | relu | 20.827 | 13.783 | 12.400 | 2.574 | 8.1 | 5.4 | 4.8 |
| B10 | 4096x4 | tanh | 45.501 | 24.847 | 25.286 | 4.822 | 9.4 | 5.2 | 5.2 |
| B11 | 4096x4 | relu | 44.755 | 24.036 | 24.320 | 4.817 | 9.3 | 5.0 | 5.0 |
| C0 | 416,256 | tanh | 0.179 | 0.125 | 0.167 | 0.089 | 2.0 | 1.4 | 1.9 |
| C1 | 416,256 | relu | 0.137 | 0.086 | 0.102 | 0.087 | 1.6 | 1.0 | 1.2 |
| C2 | 1024,512 | tanh | 0.577 | 0.339 | 0.421 | 0.169 | 3.4 | 2.0 | 2.5 |
| C3 | 1024,512 | relu | 0.494 | 0.266 | 0.299 | 0.169 | 2.9 | 1.6 | 1.8 |
| C4 | 1664,1024 | tanh | 2.092 | 1.189 | 1.259 | 0.375 | 5.6 | 3.2 | 3.4 |
