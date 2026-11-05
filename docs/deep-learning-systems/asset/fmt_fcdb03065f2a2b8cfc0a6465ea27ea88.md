
## Posit
`Posit` is a relatively new format different from the IEEE floating standard. This format requires less power and die area than the IEEE floating-point counterpart \[Gus17, Joh18\]. It does not overrepresent NaNs and provides other benefits and drawbacks \[dDF+19\]. However, this format has minimal adoption in academia and none in industry.

## Log-domain
`Log-domain` is another form of nonlinear quantization that has been shown to maintain statistical performance with smaller numerical formats \[LMC+17\]. This format has limited adoption in academia and none in industry.

## Binary and ternary
`Binary` (1 bit) and `ternary` (2 bits to represent –1, 0, and 1) have been used in research, in particular, to represent the weights in a forward propagation passes \[ROR+16, HS14\].

## Die Cost
The die cost to build a multiplier, and the power cost to use the multiplier both exhibit quadratic growth with the number of mantissa bits and increase linearly with the number of exponent bits. Therefore, a `bf16` multiplier is less expensive than a `fp16` multiplier. However, area costs continue to decrease rapidly, and therefore this difference should not be a major factor in the DL hardware design decisions. Usability and software development costs are much more critical factors.

To facilitate transitioning from hardware that only support one format (`fp16` or `bf16`), we recommend designing hardware that supports both `bf16` and `fp16` formats using a 19-bit (1, 8, 10) floating-point unit (`FPU`). Similarly, we recommend supporting both (1, 5, 2) and (1, 4, 3) `fp8` formats using a 9-bit (1, 5, 3) `FPU`. According to IBM, supporting both formats only requires a 5% larger unit than supporting one format \[SCC+19\].

## 6.2 QUANTIZATION METHODOLOGY
Using `int8` can improve the computational performance at the expense of some (1) additional development and (2) loss in statistical performance. In this section, we explain the quantization methodology and share techniques that can mitigate loss in statistical performance and reduce the development process.

Assuming an `fp32`, `fp16`, or `bf16`, trained model a simple technique to quantize to `int8` is as follows: For each weight tensor, the maximum absolute value is mapped to ±127. For the activation tensors, a representative sample of the production data, called the `calibration dataset`, is used to collect activations statistics to find the distribution of activation values in each tensor across the samples. The quantization factor is:

![image](images/pg119_1.png)

where `T[a,w]` is a tensor corresponding to either the weights `w` or the activations `a` (recall that the inputs to the NN can be considered the activations of Layer 0). The quantized values are:

![image](images/pg119_2.png)

where the function `Φ(·)` rounds to the nearest integer.

The following techniques can improve `int8` inference accuracy. Note that even with these techniques, the loss over `fp32` accuracy may still be unacceptable for some applications.

### Asymmetric quantization
Asymmetric quantization uses a scalar and a shift factor, which can improve the quantization of the activations. Note that the weights are typically approximately zero-mean and should use symmetric quantization. The minimum activation value gets mapped to –128 and the maximum value to 127.

### Threshold calibration
Threshold calibration requires deployment-like data (unlabeled data is OK) and no additional backpropagation. Mapping the largest absolute value to ± 127 (or in asymmetric quantization the minimum and maximum value to –128 and 127, respectively) may result in poor utilization of the available 256 `int8` values when an outlier number is much larger than the other numbers. To illustrate, suppose the largest number is 10× larger than the next largest value. That one number gets mapped to 127, and the rest of the values can only map to \[–13, 13\]. It is better to ignore outliers and find a threshold that minimizes the reconstruction error back to `fp32`. Another approach that works for some CNN models is to truncate outliers to minimize the information loss measured by the KL-divergence between the larger numerical representation tensor distribution and the quantized tensor distribution \[Mig17\]. Note that KL-divergence minimizes a metric of error in a layer, which may not minimize the accuracy error in the entire model. In practice, just using a threshold that captures 99% or 99.9% of the values results in superior performance accuracy.

### Quantization aware training (QAT)
Quantization aware training (QAT) requires labeled data (training data) and backpropagation. QAT (as opposed to post-training quantization) fine-tunes a model while enforcing quantization, and has been shown to improve accuracy. At each training iteration, the weights and activations of the layers targeted for quantization are fake-quantized to mimic `int8` values. The cost used in the backpropagation is based on the quantized values. The gradients and the weights updates are computed in single-precision. Another advantage is that QAT eliminates the need for the threshold calibration step as QAT minimizes the reconstruction error of the quantized values.

### Selective quantization
Selective quantization requires labeled data but no backpropagation. Some layers, such as softmax, tanh, sigmoid, depthwise-separable convolution, GELU, and the input and output layers, are more sensitive to quantization and should be kept at the larger numerical format to reduce the accuracy loss \[Wu19\]. The sensitivity of softmax can be slightly reduced by accumulating the logits in the larger numerical format and subtracting the max value before quantizing \[BHH20\]. The activation output of GELU can be clipped, for instance, to 10, in order to allow some `int8` value to represent the GELU negative activation values.

Analyzing an approximation of the Hessian matrix’s trace is recommended to assess the sensitivity of a layer. This technique can be used to reduce the numerical format to 4 bits for some layers with minimal accuracy loss \[DYC+19\]. Other less reliable but faster-to-compute metrics to assess sensitivity are the KL-divergence, and the root mean squared error (RMSE) with the reconstructed `fp32` model. RL can facilitate designing a quantized model optimized for latency, energy, and accuracy for a particular hardware target. A possible algorithm for selective quantization follows:

![image](images/pg121_1.png)

This algorithm determines the layers that can be quantized. Note that one challenge is that interleaving layers with large and small numerical formats may result in higher computational cost from the overhead of the many conversions.

### Cross-layer range equalization
Cross-layer range equalization is a data-free quantization (requires no data and no back-propagation). The range of weights across the layers is equalized, and the range of activations are constraint under the assumption that a piece-wise linear activation function (such as ReLU) is used between the layers \[NvB+19\]. This constraint is satisfied by many CNN models but not by non-CNN models. This technique is used in the Qualcomm Neural Processing SDK.

### Channel-wise quantization
Channel-wise quantization uses a quantization factor for each channel rather than one factor for the entire tensor.

### Stochastic rounding
Stochastic rounding (rather than nearest-value rounding) after multiplying by the quantization factor can improve performance \[WCB+18\]. To illustrate, rather than rounding the number 1.2 to the number 1, it is rounded to 1 with 80% probability and to 2 with 20% probability.

### Unsigned int8 ReLU activations
Unsigned `int8` ReLU activations uses the unsigned `int8` representation, rather than signed `int8`, for the activations of the ReLU functions. Using signed `int8` wastes half of the values since all the activations are nonnegative.

The techniques QAT, selective quantization, channel-wise quantization, and stochastic rounding also benefit `fp8` \[CBG+20\].

## 6.3 PRUNING AND COMPRESSION
