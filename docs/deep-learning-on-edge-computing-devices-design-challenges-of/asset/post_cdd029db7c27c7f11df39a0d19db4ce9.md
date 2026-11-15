
reduced the code rate of the fixed-point representation from the initial quantization length of $D$ bits to the effective code rate $d$, which was the number of nonzero coefficients in vector $\boldsymbol{\alpha}^{(\mathit{l})}$ (Eq. (4.6)). Fig. 4.4 visualized the loss of activation integrity caused by 5-bit activation quantization over the MNIST dataset. The absolute values of the difference between the compressed image data and the original image data were compared between the proposed method and the baseline quantization methods. In summary, the proposed Bitwise Bottleneck method showed the highest PSNR ($47.30 \pm 0.51$ dB) for activation quantization compared with the standard rounding-based method ($42.02 \pm 0.54$ dB) and sensitivity-based method ($34.94 \pm 0.84$ dB) [33].

Fig. 4.5(a) shows the relation between the effective code rate $d$ and the average PSNR achieved over the MNIST dataset. Overall, the proposed Bitwise Bottleneck approach achieved 1.98 dB to 12.44 dB higher PSNR compared with the classic rounding-based quantization and sensitivity-based quantization methods. The superiority of PSNR was consistent when different numbers of nonzero coefficients were chosen, which can be controlled by the hyperparameter of $\lambda$, as shown in the figure.

Similarly to other activation quantization approaches, a backpropagation retraining process was applied after the activation quantization process to refine the weight parameters and the coefficients $\boldsymbol{\alpha}^{(\mathit{l})}$ that were quantized to $D$ bits with a rounding-based approach. Fig. 4.5(b) shows the final classification accuracy achieved with backpropagation. The average accuracy over both the MNIST and CIFAR10 datasets was evaluated with various numbers of nonzero coefficients $d$. Experimental results showed that the proposed method outperformed the baseline approach when fewer than four bits were used for activation quantization. The loss of accuracy caused by the rounding-based quantization became worse when the dataset was more complicated, whereas the Bitwise Bottleneck approach suffered almost no loss of accuracy compared with the floating-point model when more than three bits were used for activation representation.

The Bitwise Bottleneck approach featured its ability to automatically determine the effective code rates of different layers. By setting the threshold of PSNR loss accepted for activation quantization, the bitwise bottlenecks can estimate the minimal effective code rate by the sparse optimization. Fig. 4.5(c) shows the relation among the threshold of PSNR loss, the average effective code rate across different layers, and the classification accuracy. As shown in experiments over the CIFAR10 dataset, the classification accuracy decreased when the threshold of PSNR loss increased. However,

![](img/5fa4874adaccc5ede04575a2e9e5662a_80_0.png)

![](img/5fa4874adaccc5ede04575a2e9e5662a_80_1.png)

![](img/5fa4874adaccc5ede04575a2e9e5662a_80_2.png)

![](img/5fa4874adaccc5ede04575a2e9e5662a_80_3.png)

Figure 4.5 (a) The relation between the PSNR and the effective code rate, which equals the number of nonzero coefficients in \(\alpha^{(l)}\), and the relation between the effective code rate and the value of \(\lambda\). (b) Accuracy of the deep neural network with bitwise bottlenecks over the MNIST (upper) and CIFAR10 (lower) datasets, which can compress the activation of the deep neural network with different effective code rates d. (c) The change in accuracy and average effective code rate of different layers when using the bitwise bottlenecks to compress the 8-bit fixed-point activation according to different PSNR loss thresholds. (d) The ratio of \(\alpha_f^{(l)}/2^{l-1}\) with different thresholds of PSNR loss (T = 26 upper, T = 30 lower).

when the PSNR loss was less than 24 dB, almost no decrease in classification accuracy was detected (less than 1%). The accuracy began to decrease when fewer than 6 bits on average were used for activation representation.

The Bitwise Bottlenecks approach handled the task of activation quantization as a trade-off between compression and prediction. Fig. 4.5(d) shows the ratio of \(\alpha_j^{(0)}/2^{j-1}\) for each bit of the quantized activation, where \(2^{j-1}\) is the natural coefficient of Eq. (4.3), which reflects how much information the \(j\)th bit contains. Two interesting observations can be found in the image. First, the low-end bits of the activation representation were removed by the bottlenecks, leading to minimal loss of information caused by bitwise compression. Second, despite containing more information, the high-end bits were also removed by the bottlenecks, which was caused by the bitwise sparsity in high-end bits (as shown in Fig. 4.2).

## 4.4.3 Comparison with the state-of-the-art approaches

The proposed method was evaluated with the state-of-the-art activation quantization approaches over the ImageNet dataset. The original floating-point model and the proposed Bitwise Bottleneck approach were compared with the DSQ [34], ACIQ [20], Focused Compression [35], Integer-only [22], UNIQ [36], INQ [37], DoReFa-Net [8], and Iterative Rounding [31] approaches. Thresholds of PSNR loss of 8 dB and 16 dB were adopted to quantize the activations, which resulted in an average effective code rate of 5.0 (±1) and 4.0 (±1) bits. The quantization method of DoReFa-Net [8] was adopted for initial quantization. The standard TensorFlow quantization tool was used to quantize the weights to 8 bits, and all the coefficients of \(\alpha^{(l)}\) were quantized to 6 bits.

We found in our experiments that most quantization methods could achieve almost the same accuracy as the floating-point model with 6- to 8-bits activation representation, but at 5-bit and below the accuracy began to drop obviously. Table 4.1 summarizes the results of classification accuracy over the ImageNet dataset. As shown in the table, the top-1 accuracy loss of 5-bit activation representation was up to 3.5%, and top-1 accuracy loss of 4-bit activation representation was between 1.8% and 5.6%. However, the Bitwise Bottleneck method could achieve marginal loss of accuracy at 5-bit and 4-bit. The loss of accuracy at 4-bit was 0.8%, which was 4.7% higher than that of the initial quantization method (DoReFa-Net). Moreover, the Bitwise Bottleneck method exceeded the Integer-only method with 8-bit activation and the INQ and Focused Compression methods with 32-bit floating-point activation.

| Method | Year | Weights | Activations | Top-1 Acc (%) | Top-5 Acc (%) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Floating-point Model | 2016 | 32 | 32 | 75.6 | 92.8 |
| **Bitwise Bottleneck** | – | 8 | 5 | **75.7** | **92.7** |
| DSQ | 2019 | 8 | 5 | 75.2 | 92.5 |
| Focused Compression | 2019 | 5 | 32 | 74.9 | 92.6 |
| Integer-only | 2018 | 8 | 8 | 74.9 | – |
| INQ | 2017 | 5 | 32 | 74.8 | 92.5 |
| DoReFa-Net (initial quantization) | 2016 | 8 | 5 | 73.8 | 91.7 |
| Iterative Rounding | 2014 | 8 | 5 | 72.1 | 90.4 |
| **Bitwise Bottleneck** | – | 8 | 4 | **74.8** | **92.2** |
| DSQ | 2019 | 8 | 4 | 73.8 | 91.7 |
| UNIQ | 2018 | 4 | 8 | 73.4 | – |
| ACIQ | 2019 | 8 | 4 | 71.8 | – |
| DoReFa-Net (initial quantization) | 2016 | 8 | 4 | 70.1 | 89.3 |
| Iterative Rounding | 2014 | 8 | 4 | 70.0 | 89.4 |

## 4.4.4 Efficiency improvement

From the perspective of reducing computational complexity, when the neural network was implemented in a bitwise way, a lower code rate led to linearly fewer bitwise operations. Taking the 8-bit fixed-point representation as an example, each fixed-point operation could be implemented by 8 bitwise operations, and if we cut off 1 bit, then the number of operations could be reduced by 12.5%. In addition, by reducing a single bit the hardware source requirement was also reduced by 12.5% when it was implemented using dedicated hardware. Generally, compared with the 32-bit activations representation, the bitwise bottlenecks could improve the computational efficiency by more than 6.4 times without hurting the performance of the deep neural network. Besides, considering the weights were quantized to 8-bit, the computational efficiency improvement could reach 25.6 times.

From the perspective of reducing memory occupation, reducing the activation code rate linearly reduced the memory requirement. The activation of a standard neural network was usually represented by 32-bit floating-point, which occupied 4 bytes of memory. However, the bitwise bottlenecks could compress them to fewer than 5 bits without hurting the
