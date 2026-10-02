# 2.2.2. The Decoder Module

The network architecture of the decoder module is illustrated in Figure 2. The feature vector y is first upsampled to y′ using nearest-neighbor interpolation [42]. The length of y′ is determined by Equation (3):

length(y′) = ⌈√M⌉², (3)

where M is the length of vector y. The symbol [z] means rounding number z to the nearest integer more than or equal to z. The vector y′ is then reshaped into the initial feature map F using Equation (4):

F[i,j] = y′[(i − 1) × ⌈√M⌉ + j], 1 ≤ i,j ≤ ⌈√M⌉. (4)

Afterwards, the initial feature map F is convolved with 96 filters of size 3 × 3. We empirically add a batch-normalization [43] layer after the first convolution layer to accelerate training. Then the feature maps go through several residual units. Some residual units are followed by nearest-neighbor upsampling operation as in Figure 2. Finally, the feature maps are convolved with one filter of size 1 × 1 to derive the recovered image x̂.

![](bbox=[0.12, 0.48, 0.9, 0.6])

Figure 2. The network architecture of the decoder module.

# The residual units.

The introduction of residual units is inspired by [44]. As depicted in Figure 3, two types of residual units are used. Both types follow the two-branch connection pattern. The feature maps go through the two branches and add up at the output summator. The upper branches of the two types are identical. The lower branches differ in that residual unit (1) connects the input and the output with a stack of layers, but residual unit (2) connects the input and the output directly. Each convolution layer that appears in Figure 3 is composed of 96 filters of size 3 × 3. After each convolution layer, there is a batch-normalization layer [43]. Each batch-normalization layer is then followed by a Leaky ReLU activation layer [45] if the batch-normalization layer is not directly connected to the output summator.

The nearest-neighbor upsampling operations. If the input image x is of size n × n, then the second, third, and fourth upsampling operation in Figure 2 resize the feature maps to size ½ n × ½ n × 96, ¾ n × ¾ n × 96, and n × n × 96, respectively.