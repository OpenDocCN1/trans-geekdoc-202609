
![](img/3a09e5358d763329b6e01a25dd2312d4_160_0.png)

Data components

$Y_0 Y_1 Y_2 Y_3 Y_4$

![](img/3a09e5358d763329b6e01a25dd2312d4_160_1.png)

Input layer

Hidden layer 1

Hidden layer 2

Hidden layer 3

Output layer

$Y_0$

$Y_4$

$y_{i+1} = f(W_i y_i + b_i)$

Example with $f()$ as $ReLU(x) = \max(x,0)$

![](img/3a09e5358d763329b6e01a25dd2312d4_160_2.png)

**Figure 5.5** Simple example of a neural network with forward propagation. Source: Adapted from: http://www.rsipvision.com/exploring-deep-learning/.

## 5.4: Arithmetic Precision

## Table 5.3 Examples of arithmetic precision formats

| Formats | Exponent Bits Plus Sign Bit | Mantissas Bits | Numerical Ranges |
|---|---|---|---|
| Floating-point representations | | | |
| Floating-point 32-bits (single-precision fp32) | 9 | 23 | +/- (about $1 \times 10^{-38}$ to about $3 \times 10^{38}$) |
| Floating-point 16-bits (half-precision fp16) | 6 | 10 | +/- (about $6.1 \times 10^{-5}$ to 65,504) |
| Brain floating-point (bfloat16) | 9 | 7 | +/- (about $1 \times 10^{-38}$ to about $3 \times 10^{38}$) |
| Integer Representation | Sign Plus Binary Bits | | |
| Integer 32 (sign int32) | Sign plus 31 bits | | $-2^{31}$ to $2^{31}-1$ |
| Integer 16 (sign int16) | Sign plus 15 bits | | $-2^{15}$ to $2^{15}-1$ |
| Integer 8 (sign int8) | Sign plus 7 bits | | $-2^{7}$ to $2^{7}-1$ |

Google invented a third format called the "brain floating-point." As shown in the table, relative to exponent versus mantissa bits, Google designers sacrificing amount of precision to permit a much larger numerical range than is available with fp16—but maintain a word length of 16 bits.

The IEEE-754 floating-point standard incorporates a format structure that enables more efficient numerical representations. For example, the exponent is implicit by incorporating a bias of 127 for fp32. Similarly, the fp16 incorporates a bias of 15. The binary representation of the mantissa starts with an implicit first bit. This bit is not stored in memory. As shown by Oser [42], the numerical ranges can be calculated by the following formula:

> Numerical decimal value = $(-1)^s \times 2^{(e-bias)} \times (1 + fraction)$

where **s** is either a 0 or a 1 (depending on the sign bit); **e** is the value of exponent (converted from binary to decimal); the **bias** is either 127 for fp32 or 15 for fp16; and **fraction** is the numerical representation of the mantissa value (converted from binary to a fractional decimal). The representation (1 + fraction) is determined by taking the original decimal number (N) and calculating a factor fitting within ($1 \leq N < 2$) times a power of 2 (i.e., $2^{power}$). “Power” is the decimal representation of the exponent term (i., e)—the bias term. Because the first term of (1+fraction) is always 1, the 1 is implicit (hidden) and not stored—saving an extra bit.

There are additional formats in the IEEE-754 floating-point standard, including higher precision, such as double-precision with 64 bits (fp64). Here, we discuss only two examples, fp32 and fp16, to illustrate the main differences and to simplify the discussion.

We now work through an example for fp16. For the largest positive value s=0; e=11110₂(converted to decimal=30); bias=15; fraction f=11111111, (converted to decimal= 2⁻⁴+2⁻²+2⁻³...+2⁻¹⁰), resulting in the largest positive normal value= 2¹⁵ × (1+1023/1024)=65.504. For the smallest positive value s=0; e=00001, (converted to decimal= 1); bias=15; fraction f=00000000, (converted to decimal= 1), resulting in the smallest positive normal value= 2⁻⁴×6.1×10⁻⁵.

We elaborated on these representations to emphasize the importance of precision the maximum and minimum range of values. The larger the number of bits, the higher the range of numerical values achievable, but at the expense of complex hardware requiring more power to perform the addition and multiplication operations. Modern computing hardware designers recognized the importance of mixed precision; during model training, the computation is done at high precision. Contrast, for inference, the computation can be done with a smaller number of bits, resulting in less power consumption and reduced storage.

There is ongoing research to find ways to improve power efficiencies without significant sacrifice in accuracy relative to the IEEE-754 standard [43]. Also, Zhao and colleagues have demonstrated the use of logarithmic system in training and weight updates at lower precision [45]. The benefit of logarithmic approach is that multiplications are performed through lookup tables. Zhao al. demonstrated a reduction in energy consumption of over 90 percent on several well-known computer vision and NLP tasks. In the next sections, we discuss the confluence of algorithm improvements enabled by advances in computing. We also explore various types of accelerators such as GPUs and TPUs, which exploit mixed precision among other design options such as fast interconnects and parallelism.

## 5.5: Confluence of Algorithm Improvements and Computing

The rapid AI advancement across many industries will continue to have a profound impact on societies, helping to solve worldwide problems (i.e., climate change, food shortages, education, and other issues). Economists predict that AI will undergo the typical S-curve, with initially slow acceptance, followed by rapid assimilation into the form of AI products and services, and plateauing once AI reaches maturity. The principal factors in AI adoption and value hinges on many factors discussed throughout this book. Four of the most important technical factors are:

- Data availability (i.e., good and reliable data), as discussed in chapter 3.
- ML algorithms, as discussed in chapter 4.
- Modern computing, which enables ML developers to exploit features with software developments. The most benefit will come from using innovative microprocessor architectures, making hardware well matched to ML parallel structure.
- AI implementation and deployment based on rigorous systems discipline. We elaborate further on this topic in chapters 10 and 11.

In terms of these factors, let us briefly look at ML algorithms and the hardware used to achieve world-record performance. In table 5.4, we itemize several contemporary algorithms, their architecture depth in terms of the number of layers, the training time, the Top-5 error, and GPU hardware. The ILSVRC competition was a phenomenal demonstration of the rapid advances experienced by DNN algorithms from 2012 through 2015, specifically in the computer vision domain. Many of the reasons that led to these advances are just as applicable to other domains (e.g., transformers, automatic speech recognition, and image video segmentation). From table 5.4, we identify several important takeaways:

- The AlexNet DNN was one of the first demonstrations employing the power of advances in GPU technology. It used among several innovative algorithm.

**Table 5.4** Representative DNN algorithms, training time, and hardware used

| DNN Algorithms [46] | Architecture Depth | Top-5 Error | Training Time | GPU Hardware |
|---|---|---|---|---|
| AlexNet [47]; first place in ILSVRC 2012 | 8 layers | 15.3% | 6 days | 2x NVIDIA GTX 580 |
| VGG16 [48]; second place in ILSVRC 2014 | 16 layers | 7.3% | 2–3 weeks | 4x NVIDIA Titan Black |
| GoogLeNet [49]; first place in ILSVRC 2014 | 22 layers | 6.67% | Estimate: 1 week | Used CPUs in training; estimate was <1 week if using contemporary GPUs |
| Google Inception V3 [50]; published in 2015 | 42 layers | 5.6% | 2 weeks | 8x NVIDIA Tesla K40 |
| ResNet50 [51]; first place in ILSVRC 2015 (with 152 layers; 3.57% Top-5 error) | 50 layers | 7.02% | 5 days | 4x NVIDIA Tesla M40 [52] |

ILSVRC = ImageNet Large Scale Visual Recognition Challenge, which contained about 1.2 million training images, 50,000 validation images, and 100,000 test images.

techniques, a dual path employing model parallelism—each of two NVIDIA GPUs processed a subset of the model’s neurons, with the GPUs communicating at each stage of the processing flow—the dual-path results were combined at the end.

- All other subsequent DNN algorithms that won the competition or scored well also used GPUs.
- There was an unprecedented improvement in the reduction of the ResNet-152 DNN algorithm was able to demonstrate a 3.57 percent image classification error, with a neural network depth of 152 layers—about 5x improvement in classification error performance from 2012 to 2015.
- The advancement in GPU technologies was also very remarkable. An NVIDIA GTX 580 had about 3 billion transistors in 40-nanometer process technology. In contrast, the NVIDIA Tesla M40 had about 8 billion transistors in 28-nanometer technology. The NVIDIA Tesla M40 showed more than 4x improvement of
