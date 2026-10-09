
Recently, Vinker [21] proposed adaptive curve-based compression (ACC) for pre-processing of DNN algorithms, which maps and normalizes the input image through the following transformations:

$$\tilde{I} = \frac{\log(\lambda \cdot \frac{I}{I_{max}} + \varepsilon)}{\log(\lambda + \varepsilon)},\tag{6}$$

where $\lambda$ is the scaling factor and the selection rule of $\lambda$ is to minimize the following cross-entropy:

$$\arg \min_\lambda - \sum_t H_l(\tilde{I}) \log(H_l(\mathrm{LDR})) ,\tag{7}$$

where $H(.)$ represents the histogram. $H(\tilde{I})$ as a function of $\lambda$ denotes the histogram of $\tilde{I}$ and $H(\mathrm{LDR})$ represents the histogram of native LDR images. $H(\mathrm{LDR})$ is obtained by averaging the histogram of 900 high-quality images in the DIV2k [29] dataset. All histograms use 20 bins indexed by $l$.

Inspired by the above works, we construct a unified TM algorithms’ preprocessing format named adaptive logarithmic transformation AdaLogT:

$$\tilde{I} = \frac{\log(I \cdot 10^p + 1)}{\log(I_{max} \cdot 10^p + 1)} \triangleq \textit{AdaLogT}(I;p) ,\tag{8}$$

where $I_{max}$ represents the maximum value of image $I$. $\tilde{I}$ is strictly limited to the range $[0,1]$ after normalization.

Equations (2), (3), and (5) can be expressed in the form of Equation (8). In fact, Equation (5) corresponds to the special case of $p=6$ in Equation (8). For Equation (2), we have

$$\tilde{I} = \log(I + \varepsilon) = \log(\frac{1}{\varepsilon} \cdot I + 1) + \log(\varepsilon) ,\tag{9}$$

For $\tilde{I}_{min}$, $\tilde{I}_{max}$, there are

$$\begin{aligned} \tilde{I}_{min} & = \log(I_{min} + \varepsilon) = \log(\frac{1}{\varepsilon} \cdot \tilde{I}_{min} + 1) + \log(\varepsilon) , \\ \tilde{I}_{max} & = \log(I_{max} + \varepsilon) = \log(\frac{1}{\varepsilon} \cdot \tilde{I}_{max} + 1) + \log(\varepsilon) , \end{aligned}\tag{10}\tag{11}$$

Since $\tilde{I}_{min} = 0$, bringing Equations (9)–(11) into Equation (8) has

$$\begin{aligned} \tilde{I} &= \frac{\log(\frac{1}{\varepsilon} \cdot I + 1) - \log(\frac{1}{\varepsilon} \cdot I_{min} + 1)}{\log(\frac{1}{\varepsilon} \cdot I_{max} + 1) - \log(\frac{1}{\varepsilon} \cdot I_{min} + 1)} \\ &= \frac{\log(\frac{1}{\varepsilon} \cdot I + 1)}{\log(\frac{1}{\varepsilon} \cdot I_{max} + 1)}, (0 \le \tilde{I} \le 1) \end{aligned}\tag{12}$$

Therefore, Equation (8) is a generalized form of Equations (2) and (5). The parameter $p$ enables us to adaptively obtain a suitable log-normalized transformation for different input images, which represents the order of magnitude of image amplification as shown in Figure 2. Using the parameter $p$ to amplify the input luminance is equivalent to performing the corresponding global compression mapping, which has the properties of enhancing the contrast of low-luminance while compressing the dynamic range of high-luminance for all pixels of the image.

With the increase in the parameter $p$, the range of enhancement area reduced, and the amplitude of enhancement increased. Meanwhile, the suppression effect of the highlighted area is enhanced, and the overall luminance of the image is improved. When $p$ is too large, the dynamic range of the original low-luminance region is also compressed, and the image details will be suppressed, resulting in the lack of contrast. For HDR images where most of the data is located in the low-luminance region and a small part of the data have the characteristics of very high luminance, the selection of parameter $p$ is essentially a trade-off between the detail enhancement region and the dynamic range compression region. From Figure 2, we can select the range of $p$ as $[-5, 10]$. For different input images, the parameter $p$ is selected adaptively according to the image information and the domain of the TM algorithm. Specific selection strategies will be given in the following sections.

![](img/e4200cc4308edaf8913e513b0f96dbb6_366_0.png)

**Figure 2.** Mapping curves with different $p$ values.

**Table 1.** Summary of tone mapping preprocessing research.

| Researcher | Expression | Advantage | Disadvantage |
| :--- | :---: | :---: | :---: |
| Stockham [27] | $\frac{\log(I+1)}{\log(I_{max}+1)}$ | Strictly mapped to the interval $[0, 1]$ | The luminance compression is excessive; The lost of high contrast content |
| Dargo [10] | $\frac{I_{max} \cdot 0.01}{\log_{10}(I_{max}+1)} \frac{\log(I+1)}{\log(2+(\frac{I}{I_{max}})^b \frac{\log(I)}{\log(0.5) \cdot 8})}$ | Well-suited to the specific image content | Parameter $b$ needs to be adjusted for different images; Local contrast reduction |
| Gu [28] | $\frac{\log(10^p+1)}{\log(I_{max} \cdot 10^p+1)}$ | Enhancing low-light areas of the image; Improving the overall brightness of the image | Overexposure may occur |
| Vinker [21] | $\frac{\log(\lambda \cdot \frac{I}{I_{max}}+\epsilon)}{\log(\lambda+\epsilon)}$ | Adaptive searching for appropriate mapping curves | High computational complexity; Not strictly normalized to the interval $[0, 1]$ |

## 3. Domain-Aware Objective Function

Traditional TM algorithms can be classified into luminance-domain and gradient-domain methods broadly. The luminance-domain methods use layer decomposition, histogram [15,30,31], HVS [32–34], etc. to deal with image luminance. These types of methods consider how to compress the HDR image luminance to the display range of traditional display devices. The gradient-domain methods focus on the preservation of image contrast and gradient, directly acting on the image gradient to achieve overall dynamic range compression. Based on their different figure directions, we propose different objective functions in the luminance domain and gradient domain to guide the selection of the parameter $p$, which are called luminance-domain-aware AdaLogT methods and gradient-domain-aware AdaLogT methods, respectively. The overall flowchart of the proposed method is shown in Figure 3.

![](img/e4200cc4308edaf8913e513b0f96dbb6_367_0.png)

### 3.1. Luminance-Domain-Aware AdaLogT Method

The grayscale mean of image pixels reflects the exposure degree of the image [35–37]. Direct observation shows that the distribution of HDR image pixels at each luminance level is uneven [38], as shown in Figure 4a. On the other hand, histogram equalization states that if the pixels of an image can be distributed evenly over all possible gray levels, the image will have high contrast and richer details. In AdaLogT, different parameters p can adjust the luminance distribution of the image without changing the overall shape of the image histogram, thereby adjusting the exposure level of the image. Figure 4 shows the image grayscale histogram under different parameters. With the logarithmic transformation of different p values, the image histogram gradually extends to other luminance levels.

![](img/e4200cc4308edaf8913e513b0f96dbb6_367_1.png)

Image skewness $s(\cdot)$ measures the symmetry of the image distribution concerning the mean value, and the degree of its approximation to 0 reflects the degree of symmetry of the distribution. Therefore, we introduce image skewness to ensure the symmetry of the image distribution after adjustment. Thus, the objective function and corresponding optimization problem for luminance-domain TM algorithms are given as follows:

$p^{*}=\underset{p}{\operatorname{arg} \min } \alpha \cdot\left\|\bar{I}-T\right\|_{F}^{2}+(1-\alpha) \cdot\left|s(\bar{I})\right|,$

$s . t . \bar{I}=\log \left(I \cdot 10^{p}+1\right) / \log \left(I_{\max } \cdot 10^{p}+1\right),$

$s(\bar{I})=\mathbb{E}(\bar{I}-\mu)^{3} / \sigma^{3},$

where $\|\cdot\|_{F}$ indicates Frobenius norm. $s(\bar{I})$ is the skewness of image $\bar{I}, |s(\bar{I})|$ means the absolute value of $s(\bar{I})$, and $\mathbb{E}(\cdot)$ denotes the expectation. $\mu$ and $\sigma$ are respectively the mean and variance of $\bar{I}$. $T$ represents the exposure level of the target image, and $\alpha$ is the weight to balance exposure and skewness. This paper defaults to $T=0.5$ and $\alpha=0.8$.

We can calculate the above optimization problem with the trichotomy method to obtain the optimal parameter $p$, as shown in Algorithm 1. Figure 5 shows the grayscale histograms of some images before and after adaptive logarithmic transformation. By comprehensively considering exposure and skewness, the AdaLogT images have better display luminance and contrast, which is reflected in the histogram, that is, the pixels are distributed to as many grayscale levels as possible.

**Algorithm 1: Trichotomy method for optimum value**
- **input**: Grayscale high dynamic range image $I$, Exposure level $T$, Lower bound $L$, Upper bound $U$, weight $\alpha$.
- **output**: $p^{*}$
1. $f(I):=\alpha \cdot\left\|I-T\right\|_{F}^{2}+(1-\alpha) \cdot|s(I)| ;$
2. $I_{p}:=\log \left(I \cdot 10^{p}+1\right) / \log \left(I_{\max } \cdot 10^{p}+1\right) ;$
3. **while** $L < U$ **do**
   - $I_{mid}:=(L+U) \gg 1, L_{mid}:=(I_{mid}+U) \gg 1 ;$
   - **Compute** $f(I_{mid}), f(L_{mid})$;
   - **if** $f(I_{mid}) <= f(L_{mid})$ **then**
     - $U=I_{mid}$
   - **else**
     - $L=L_{mid}$
4. $p^{*}=I$

![](img/e4200cc4308edaf8913e513b0f96dbb6_368_0.png)

Figure 5.
