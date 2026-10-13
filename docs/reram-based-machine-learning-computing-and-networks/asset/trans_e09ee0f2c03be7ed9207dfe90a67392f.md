

### 步骤 3：异或（XOR）

此步骤旨在通过运算 ![image](images/ch06_si614.gif) 识别 ![image](images/ch06_si613.gif) 的索引。请注意，仅当 ![image](images/ch06_si616.gif) 和 ![image](images/ch06_si617.gif) 来自步骤 1 时，![image](images/ch06_si615.gif) 才成立。ReRAM 交叉阵列输入与电阻的映射也如图 22(c) 所示，阈值电压配置为 ![image](images/ch06_si618.gif)。因此，通过异或运算识别 ![image](images/ch06_si619.gif) 的索引。

### 步骤 4：编码

第三步产生二进制格式的 ![image](images/ch06_si620.gif) 作为编码器，其阈值同步骤 2。第二步的输入产生类似 ![image](images/ch06_si621.gif) 的结果，其中仅当 ![image](images/ch06_si622.gif) 输入为 ![image](images/ch06_si623.gif) 时成立。结果是，仅读出第 ![image](images/ch06_si624.gif) 行，且此步骤中不发生电流合并。相应的二进制格式 ![image](images/ch06_si625.gif) 为中间结果，存储在第 ![image](images/ch06_si626.gif) 行中，如[图 6.23](#Chapter6.html#c06_fig23)(c)所示。编码步骤需要一个 ![image](images/ch06_si627.gif) ReRAM 交叉阵列，其中 ![image](images/ch06_si628.gif) 为用二进制格式表示 ![image](images/ch06_si629.gif) 到 ![image](images/ch06_si630.gif) 所需的位数。

通过应用这四个步骤，可将不同的张量核映射到 ReRAM 交叉阵列上，以并行执行矩阵-向量乘法。与最先进的实现相比，该方法能更快、更节能地执行矩阵-向量乘法。

#### 6.2.2.2 在单层架构上映射 TNN

此外，本节展示了如何根据第 4.4 节的算法和网络，映射基于两层 TNN 的推理过程。本节进一步讨论了如何利用 3D 单层 CMOS-ReRAM 架构设计 TNN 加速器。与第 2.2 节的映射相比，分布式映射可实现更高的并行度。

##### TNN 加速器设计

根据公式 (4.28)，![image](images/ch06_si631.gif) 需要与 ![image](images/ch06_si632.gif) 矩阵相乘，这与通用神经网络不同。在该公式中，只需从每个张量核中取出 3D 矩阵的一个切片（即 2D 矩阵）来执行矩阵-向量乘法。因此，计算复杂度可显著降低。我们在[图 6.24](#Chapter6.html#c06_fig24)中展示了 TNN 两个隐藏层之间的详细加速器设计。由于神经网络参数被压缩，遵循图 5.12(b)，可将 TNN 的所有权重存储在 ReRAM 交叉阵列中。输入数据 ![image](images/ch06_si633.gif) 由多个张量核、CMOS 池化和激活函数串行处理。

![image](images/PBPC0390-06-f24.jpg)

**图 6.24** 用于 TNN 的高并行 3D 单层 CMOS-ReRAM 加速器映射细节

张量核的详细设计也如[图 6.24](#Chapter6.html#c06_fig24)所示。在每个张量核中，必须将 3D 矩阵的不同切片存储在不同的 ReRAM 交叉阵列中。由于一次仅使用一个 2D 矩阵，因此使用两个张量核多路选择器（MUX），以便仅将一个矩阵连接到输入电压和输出 ADC。TC 选择模块根据 ![image](images/ch06_si634.gif) 和 ![image](images/ch06_si635.gif) 控制输入和输出 MUX。对于中间的张量核，可移除 ADC/DAC 对，因为 ReRAM 交叉阵列输入不需要数字表示。

##### TNN 在 3D CMOS-ReRAM 架构上的优势总结

从算法优化角度来看，这种张量化有利于实现大型神经网络。首先，通过执行张量化，可压缩神经网络的规模。此外，采用小张量秩也可降低计算负载。其次，权重矩阵的张量化可将大矩阵分解为许多小的张量核矩阵，从而有效减少 ReRAM 的配置时间。最后，小矩阵的乘法可在 ReRAM 上以高度并行的方式执行，以加速大型神经网络的处理时间。

从硬件计算架构角度来看，所提出的 3D CMOS-ReRAM 加速器可大幅提高能效和神经网络处理速度。矩阵-向量乘法可由 ReRAM 交叉阵列固有实现。与 CMOS 相比，多位张量核权重可由单个 ReRAM 表示，加法可通过电流合并实现。此外，由于所有用于神经网络权重的张量核均存储在 ReRAM 器件中，可实现更好的面积效率。由于 ReRAM 的非易失性，所提出的 CMOS-ReRAM 功耗远小于 CMOS 实现。在[图 6.24](#Chapter6.html#c06_fig24)所示的 TNN 加速器设计中，仅 3D 矩阵的一个切片处于激活状态，而大多数矩阵处于非激活状态。对于传统 CMOS 实现，非激活张量核权重会消耗巨大的静态功耗。但在所讨论的架构中，非激活矩阵不消耗功率，从而实现了高能量利用率，带来了更好的能效。

#### 6.2.3 基于 3D CMOS-ReRAM 的机器学习算法实验评估

##### 6.2.3.1 基于 SLFN 的人脸识别片上设计

###### 实验设置

实验中实现了不同的基线以进行性能比较。各基线详情如下：

**基线 1**：通用处理器。通用处理器实现基于配备 3.46 GHz 核心和 64.0 GB 内存的计算机服务器上的 MATLAB。

**基线 2**：GPU。GPU 实现在同一服务器上通过 MATLAB GPU 并行工具箱执行。使用 Nvidia GeForce GTX 970 加速神经网络学习中的矩阵-向量乘法运算。

**基线 3**：3D-CMOS-ASIC。基于所提架构的 3D-CMOS-ASIC 实现基于 CMOS 65nm 低功耗 PDK，使用 Verilog 完成，工作频率为 1 GHz。通过 Synopsys DC 编译器 (D-2010.03-SP2) 评估功耗、面积和频率。引用 [238] 中的 TSV 模型用于面积和功耗评估。假设层间有 512 个垂直 TSV 以支持通信和并行计算 [239]。

**所提 3D-ReRAM-CMOS**：CMOS 评估设置和 TSV 模型与基线 3 相同。对于 ReRAM 交叉阵列设计评估，根据 [206]，ReRAM 电阻分别设置为 ![image](images/ch06_si636.gif) 和 ![image](images/ch06_si637.gif) 作为导通态和截止态电阻，工作频率为 200 MHz。

###### 性能评估

