
## Performance analysis

In [Table 6.14](#Chapter6.html#c06_tbl14), performance comparisons among C-Program-optimized CPU performance, GPU performance, 3D CMOS-ASIC and 3D multilayer CMOS-ReRAM accelerator are presented for `![image](images/ch06_si831.gif)` testing images. The acceleration of each layer is also presented for three layers (`![image](images/ch06_si832.gif)`, `![image](images/ch06_si833.gif)` and `![image](images/ch06_si834.gif)`). Please note that the dimension of weight matrices are decomposed into `![image](images/ch06_si835.gif)` and `![image](images/ch06_si836.gif)` with `![image](images/ch06_si837.gif)` bit-width and maximum rank 6. The compression rate is `![image](images/ch06_si838.gif)` and `![image](images/ch06_si839.gif)` with and without bit truncation. Here, the compression rate is the ratio of volume of weights before and after compression. Among the four implementations, 3D multilayer CMOS-ReRAM accelerator performs the best in area, energy and speed. Compared to CPU, it achieves `![image](images/ch06_si840.gif)` speedup, `![image](images/ch06_si841.gif)` energy-saving and `![image](images/ch06_si842.gif)` area-saving. For GPU-based implementation, our proposed 3D CMOS-ReRAM architecture achieves `![image](images/ch06_si843.gif)` speedup and `![image](images/ch06_si844.gif)` energy-saving. We also design a 3D CMOS-ASIC implementation with similar structure as 3D multilayer CMOS-ReRAM accelerator with better performance compared to CPU- and GPU-based implementations. The proposed 3D multilayer CMOS-ReRAM 3D accelerator is `![image](images/ch06_si845.gif)` speedup, `![image](images/ch06_si846.gif)` energy-saving and `![image](images/ch06_si847.gif)` area-saving compared to 3D CMOS-ASIC.

### Table 6.14 Performance comparison under different hardware implementations on MNIST data set with 10,000 testing images

`![image](images/tab6.14.jpg)`

The throughput and energy efficiency for these four cases are also summarized in [Table 6.14](#Chapter6.html#c06_tbl14). For energy efficiency, the discussed accelerator can achieve 1,499.83 GOPS/W, which has `![image](images/ch06_si848.gif)` better energy efficiency comparing to 3D the CMOS-ASIC result (347.29 GOPS/W). In comparison to our GPU baseline, it has `![image](images/ch06_si849.gif)` better energy efficiency comparing to NVIDIA Quadro 5000. For a newer GPU device (NVIDIA Tesla K40), which can achieve 1,092 GFLOPS and consume 235 W [241], our proposed accelerator has `![image](images/ch06_si850.gif)` energy-efficiency improvement.

### 6.2.3.3 TNN-based distributed on-chip design on 3D single-layer architecture

#### Experiment settings

In the experiment, we have implemented different baselines for performance comparisons. The detail of each baseline is listed as follows:

**Baseline 1**: General processor (CPU/GPU). The general processor implementation is based on optimized C-program on a computer server with `![image](images/ch06_si851.gif)` cores of `![image](images/ch06_si852.gif)` GHz and `![image](images/ch06_si853.gif)` GB RAM. A Nvidia GeForce GTX 970 is used as reference for the GPU performance comparison.

**Baseline 2**: 2D CMOS-ASIC. The 2D CMOS-ASIC implementation with proposed architecture is done by Verilog with `![image](images/ch06_si854.gif)` GHz working frequency based on CMOS 65-nm low-power PDK. Power, area and frequency are evaluated through Synopsys DC compiler (D-2010.03-SP2).

**Baseline 3**: 3D CMOS-ASIC. The 3D CMOS-ASIC implementation is the same as 2D version but features with TSV communication. TSV area, power and delay are evaluated based on Simulator DESTINY [218] and fine-grained TSV model CACTI-3DD [242]. The buffer size of the top layer is SRAM based and set `![image](images/ch06_si855.gif)` MB to store tensor cores. The TSV area is estimated to be `![image](images/ch06_si856.gif)` with capacitance of `![image](images/ch06_si857.gif)` fF. TSV model in [238] is included for area and power evaluation; 512 vertical TSVs are assumed between layers to support communication and parallel computations [239].

**Proposed 3D CMOS-ReRAM**: The settings of CMOS evaluation and TSV model are the same as Baseline 3. For the ReRAM-crossbar design evaluation, the resistance of ReRAM is set as `![image](images/ch06_si858.gif)` and `![image](images/ch06_si859.gif)` as on-state and off-state resistance and 2V SET/RESET voltage according to [206] with working frequency of `![image](images/ch06_si860.gif)` MHz. The CMOS and ReRAM integration is evaluated based on [64].

To evaluate the proposed architecture, we apply CIFAR-10 [233] and MNIST [232] data set to analyze the neural network compression and architecture performance analysis. The energy-efficient neural network is designed on MATLAB first using Tensor-train toolbox [204] and tensor network [196]. After determining the network configuration and compression rate, it is then fully optimized using C-program as CPU-based result. Then we apply nonuniform quantization to perform tensor-core quantization before mapping on the 3D CMOS-ReRAM architecture. To evaluate the model compression, we compare our method with SVD-based node-pruned method [243] and general neural network [53]. The energy efficiency and speedup are also evaluated.

#### Energy-efficient tensor-compressed neural network

To achieve high compression rate, we first apply nonuniform quantization for tensor-core weights. As shown in [Figure 6.30](#Chapter6.html#c06_fig30), the probability density function of tensor-core weights can be modeled as Gaussian distribution. For such known pdf, we can effectively find the optimal level representative values with minimized mean square error. [Figure 6.31](#Chapter6.html#c06_fig31) shows the trade-off between accuracy, bit-width and compression rate on MNIST data set with three-layer neural network. [Table 6.15](#Chapter6.html#c06_tbl15) shows the clear effect of quantization on the compression rate. In general, bit-width quantization can help improve `![image](images/ch06_si861.gif)` more compression rate on neural network.

`![image](images/PBPC0390-06-f30.jpg)`

**Figure 6.30** TNN Layer 1 weight and Layer 2 weight histogram with approximate Gaussian distribution

`![image](images/PBPC0390-06-f31.jpg)`

**Figure 6.31** Compression rate and accuracy with increasing bit-width

**Table 6.15** Model compression under different numbers of hidden nodes and tensor ranks on MNIST data set

`![image](images/tab6.15.jpg)`

To have a fair comparison with [245], we also adopted LeNet-300-100 network [232], which is a two hidden FC layer network (`![image](images/ch06_si872.gif)`, `![image](images/ch06_si873.gif)`, `![image](images/ch06_si874.gif)`). Under such configuration, [245] can achieve `![image](images/ch06_si875.gif)` compression with error rate 1.58% using quantization (`![image](images/ch06_si876.gif)`-bit precision), pruning and Huffman coding techniques. By adopting `![image](images/ch06_si877.gif)` bit-width configuration on tensorized layer, we can achieve even more compression rate (`![image](images/ch06_si878.gif)`) with maintained accuracy (1.63%).

We also apply the proposed TNN to CIFAR-10 data set. CIFAR-10 data set consists of `![image](images/ch06_si879.gif)` images with size of `![image](images/ch06_si880.gif)` under ten different classes. We adopt LeNet-alike neural network [232] and we use a two-layer FC TNN to replace the last two FC layers, which is `![image](images/ch06_si881.gif)` and `![image](images/ch06_si882.gif)`. By adopting nonuniform tensor-core bit quantization (8 bit-width), we can achieve `![image](images/ch06_si883.gif)` compression on FC layers and `![image](images/ch06_si884.gif)` on the whole network, respectively, with the same accuracy loss (2%).

#### Energy-efficient 3D CMOS-ReRAM architecture
