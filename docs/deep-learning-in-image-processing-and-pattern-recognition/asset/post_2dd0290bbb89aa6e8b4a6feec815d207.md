
![](img/e4200cc4308edaf8913e513b0f96dbb6_595_0.png)

![](img/e4200cc4308edaf8913e513b0f96dbb6_595_1.png)

![](img/e4200cc4308edaf8913e513b0f96dbb6_595_2.png)

Comparison of skeleton line extraction methods under thermal deformation of ceramic plates [35]. (a–e) Extracted skeleton lines using the measured fringe pattern and ideal skeleton line. (a-1–a-6) Input test images. (b-1–b-6) Ideal skeletons corresponding to the test images. (c-1–c-6) VID-GVF extraction method. (d-1–d-6) U-net extraction method. (e-1–e-6) M-Net extraction method. Red boxes represent damaged fringes.

**Table 2.** Comparison of the performance of five methods for extracting skeleton lines [32–36].

| Methods | Acc | Sensitivity | Specificity | F1 | CC | Running Time(s) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| D-GVF [32] | / | / | / | / | 0.9775 | / |
| U-net [33] | 0.9133 | 0.6884 | 0.8621 | 0.6254 | 0.9408 | 0.5 |
| CTrans U-net [34] | 0.9878 | 0.8890 | 0.9887 | 0.8881 | 0.9905 | / |
| M-Net [35] | 0.9571 | 0.7412 | 0.9411 | 0.9521 | 0.9521 | / |
| Pix2pix cGAN [36] | 0.9704 | / | / | 0.8174 | 0.8633 | 11.7 |

Note: The above data are the experimental results under their respective data sets. The calculation formula for evaluation indicators is as follows:

- **True Positive (*TP*):** the number of samples that are actually positive and correctly predicted as positive.
- **True Negative (*TN*):** the number of samples that are actually negative and correctly predicted as negative.
- **False Positive (*FP*):** the number of samples that are actually negative but incorrectly predicted as positive.
- **False Negative (*FN*):** the number of samples that are actually positive but incorrectly predicted as negative.

Existing deep learning methods have fewer applications in fringe skeleton line extraction, partly because the physical model for filtering denoising is more explicit, and more mature CNN models have been devised in other image processing fields, which can be directly imported into ESPI denoising. Most deep learning-based fringe skeleton line extraction methods add structural components in the encoder and decoder paths to adapt to ESPI fringe processing. Compared with the following methods, the previous method still requires specific algorithms for skeleton line extraction after filtering denoising, which increases the difficulty of fringe skeleton line extraction. Therefore, directly extracting fringe skeleton lines from the original fringe image without preprocessing could be the focus of research in the future.

## 3.3. Application of Deep Learning in the Interpolation Algorithm

The extracted fringe skeleton lines are discrete sampling points. To obtain the phase information of the entire field, an interpolation algorithm is required to predict the unsampled phase distribution of the entire field. Classic interpolation algorithms include bilinear interpolation [38], nearest neighbor interpolation [39], C spline interpolation [40], and interpolation methods based on the heat conduction theory [31]. Although these methods are simple and fast, they exhibit the following problems:

- (1) The interpolation result is not sufficiently accurate, and the resulting phase is not sufficiently smooth.
- (2) The quality requirements for the skeleton line are high.
- (3) Interpolation speed is slow.

Currently, the phase extraction interpolation algorithm for ESPI fringe patterns still relies on neural networks or simple machine learning methods, as the previous method displays in image format, whereas the subsequent one is related to mathematical methods. In 2007, Tang et al. at Tianjin University first proposed using a BP neural network for fringe skeleton line interpolation [41]. Figure 9 displays the results, which reveal that the phase information obtained by the network is smoother. However, this method requires specialized partial differential equation methods for preprocessing and lacks specific evaluation metrics to quantify the interpolation results. Determining the true phase accuracy obtained from the interpolated image alone is impossible.

![](img/e4200cc4308edaf8913e513b0f96dbb6_597_0.png)

Figure 9. Interpolation results of different methods [41] (a-c) white striped skeleton line, C spline interpolation method's result, and BPFN method's result).

In 2011, Wang et al. from North China University of Technology proposed the radial basis function (RBF) neural network interpolation method, which solves the problem of high-quality requirements for skeleton lines and can obtain excellent results even for severely fractured skeleton lines [42]. However, similar to [41], specific quantitative metrics for evaluating the phase information obtained after interpolation were not provided. In addition, this method did not fully leverage the experimental data information from ESPI fringe patterns.

In 2020, Chen from Tianjin University proposed using hierarchical recurrent neural networks for interpolation processing, which solved the problem of slow processing speed [19]. In the thermal deformation experiment of steel plates under high-intensity laser irradiation, this method could perform interpolation operations on the fringe patterns obtained from dynamic measurements in only 4 s, which considerably lowered the 25 s required in the conventional method. Compared with the BP neural network method, the processing time of both methods was identical, but the phase information of the previous method was smoother. Figure 10 displays the specific interpolation results.

![](img/e4200cc4308edaf8913e513b0f96dbb6_597_1.png)

Figure 10. Three-dimensional phase maps and two-dimensional pseudo-color phase maps interpolated using three different methods [19]. (a) Dynamic measurement fringe pattern of steel plate hot deformation. (b-d) Three-dimensional phase pattern and two-dimensional pseudo-color phase pattern from C-spline interpolation, a BP neural network, and reference [19], respectively.

Currently, interpolation algorithms have not been improved considerably, and the existing literature lacks quantitative evaluation metrics for phase information after interpolation. In this paper, because the evaluation of phase information only based on the smoothness of the image was inadequate, other evaluation metrics were required for quantification. For example, comparing the phase information after interpolation of classic methods with that based on neural network interpolation, calculating SSIM or RMSE between the two can make the performance comparison between methods more specific.

# 4. Application of Deep Learning in Phase Extraction of the ESPI-Wrapped Phase Image

Figure 11 displays the phase extraction method based on wrapped phase maps. The wrapped phase map is obtained using phase shifting, is then filtered and denoised, and finally unwrapped to obtain the final full-field phase information. The following sections describe the application of deep learning in the phase extraction of ESPI-wrapped phase maps.

![](img/e4200cc4308edaf8913e513b0f96dbb6_598_0.png)

**Figure 11.** Schematic of the phase extraction method based on the wrapped phase map [19].

## 4.1. Application of Deep Learning in the Phase Shift Method

According to the different methods of changing the phase difference, the classical phase shift method can be divided into the time phase shift and spatial phase shift method. The time phase shift method changes the phase shift amount on the time series to measure the deformation of the object and obtain deformation information. The spatial phase shift method obtains phase information by applying various phase shifts at one time. According to the different phase shift amounts, the three-step phase shift method [43], four-step phase shift method [44], five-step phase shift method [45], and so on have emerged successively. Their main difference is in the number of interferometric images used and the measurement accuracy. This article is focused on the most commonly used four-step phase shift algorithm. The four-step phase shift method collects two speckle patterns before and after object deformation, with a phase shift of 90◦ for each time in the speckle pattern collection. The intensity distribution of the four speckle interference patterns collected by the CCD can be expressed as follows:

$$
\begin{array}{l} 
I _ { 1 } ( x , y ) = A ( x , y ) + B ( x , y ) \cos [ \varphi ( x , y ) ] \\ 
I _ { 2 } ( x , y ) = A ( x , y ) + B ( x , y ) \cos [ \varphi ( x , y ) + \pi / 2 ] \\ 
I _ { 3 } ( x , y ) = A ( x , y ) + B ( x , y ) \cos [ \varphi ( x , y ) + \pi ] \\ 
I _ { 4 } ( x , y ) = A ( x , y ) + B ( x , y ) \cos [ \varphi ( x , y ) + 3 \pi / 2 ] 
\end{array}\tag{16}
$$

Solving the above equations simultaneously, we can obtain the following phase of the optical field:

$$
\varphi ( x ) = \arctan \frac { I _ { 4 } ( X , Y ) - I _ { 2 } ( X , Y ) } { I _ { 1 } ( X , Y ) - I _ { 3 } ( X , Y ) }\tag{17}
$$

Improved four-step phase shift methods such as 4 + 2 [46] and 4 + 1 time phase shift techniques [47] have since emerged.

From a mathematical perspective, the classical phase shifting method involves adding a known phase shift under various conditions to increase the number of equations, rendering the number of equations greater than or equal to the unknowns, and subsequently solving for the phase value. When using conventional phase shifting methods for phase extraction, selecting an appropriate method based on the differences in processing objects and acquisition speed is necessary. In practice, the following problems are observed:

1. Conventional phase shifting requires the use of multiple images for phase extraction, whereas phase extraction based on a single fringe pattern exhibits lower accuracy. Balancing the two to achieve higher phase accuracy using fewer images remains challenging.
2. The process of time phase shifting requires the acquisition of multiple images, which requires considerable time and limits dynamic measurement.

In 2019, at the Nanjing University of Science and Technology, Feng et al. first demonstrated that deep neural networks can be trained to perform fringe analysis [48]. This study proposed a two-stage convolutional neural network. In the first network, the background intensity information in the fringe pattern was removed, and the output of the second network was the numerator and denominator of the arctangent function, as shown in Equation (17). Finally, the phase was calculated based on the output of network using the arctangent function. In this method, the phase was extracted using a single fringe pattern, and conventional phase shifting methods were combined to solve problem (1). The average absolute error of phase extraction using this method, Fourier transform (FT), and WFT was 0.087, 0.20, and 0.19 rad, respectively. Thus, the phase extraction accuracy improved considerably. However, this method requires the calculation of numerous accurate intermediate data from experimental data before training.

To solve problem (2), Zhang et al., at Shenzhen University, proposed a training strategy for phase shifting networks (PSNs) in 2021 [49]. The input of the method is a single frame of built-in interferogram, whereas the output comprises multiple phase shifting interferograms. This simulates the process of acquiring multiple images in conventional phase shifting. The speed of this method is only 65 ms, which is faster than the 160 ms of classic four-step phase shifting and slightly lower than the 30 ms of the single-frame interferogram phase extraction method. However, in terms of phase extraction RMSE, this method is only 0.11 rad, which is considerably lower than the 0.51 rad of the single-frame interferogram phase extraction method and close to the 0.09 rad of the classic four-step phase shifting. Figure 12 displays the specific method of reference [49].
