
# 6.2.1 Mapping SLFN on 3D Multilayer CMOS-ReRAM Architecture

The details of this section are obtained from [235]. This work presents mapping the SLFN-based learning and inference processes according to the algorithm and network in Section 4.2. This section will focus on the mapping of all the matrix–vector multiplication operations on ReRAM crossbar and other operations in CMOS. Multilayer 3D CMOS-ReRAM architecture in Figure 5.13 is used for the acceleration.

This section will first discuss the data quantization on the proposed architecture. Then this section illustrates how to map matrix–vector multiplication on ReRAM-crossbar layer. Finally, CMOS-ASIC accelerator is also designed in Layer 3 for remaining operations in pipelined and parallel fashion.

## 6.2.1.1 Data Quantization

To implement the whole training algorithm on the proposed 3D multilayer CMOS-ReRAM accelerator, the precision of the real values requires a careful evaluation. Compared to the software double precision floating point format (64-bit), the values in the training algorithm are truncated into finite precision. By cross-validation from software, a balanced point between hardware resource and testing accuracy can be achieved. A general `N`-bit fixed point representation with `I`-bit integer and `F`-bit fraction point is shown as follows:

```
Value = (-1)^S * (I_bits + F_bits)
```

In the described accelerator, one needs to first assign a fixed 16 bit-width for normalized input data such as `x` and `y` with scale factor `S_x` and `S_y`. For weights such as `A` and `B` in SLFN, one can determine `I` by finding the logarithm of dynamic range (i.e., `log2(max|W|)`) and `F` is set as `N - I`. Furthermore, one needs to apply greedy search method based on the testing accuracy to find the optimal bit-width. The bit-width is reduced with cross-validation applied to evaluate the effect. By dynamic tuning the bit-width, our objective is to find the minimum bit-width with acceptable testing accuracy loss.

## 6.2.1.2 ReRAM Layer Implementation for Digitized Matrix–Vector Multiplication

The matrix–vector multiplication is illustrated with the example of output layer (4.7) calculation, where each element in `H` is calculated using `H = X * W`. Such a multiplication can be expressed in terms of binary multiplication [147].

```
H_acc = Σ (X_bin[i] XOR W_bin[j]) * 2^(i+j)
```

where `H_acc` is the accelerated result from ReRAM crossbar. `X_bin` is the binary bit of `X` with `N_x` bit-width and `W_bin` is the binary bit of `W` with `N_w` bit-width. As mentioned above, bit-width `N_x` and `N_w` are decided using cross-validation in design to achieve balanced accuracy and hardware usage [236].

**Step 1: Parallel Digitizing**: It requires an `N_x * N_w` ReRAM crossbar. Each inner product is produced ReRAM crossbar as shown in Figure 6.19(a). `X` is set as crossbar input and `W` is written in ReRAM cells. In the `N_x * N_w` ReRAM crossbar, resistance of ReRAMs in each column is the same, but `R_col` among columns is different. As a result, the output of each column mainly depends on ladder-like threshold voltages `V_th`. If the inner-product result is `P`, the output of Step 1 is like `O = [0, ..., 0, 1, 1, ..., 1]`, where `k` and `m`.

![Figure 6.19 Detailed mapping for digitalized matrix–vector multiplication on ReRAM crossbar: (a) parallel digitizing; (b) XOR; (c) encoding; (d) legend of mapping](images/PBPC0390-06-f19.jpg)

**Step 2: XOR**: It is to identify the index of `k` with the operation `X_bin XOR W_bin`. Note that `XOR_out` is `1` only when `X_bin` and `W_bin` from Step 1. The mapping of ReRAM-crossbar input and resistance is shown in Figure 6.19(b), and threshold voltage configuration is `V_th_xor`. Therefore, the index of `k` is identified by XOR operation.

**Step 3: Encoding**: The third step produces `H_bin` in binary format as an encoder with the thresholds as Step 2. The input from the second step produces `O_xor` like result where only the `k`-th input is `1`. As a result, only the `k`-th row is read out and no current merge occurs in this step. The according binary format `H_bin` is an intermediate result and stored in the `k`-th row, as shown in Figure 6.19(c). Encoding step needs an `N_h * N_h` ReRAM crossbar, where `N_h` is the number of bits in order to represent `0` to `2^N_h - 1` in binary format.

## 6.2.1.3 CMOS Layer Implementation for Decoding and Incremental Least-Squares

In the CMOS layer, decoding and more complex operations for incremental least-squares solution are designed. Since the output from ReRAM layer is in binary format, decoding is required to obtain the real values. Adder and shifter are designed in Layer 3 with CMOS to complete this process as shown in Figure 6.20.

![Figure 6.20 Inner-product operation on ReRAM crossbar](images/PBPC0390-06-f20.jpg)

To fully map the incremental machine learning on the proposed 3D multilayer CMOS-ReRAM accelerator, there are following operations needed in CMOS-ASIC including sorting in (4.3), nonlinear mapping in (4.4) and division. Figure 6.21 shows the detailed mapping of the supervised classification on the proposed 3D multilayer CMOS-ReRAM accelerator. The ReRAM logic layer (Layer 2) will work as vector core with parallel process elements for multiplication and summation. The scalar core is implemented to perform scalar operation including division. A sequential divider is implemented with five-stage pipelines to reduce critical path latency. Nonlinear mapping such as Sigmoid function for activation is also implemented in LUT (4.4). As a result, the whole training process including both feature extraction and classifier learning can be mapped to the proposed 3D multilayer CMOS-ReRAM accelerator with small accuracy loss.

![Figure 6.21 Detailed pipelined and parallel mapping of CMOS-ASIC accelerator](images/PBPC0390-06-f21.jpg)

# 6.2.2 On-chip Design for TNNs

TNNs are another prominent class of machine learning architectures in the present time. In this section, we will map a two-layer TNN-based inference processes according to the algorithm and network in Section 4.4. This section also discusses how to utilize the proposed 3D multilayer CMOS-ReRAM architecture to design the TNN accelerator.

## 6.2.2.1 Mapping on Multilayer Architecture

Let us first discuss the CMOS layer design, which performs the high-level control of TNN computation. Then a highly parallel ReRAM-based accelerator is introduced with the TNN architecture and dot-product engine.

### CMOS Layer Accelerator
