| | Max pooling | Average pooling |
|---|---|---|
| Purpose | Each pooling operation selects the maximum value of the current view | Each pooling operation averages the values of the current view |
| Illustration | max pooling illustration | avg pooling illustration |
| Comments | - Preserves detected features
- Most commonly used | - Downsamples feature map
- Used in LeNet |

![](bbox=[0.58, 0.08, 0.85, 0.13])

Zero-padding – Zero-padding denotes the process of adding P zeroes to each side of the boundaries of the input. This value can either be manually specified or automatically set through one of the three modes detailed below:

| | Valid | Same | Full |
|---|---|---|---|
| Value | P = 0 | P_start = [ S⌈I/S⌉ - I + F - S / 2 ]  P_end = [ S⌈I/S⌉ - I + F - S / 2 ] | P_start ∈ [0,F-1]  P_end = F - 1 |
| Illustration | zero padding valid illustration | zero padding same illustration | zero padding full illustration |
| Purpose | - No padding
- Drops last convolution if dimensions do not match | - Padding such that feature map size has size ⌈I/S⌉
- Output size is mathematically convenient
- Also called 'half' padding | - Maximum padding such that end convolutions are applied on the limits of the input
- Filter 'sees' the input end-to-end |

Fully Connected (FC) – The fully connected layer (FC) operates on a flattened input where each input is connected to all neurons. If present, FC layers are usually found towards the end of CNN architectures and can be used to optimize objectives such as class scores.

![](bbox=[0.13, 0.41, 0.48, 0.57])

# 1.3 Filter hyperparameters

The convolution layer contains filters for which it is important to know the meaning behind its hyperparameters.

Dimensions of a filter – A filter of size F × F applied to an input containing C channels is a F × F × C volume that performs convolutions on an input of size I × I × C and produces an output feature map (also called activation map) of size O × O × 1.

![](bbox=[0.06, 0.74, 0.49, 0.85])

*Remark: the application of K filters of size F × F results in an output feature map of size O × O × K.*

Stride – For a convolutional or a pooling operation, the stride S denotes the number of pixels by which the window moves after each operation.

# 1.4 Tuning hyperparameters

Parameter compatibility in convolution layer – By noting I the length of the input volume size, F the length of the filter, P the amount of zero padding, S the stride, then the output size O of the feature map along that dimension is given by:

$$O = \frac{I - F + P_{start} + P_{end}}{S} + 1$$

![](bbox=[0.61, 0.71, 0.87, 0.87])

*Remark: often times, P_start = P_end ≡ P, in which case we can replace P_start + P_end by 2P in the formula above.*