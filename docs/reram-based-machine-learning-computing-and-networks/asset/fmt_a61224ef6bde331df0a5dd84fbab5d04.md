
### Step 3: XOR

It is to identify the index of ![image](images/ch06_si613.gif) with the operation ![image](images/ch06_si614.gif). Note that ![image](images/ch06_si615.gif) only when ![image](images/ch06_si616.gif) and ![image](images/ch06_si617.gif) from Step 1. The mapping of ReRAM-crossbar input and resistance is also shown in 22(c), and threshold voltage configuration is ![image](images/ch06_si618.gif). Therefore, the index of ![image](images/ch06_si619.gif) is identified by XOR operation.

### Step 4: Encoding

The third step produces ![image](images/ch06_si620.gif) in binary format as an encoder with the thresholds as Step 2. The input from the second step produces ![image](images/ch06_si621.gif) like result where only the ![image](images/ch06_si622.gif) input is ![image](images/ch06_si623.gif). As a result, only the ![image](images/ch06_si624.gif) row is read out and no current merge occurs in this step. The according binary format ![image](images/ch06_si625.gif) is an intermediate result and stored in the ![image](images/ch06_si626.gif) row, as shown in [Figure 6.23](#Chapter6.html#c06_fig23)(c). Encoding step needs an ![image](images/ch06_si627.gif) ReRAM crossbar, where ![image](images/ch06_si628.gif) is the number of bits in order to represent ![image](images/ch06_si629.gif) to ![image](images/ch06_si630.gif) in binary format.

By applying these four steps, one can map different tensor cores on ReRAM crossbars to perform the matrix–vector multiplication in parallel. Compared to the state-of-the-art realizations, this approach can perform the matrix–vector multiplication faster and more energy-efficient.

#### 6.2.2.2 Mapping TNN on single-layer architecture

Further, this section shows how to map a two-layer TNN-based inference processes according to the algorithm and network in Section 4.4. This section further discusses how to utilize the 3D single-layer CMOS-ReRAM architecture to design the TNN accelerator. Compared to the mapping in Section 2.2, a higher parallelism can be achieved with a distributed mapping.

##### TNN accelerator design

According to (4.28), ![image](images/ch06_si631.gif) needs to be multiplied by ![image](images/ch06_si632.gif) matrices unlike the general neural network. In this equation, it is only needed to take a slice of 3D matrix (i.e., a 2-D matrix) from each tensor core to perform the matrix–vector multiplication. Therefore, the computation complexity can be significantly reduced. We show the detailed accelerator design between two hidden layers of TNN in [Figure 6.24](#Chapter6.html#c06_fig24). Since the parameters of the neural network are compressed, one can store all the weights of TNN in ReRAM crossbar, following Figure 5.12(b). The input data ![image](images/ch06_si633.gif) is processed by several tensor cores, CMOS pooling and activation serially.

![image](images/PBPC0390-06-f24.jpg)

**Figure 6.24** Mapping details of highly parallel 3D single-layer CMOS-ReRAM accelerator for TNN

The detailed design of a tensor core is also shown in [Figure 6.24](#Chapter6.html#c06_fig24). In each tensor core, one has to store different slices of the 3D matrix into different ReRAM crossbars. Since only one 2D matrix is used at a time, two tensor-core Multiplexers (MUX) are used so that only one matrix is connected to the input voltage as well as the output ADC. The TC selection module controls the input and output MUX according to ![image](images/ch06_si634.gif) and ![image](images/ch06_si635.gif). For the tensor cores in the middle, the ADC/DAC pair can be removed since one does not need a digital representation for ReRAM-crossbar inputs.

##### Benefits summary of TNN on 3D CMOS-ReRAM architecture

From the algorithm optimization perspective, such tensorization can benefit of implementing large neural networks. First, by performing tensorization, the size of neural network can be compressed. Moreover, the computation load can also be reduced by adopting small tensor ranks. Second, a tensorization of weight matrix can decompose the big matrix into many small tensor-core matrices, which can effectively reduce the configuration time of ReRAM. Lastly, the multiplication of small matrix can be performed in a highly parallel fashion on ReRAM to speed up the large neural network processing time.

From the hardware computing architecture perspective, the proposed 3D CMOS-ReRAM accelerator can greatly improve the energy efficiency and neural network processing speed. The matrix–vector multiplication can be intrinsically implemented by ReRAM crossbar. Compared to CMOS, a multibit tensor-core weight can be represented by a single ReRAM, and the addition can be realized by current merging. Moreover, as all the tensor cores for the neural network weights are stored in the ReRAM devices, better area efficiency can be achieved. The power consumption of the proposed CMOS-ReRAM is much smaller than the CMOS implementation due to nonvolatile property of ReRAM. In the TNN accelerator design shown in [Figure 6.24](#Chapter6.html#c06_fig24), only a slice of the 3D matrix is active while most of the matrices are inactive. For traditional CMOS realization, it costs huge static power for the inactive tensor-core weights. But in the discussed architecture, the inactive matrices do not consume power so that the energy utilization is high, resulting a better energy efficiency.

#### 6.2.3 Experimental evaluation of machine learning algorithms on 3D CMOS-ReRAM

##### 6.2.3.1 On-chip design for SLFN-based face recognition

###### Experimental settings

In the experiment, different baselines are implemented for performance comparisons. The detail of each baseline is listed as follows:

**Baseline 1**: General processor. The general process implementation is based on MATLAB on a computer server with 3.46 GHz core and 64.0 GB RAM.

**Baseline 2**: GPU. The GPU implementation is performed by MATLAB GPU parallel toolbox on the same server. An Nvidia GeForce GTX 970 is used for the acceleration of matrix–vector multiplication operations for learning on neuron network.

**Baseline 3**: 3D-CMOS-ASIC. The 3D-CMOS-ASIC implementation with proposed architecture is done by Verilog with 1 GHz working frequency based on CMOS 65nm low power PDK. Power, area and frequency are evaluated through Synopsys DC compiler (D-2010.03-SP2). TSV model in [238] is included for area and power evaluation. 512 vertical TSVs are assumed between layers to support communication and parallel computations [239].

**Proposed 3D-ReRAM-CMOS**: The settings of CMOS evaluation and TSV model are the same as Baseline 3. For the ReRAM-crossbar design evaluation, the resistance of ReRAM is set as ![image](images/ch06_si636.gif) and ![image](images/ch06_si637.gif) as on-state and off-state resistance respectively according to [206] with working frequency of 200 MHz.

###### Performance evaluation
