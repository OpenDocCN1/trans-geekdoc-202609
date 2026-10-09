in managing real-world low-resolution text images, the restoration detail and recognition rates markedly surpass those of the contemporary TBSRN model.

The paper is structured as follows: Section 2 elaborates on the fundamental principles of degradation and transfer learning. In Section 3, the network's architecture is comprehensively explained. Section 4 offers visualizations and numerical comparisons of the approach's results, showcasing its viability. Lastly, Section 5 provides a concise summary of the entire paper and draws conclusions.

# ## 2. Theoretical Foundations

# ### 2.1. Noise

# #### 2.1.1. Gaussian Noise

Gaussian noise is a prevalent random interference encountered in digital signal and image processing, typically originating from imaging tools and transmission pathways. Such interference compromises image clarity, necessitating denoising interventions. Its applications span areas like image denoising, enhancement, and restoration. This study harnesses a three-dimensional Gaussian noise model with zero mean, allowing manual modulation of noise intensity by adjusting the standard deviation, symbolized by the covariance matrix $\Sigma$. It is worth highlighting that the generalized Gaussian noise model can morph into additive Gaussian white noise and grayscale Gaussian noise, though these are extreme cases. Additive Gaussian white noise is characterized by its independent components, each obeying Gaussian distribution principles, leading to its alternative name: Gaussian white noise. Its probability density function follows a normal distribution, with statistical features including zero mean and constant variance. Grayscale Gaussian noise parallels the additive Gaussian white noise in its statistical attributes, maintaining zero mean and uniform variance. Its power spectral density remains constant across frequencies, affecting only pixel grayscale values without altering their hues. Acknowledging the diverse and unpredictable nature of degradation, varying noise intensities are incorporated in the study. Noise levels are uniformly sampled within the range $\{1/255, 2/255, \ldots, 5/255\}$, generating samples under three scenarios with respective probabilities of 0.4, 0.4, and 0.2. The probability density function of Gaussian noise can be represented as follows:

```
$$p(z) = \frac{1}{\sqrt{2\pi\sigma^2}}\exp\left\{-(z-\mu)^2/2\sigma^2\right\}. \tag{1}$$
```

where 'exp' denotes the exponential function based on the natural constant e; 'z' is the grayscale image value; '$\mu$' signifies the expected value of z; and '$\sigma$' stands for the standard deviation of z.

# #### 2.1.2. JPEG Compression Noise

JPEG, short for Joint Photographic Experts Group, is an image compression standard tailored specifically for compressing natural, real-world full-color or grayscale imagery. Its primary objective is to minimize data redundancy, facilitating efficient data storage or transmission. The JPEG compression mechanism can introduce various types of noise, among which quantization noise and encoding noise are most prevalent. Quantization noise emerges due to errors in the quantization process post the DCT (discrete cosine transform) phase in JPEG compression. High-frequency components within images tend to be more susceptible to these quantization inaccuracies, leading to image distortions and the appearance of noise. Encoding noise, on the other hand, arises when quantized coefficients undergo encoding. To conserve the data stream, the encoding phase employs compression techniques such as Huffman coding and run-length encoding. While these methods manage to reduce the bitrate without compromising image integrity, they can inadvertently add some noise.

Recognizing that low-resolution text images in real-world settings often undergo significant compression, this study sets the image compression quality factor range between [20, 65]. This choice mirrors actual degradation conditions and accentuates the randomness