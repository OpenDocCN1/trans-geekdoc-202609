
Moreover, the pooling operation is optionally applied to select the most significant information from the features, which performs a downsampling across an `![image](images/ch07_si62.gif)` contiguous region on the feature. There are two kinds of pooling schemes commonly used in CNN-based network: max-pooling and average-pooling. The max-pooling takes the maximum value of the pooling region while the average-pooling takes the mean value of the pooling region. The deep ResNet begins with a max pooling and ends with a global average pooling layer and a `![image](images/ch07_si63.gif)`\-way fully connected (FC) layer with a softmax layer. To save runtime memory and storage usage in inference, we can do the fusion as `![image](images/ch07_si64.gif)` function commutes with the max-pooling function:

```
![image](images/ch07_eqn9.gif)
```

and the quantized max-pooling, called the QPooling, is applied with the following equation:

```
![image](images/ch07_eqn10.gif)
```

where `![image](images/ch07_si65.gif)` and `![image](images/ch07_si66.gif)` are the features before and after pooling, respectively.

#### 7.2.5 Quantized deep neural network overview

The overall working flow of the deep ResNet model with quantization and parallelization is presented in [Figure 7.3](#Chapter7.html#c07_fig3). After the first layer, the QPooling will primarily work and feed the downsampled features into 4-bit QConv. Then each 4-bit QConv layer conducts a quantized convolution between 4-bit quantized features and weights. Then the feature output of QConv will be further processed by the QBN and QReLUs function. After every three convolution layers, the add-residual operation will be performed with 4-bit quantized parameters at the end of residual block.

As all the major parameters and expensive computation are performed with 4-bit quantization, the proposed 4-bit ResNet will get much less storage cost, faster speed as well as higher energy efficiency.

**Algorithm 7.1:** Training quantized ResNet with 4-bit weights, features. `![image](images/ch07_si67.gif)` is the number of layers and `![image](images/ch07_si68.gif)` is the parameter gradient.

**Require**: previous inputs `ak−1` and previous weights `wk`

**Ensure**: updated weights `w∗ k` .

1. Computing the forward flow:

```
1: for k = 1 : L do
2: wq k ← quantize(wk )
3: a q k−1 ← quantize(ak−1)
4: s q k ← compute(wb k , a q k−1)
5: a qbn k ← compute(s q k ,μ, σ2, γ , β)
6: if max-pooling layer then
7: a qp k ← compute(a qbn k )
8: a qrelu k ← compute(a qp k )
9: else
10: a qrelu k ← compute(a qbn k )
11: end if
12: a q k ← a qrelu k
13: end for
```

2. Computing the backward gradients:

```
14: for k = L : 1 do
15: ga q k−1 ← backward(ga q k ,wq k )
16: gwq k ← backward(ga q k , a q k−1)
17: end for
```

3. Accumulating the parameters gradients:

```
18: for k = 1 : L do
19: w∗ k ← update(wq k , gwq k )
20: end for
```

#### 7.2.6 Training strategy

The detailed training strategy is presented in Algorithm 2.5. The network is assumed to have a feedforward linear topology, and the computation is performed with 4-bit quantization with high parallelism and efficiency. Note that the `![image](images/ch07_si86.gif)` and `![image](images/ch07_si87.gif)` functions represent the corresponding quantization and computation methods mentioned above, the `![image](images/ch07_si88.gif)` function specifies how to calculate parameter gradients in the backward propagation [254], and the `![image](images/ch07_si89.gif)` function presents how to update the parameters when their gradients are known [269].

After training, the proposed 4-bit ResNet model can be obtained, which is highly compressed through quantization. Compared to the original ResNet, the quantized ResNet benefits a lot from the large compression and high parallelization. It will reduce the complexity and enlarge the throughput of networks with low-bitwidth parameters, so that the implementation on the in-memory device also becomes more realizable.

### 7.3 Device for in-memory computing

In this section, the ReRAM-crossbar device will be presented which can be used for both storage and computation. And it will be employed to support a CMOS-ReRAM in-memory computing accelerator. The large-scale deep ResNet with quantization which has been discussed in Section 7.2 will be mapped.

#### 7.3.1 ReRAM crossbar

ReRAM [62] is an in-memory computing device facing the future. The different resistance states of ReRAM can represent different parameters while computing. Besides working as storage memory, a ReRAM crossbar can be applied to perform logic operations [263], especially the dot-product-based convolutions.

Previous works in [258, 259] usually choose the two-terminal ReRAM device which only has two nonvolatile states: high-resistance state (HRS) and low-resistance state (LRS) to build an in-memory architecture, as shown in [Figure 7.4](#Chapter7.html#c07_fig4)(a). However, when the applied network becomes deeper and more complex, the two-terminal computing results in limitation on the performance of ReRAM crossbar while sacrifices the accuracy of network. For the implementation of proposed 4-bit ResNet-50, we apply the ReRAM model in [270], which has multibit resistance states. The states of proposed ReRAM device are determined by the distribution of set voltage `![image](images/ch07_si90.gif)`.

```
![image](images/PBPC0390-07-f04.jpg)
```

Figure 7.4 (a) Traditional two-terminal ReRAM crossbar; (b) 4-bit ReRAM crossbar with 4-bit DAC/ADC circuits

In one ReRAM crossbar, given the input probing voltage `![image](images/ch07_si91.gif)` on each writeline (WL), the current `![image](images/ch07_si92.gif)` on each bitline (BL) becomes the natural multiplication–accumulation of current through each ReRAM device. Therefore, the ReRAM-crossbar array can intrinsically perform the matrix–vector multiplication. Given an input voltage vector `![image](images/ch07_si93.gif)`, the output vector `![image](images/ch07_si94.gif)` can be expressed as

```
![image](images/ch07_eqn11.gif)
```

where `![image](images/ch07_si95.gif)` is configurable conductance of the ReRAM resistance `![image](images/ch07_si96.gif)`, which can represent real value of weights. Compared to the traditional CMOS implementation, the ReRAM device can achieve a higher level of parallelism and consumes less power including standby power.

Different from the traditional non-quantized two-terminal ReRAM crossbar, the proposed 4-bit quantized ReRAM crossbar is shown in [Figure 7.4](#Chapter7.html#c07_fig4)(b), and the 4-bit resistance is configured for each ReRAM device. Moreover, the novel designed 4-bit DACs are applied on WL to transfer the digital input, and the 4-bit ADCs are applied on BL to identify the analog output. Therefore, the sensed analog output can be encoded in quantized digital signal to produce the multiplied result [237].

Compared to the two-terminal ReRAM crossbar, the 4-bit ReRAM crossbar has a better robustness on the IR-drop in the large-size implementation, so that the wire resistance affects little on IR-drop. In addition, since only 4-bit inputs are configured in quantized ReRAM crossbar, it has a better programming accuracy and can provide a better strategy for mapping deeper and large-scale networks.

#### 7.3.2 Customized DAC and ADC circuits
