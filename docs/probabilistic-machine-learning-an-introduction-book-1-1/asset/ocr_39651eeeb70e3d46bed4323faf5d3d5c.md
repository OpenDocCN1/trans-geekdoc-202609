![](bbox=[0.17, 0.14, 0.5, 0.33])

![](bbox=[0.55, 0.13, 0.85, 0.33])

*Figure 14.6: Illustration of padding and strides in 2d convolution. (a) We apply “same convolution” to a 5 × 7 input (with zero padding) using a 3 × 3 filter to create a 5 × 7 output. (b) Now we use a stride of 2, so the output has size 3 × 4. Adapted from Figures 14.3–14.4 of [Gér19].*

input. This is called **strided convolution**. This is illustrated in Fig. 14.6a, where we convolve a 5 × 7 image with a 3 × 3 filter with stride 2 to get a 3 × 4 output.

In general, if the input has size $x_h \times x_w$, we use a kernel of size $f_h \times f_w$, we use zero padding on each side of size $p_h$ and $p_w$, and we use strides of size $s_h$ and $s_w$, then the output has the following size [DV16]:

$$\left\lfloor \frac{x_h + 2p_h - f_h + s_h}{s_h} \right\rfloor \times \left\lfloor \frac{x_w + 2p_w - f_w + s_w}{s_w} \right\rfloor \tag{14.10}$$

For example, consider Fig. 14.6(a). We have $p = 1$, $f = 3$, $s = 1$, $x_h = 5$ and $x_w = 7$, so the output has size

$$\left(\left\lfloor \frac{5 + 2 - 3 + 1}{1} \right\rfloor, \left\lfloor \frac{7 + 2 - 3 + 1}{1} \right\rfloor\right) = \left(\left\lfloor \frac{5}{1} \right\rfloor, \left\lfloor \frac{7}{1} \right\rfloor\right) = 5 \times 7 \tag{14.11}$$

In general, if we use padding which is half the filter size, $p = \lfloor f/2 \rfloor$, (where $f$ is odd), then the output will have the same size as the input.

Now consider Fig. 14.6(b), where we set the stride to $s = 2$. Now the output is smaller than the input.

$$\left(\left\lfloor \frac{5 + 2 - 3 + 2}{2} \right\rfloor, \left\lfloor \frac{7 + 2 - 3 + 2}{2} \right\rfloor\right) = \left(\left\lfloor \frac{6}{2} \right\rfloor, \left\lfloor \frac{4}{1} \right\rfloor\right) = 3 \times 4 \tag{14.12}$$

# 14.2.4.1 Multiple input and output channels

In Fig. 14.5, the input was a gray-scale image. In general, the input will have multiple **channels** (e.g., RGB, or hyper-spectral bands for satellite images). We can extend the definition of convolution to this case by defining a kernel for each input channel; thus now **W** is a 3d weight matrix or **tensor**.