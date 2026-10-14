
-   [评估加密水印图像的安全性，NPCR 如在 `Equation (7)`](#ch37.xhtml#math37_7) 所示，其中表示从检索图像中检索图像的原始图像的像素变化率。在 `Equation (8)` 中 `I[0]` 表示原始 X 射线图像，`I[1]` 是检索的 X 射线图像。

(7)  

```math
\\text{NPCR} = \\frac{\\sum\\_{x = 1,y = 1}^{\\text{n},\\text{m}}\\text{D}(\\text{x},\\text{y})}{\\text{n} \\times \\text{m}} \\times 100\\text{\\%}
```  

(8)  

```math
D(x,y) = \\left\\{ \\begin{array}{l} {0,\\, if\\, I\_{0}(x,y) = I\_{1}(x,y)} \\\\ {1,\\, if\\, I\_{0}(x,y)! = I\_{1}(x,y)} \\\\ \\end{array} \\right.
```  

### 通用平均变化强度 (UACI)

UACI 通过 `equation (9)` 表示。

(9)  

```math
UACI = \\frac{\\sum\\_{x = 1,y = 1}^{N,M}\\left| {I\_{0}(x,y) - I\_{1}(x,y)} \\right|}{(N \\times M) \\times 255}
```  

### 熵

熵通过 `Equation (10)` 表示。

(10)  

```math
H(U) = \\sum\\limits\_{i = 0}^{255}p(u\_{i})\\log\_{2}p(u\_{i})
```  

### 比特错误率 (BER)

BER 通过 `Equation (11)` 表示。

(11)  

```math
BER = \\frac{\\sum\_{i}I(i) - SI(i)}{I.}
```  

### 平均绝对百分比误差 (MAPE)

MAPE 在 `Equation (12)` 中表示。

(12)  

```math
MAPE = \\frac{1}{L}\\sum\\limits\_{i = 1}^{L}\\left( \\frac{\\left| I(i) - SI(i) \\right|}{I} \\right) \\times 100\\text{\\%}
```  

### 信号噪声比 (SNR)

SNR 在 `Equation (13)` 中表示。

(13)  

```math
SNR = 10\\log\_{10}\\frac{\\sum\_{i = 1}^{L}\\left( {I(i) - SI(i)} \\right)^{2}}{\\sum\_{i = 1}^{L}\\left( {I(i)} \\right)^{2}}
```  

### 压缩比 (CR)

如在 `Equation (14)` 所示，它是原始图像字节大小除以恢复图像字节大小。

(14)  

```math
CR = \\frac{Sizeof(I)}{Sizeof(SI)}
```  

### Kullback-Leibler divergence (KLD)

KLD 在 `Equation (15)` 中表示。

(15)  

```math
KLD(p\_{or},p\_{tr}) = \\int^{}p\_{or}(x)\\log\\frac{p\_{tr}(x)}{p\_{or}(x)}dx
```  

在 `Table 37.6` 中观察到，少数研究者（`[Krishna, 2018](#ch37.xhtml#ref37_17)`；`[Mothi and Karthikeyan, 2019`](#ch37.xhtml#ref37_23)`；`[Ali et al., 2022`](#ch37.xhtml#ref37_6)`；`[Kore and Patil, 2022`](#ch37.xhtml#ref37_16)`；Zolfaghari and Koshiba, 2022；`[Parmar and Shah, 2023`](#ch37.xhtml#ref37_24)`）没有讨论计算时间，也没有讨论标准统计检验，如 PSNR、MSE、RMSE 等。而文章（`[Al [Hamid et al., 2017`](#ch37.xhtml#ref37_13)`；`[Adnan and Ariffin, 2019`](#ch37.xhtml#ref37_2)`；Cordova, and Halibas, 2020；Adee and Mouratidis, 2022；Maata et al., 2022）也没有进行任何标准统计检验，这证明了他们所提方法的有效性。而本论文所提议的 PHM 方法实现了 74.5584 dB 的 PSNR，MSE 值接近零（0.000000035），这是期望的 MSE 值。相关系数（R）为 0.999999，结果在 MAPE、RMSE、SNR、KLD、压缩比（CR）、BER、NPCR、UACI、PRD 和熵等测试中表现优异。因此，可以得出结论：所提的 PHM 方法能够确保 X 射线图像的保密性和隐私性。

PHM 增强了 EMI 在存储时或在网络传输前的安全性。所提的混合方法高效实现，结合了基于边缘的隐写术与三层加密。X 射线图像首先通过边缘隐写术隐藏，然后应用分层加密，确保保密性、隐私性、降低计算时间和降低计算成本，从而适用于实时应用，并使用 5856 张需要保护的 X 射线图像的总数据量、加密时间、解密时间和总时间来评估所提方法的性能。与已发表的研究相比，所提方法的加密时间为 0.13008 s，解密时间为 0.16772 s，这在数据集大小（1.2 GB）方面优于同行。PHM 实现了 74.55 dB 的 PSNR，MSE 接近零，这也是期望的值。在 SSIM、RMSE、MAPE、BER 等测试中表现更好。因此，可以得出结论：所提的混合方法（PHM）在保护不同尺寸和规模的 EMI 图像大数据集方面是高效且有效的。统计分析表明 PHM 更优，从而增强了 EMI 的保密性和隐私性。未来，可以在覆盖图像中实现机器学习算法以便于检测边缘，并将覆盖图像 Lena 改为任意图像。此外，还可以将其集成到区块链环境中。

*   [`[Adee, Rose, and Haralambos Mouratidis.](#ch37.xhtml#R_ref37_1)` (2022). A dynamic four-step data security model for data in cloud computing based on cryptography and steganography. Sensors, 22(3): 1109. 1–23.]

*   [`[Adnan, N. A. N. and Ariffin, S.](#ch37.xhtml#R_ref37_2)` (2019). Big data security in the web-based cloud storage system using 3d-Aes block cipher cryptography algorithm. Comm. Comp. Inform. Sci., 937, 309–321. [https://doi.org/10.1007/978-981-13-3441-2_24](https://doi.org/10.1007/978-981-13-3441-2_24)]

*   [`[Agarwal, Shweta, and Chander Prabha](#ch37.xhtml#R_ref37_3)` (2022). Analysis of Lung Cancer Prediction at an Early Stage: A Systematic Review. In Congress on Intelligent Systems: Proceedings of CIS 2021. 1, 701–711. Singapore: Springer Nature Singapore.]

*   [`[Ahmad, M. A., Elloumi, M., Samak, A. H., Al-Sharafi, A. M., Alqazzaz, A., Kaid, M. A., and Iliopoulos, C.](#ch37.xhtml#R_ref37_4)` (2022). Hiding patients’ medical reports using an enhanced wavelet steganography algorithm in DICOM images. Alexandria Engg. J., 61(12), 10577–10592. [https://doi.org/10.1016/j.aej.2022.03.056](https://doi.org/10.1016/j.aej.2022.03.056)]

*   [`[Akkasaligar, Prema T., and Sumangala Biradar](#ch37.xhtml#R_ref37_5)` (2020). Selective medical image encryption using DNA cryptography. Information Security Journal: A Global Perspective. 29(2): 91–101.]

*   [`[Ali, Aitizaz, Muhammad Fermi Pasha, Jehad Ali, Ong Huey Fang, Mehedi Masud, Anca Delia Jurcut, and Mohammed A. Alzain](#ch37.xhtml#R_ref37_6)` (2022). Deep learning based homomorphic secure search-able encryption for keyword search in blockchain healthcare system: A novel approach to cryptography. Sensors, 22(2): 528. 1–29.]

*   [`[Avula Gopalakrishna, Chandini, and Prabhugoud I. Basarkod](#ch37.xhtml#R_ref37_7)` (2023). An efficient lightweight encryption model with re-encryption scheme to create robust blockchain architecture for COVID-19 data. Transactions on Emerging Telecommunications Technologies. 34(1): e4653. [https://doi.org/10.1002/ett.4653](https://doi.org/10.1002/ett.4653)]

*   [`[Awadh, W. A., Alasady, A. S., and Hamoud, A. K.](#ch37.xhtml#R_ref37_8)` (2022). Hybrid information security system via combination of compression, cryptography, and image steganography. Int. J. Elec. Comp. Engg., 12(6), 6574–6584. [https://doi.org/10.11591/ijece.v12i6.pp6574-6584](https://doi.org/10.11591/ijece.v12i6.pp6574-6584)]

*   [`[El-Shafai, W., Khallaf, F., El Sayed M. El-Rabaie, and Abd El-Samie, F. E.](#ch37.xhtml#R_ref37_9)` (2022). Proposed neural SAE-based medical image cryptography framework using deep extracted features for smart IoT healthcare applications. Neural Comput. Appl., 34(13), 10629–10653. [https://doi.org/10.1007/s00521-022-06994-z](https://doi.org/10.1007/s00521-022-06994-z)
