
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

在 `Table 37.6` 中观察到，少数研究者（`Krishna, 2018`；`Mothi and Karthikeyan, 2019`；`Ali et al., 2022`；`Kore and Patil, 2022`；Zolfaghari and Koshiba, 2022；`Parmar and Shah, 2023`）没有讨论计算时间，也没有讨论标准统计检验，如 PSNR、MSE、RMSE 等。而文章（`Al [Hamid et al., 2017`；`Adnan and Ariffin, 2019`；Cordova, and Halibas, 2020；Adee and Mouratidis, 2022；Maata et al., 2022）也没有进行任何标准统计检验，这证明了他们所提方法的有效性。而本论文所提议的 PHM 方法实现了 74.5584 dB 的 PSNR，MSE 值接近零（0.000000035），这是期望的 MSE 值。相关系数（R）为 0.999999，结果在 MAPE、RMSE、SNR、KLD、压缩比（CR）、BER、NPCR、UACI、PRD 和熵等测试中表现优异。因此，可以得出结论：所提的 PHM 方法能够确保 X 射线图像的保密性和隐私性。

PHM 增强了 EMI 在存储时或在网络传输前的安全性。所提的混合方法高效实现，结合了基于边缘的隐写术与三层加密。X 射线图像首先通过边缘隐写术隐藏，然后应用分层加密，确保保密性、隐私性、降低计算时间和降低计算成本，从而适用于实时应用，并使用 5856 张需要保护的 X 射线图像的总数据量、加密时间、解密时间和总时间来评估所提方法的性能。与已发表的研究相比，所提方法的加密时间为 0.13008 s，解密时间为 0.16772 s，这在数据集大小（1.2 GB）方面优于同行。PHM 实现了 74.55 dB 的 PSNR，MSE 接近零，这也是期望的值。在 SSIM、RMSE、MAPE、BER 等测试中表现更好。因此，可以得出结论：所提的混合方法（PHM）在保护不同尺寸和规模的 EMI 图像大数据集方面是高效且有效的。统计分析表明 PHM 更优，从而增强了 EMI 的保密性和隐私性。未来，可以在覆盖图像中实现机器学习算法以便于检测边缘，并将覆盖图像 Lena 改为任意图像。此外，还可以将其集成到区块链环境中。

* `[Adee, Rose, and Haralambos Mouratidis.` (2022). A dynamic four-step data security model for data in cloud computing based on cryptography and steganography. Sensors, 22(3): 1109. 1–23.]

* `[Adnan, N. A. N. and Ariffin, S.` (2019). Big data security in the web-based cloud storage system using 3d-Aes block cipher cryptography algorithm. Comm. Comp. Inform. Sci., 937, 309–321. [`doi.org/10.1007/978-981-13-3441-2_24`](https://doi.org/10.1007/978-981-13-3441-2_24)]

* `[Agarwal, Shweta, and Chander Prabha` (2022). Analysis of Lung Cancer Prediction at an Early Stage: A Systematic Review. In Congress on Intelligent Systems: Proceedings of CIS 2021. 1, 701–711. Singapore: Springer Nature Singapore.]

* `[Ahmad, M. A., Elloumi, M., Samak, A. H., Al-Sharafi, A. M., Alqazzaz, A., Kaid, M. A., and Iliopoulos, C.` (2022). Hiding patients’ medical reports using an enhanced wavelet steganography algorithm in DICOM images. Alexandria Engg. J., 61(12), 10577–10592. [`doi.org/10.1016/j.aej.2022.03.056`](https://doi.org/10.1016/j.aej.2022.03.056)]

* `[Akkasaligar, Prema T., and Sumangala Biradar` (2020). Selective medical image encryption using DNA cryptography. Information Security Journal: A Global Perspective. 29(2): 91–101.]

* `[Ali, Aitizaz, Muhammad Fermi Pasha, Jehad Ali, Ong Huey Fang, Mehedi Masud, Anca Delia Jurcut, and Mohammed A. Alzain` (2022). Deep learning based homomorphic secure search-able encryption for keyword search in blockchain healthcare system: A novel approach to cryptography. Sensors, 22(2): 528. 1–29.]

* `[Avula Gopalakrishna, Chandini, and Prabhugoud I. Basarkod` (2023). An efficient lightweight encryption model with re-encryption scheme to create robust blockchain architecture for COVID-19 data. Transactions on Emerging Telecommunications Technologies. 34(1): e4653. [`doi.org/10.1002/ett.4653`](https://doi.org/10.1002/ett.4653)]

* `[Awadh, W. A., Alasady, A. S., and Hamoud, A. K.` (2022). Hybrid information security system via combination of compression, cryptography, and image steganography. Int. J. Elec. Comp. Engg., 12(6), 6574–6584. [`doi.org/10.11591/ijece.v12i6.pp6574-6584`](https://doi.org/10.11591/ijece.v12i6.pp6574-6584)]

* `[El-Shafai, W., Khallaf, F., El Sayed M. El-Rabaie, and Abd El-Samie, F. E.` (2022). Proposed neural SAE-based medical image cryptography framework using deep extracted features for smart IoT healthcare applications. Neural Comput. Appl., 34(13), 10629–10653. [`doi.org/10.1007/s00521-022-06994-z`](https://doi.org/10.1007/s00521-022-06994-z)

* 乔治娃-茨纳瓦, 加利亚, 加林娜·博戈多娃, 以及耶夫根尼亚·古波多诺娃. (2022). 数学方法在利用密码学和隐写技术保护心脏数据准确性的评估。数学, 10(3): 390. 1–18.

* Brar, P. S., Shah, B., Singh, J., Ali, F., and Kwak, D. (2022). 使用修改后的技术接受模型评估基于物联网的室内灾害管理软件工具在救援人员中的采用情况。传感器, 22(5), 1866, [`doi.org/10.3390/s22051866`](https://doi.org/10.3390/s22051866).

* Hachaj, T., Koptyra, K., and Ogiela, M. R. (2021). 基于特征向量的隐写技术。熵, 23(3), 1–24. [`doi.org/10.3390/e23030273`](https://doi.org/10.3390/e23030273).

* Hamid, H. A. A., Mizanur Rahman, Sk Md, Hossain, M. S., Almogren, A., and Alamri, A. (2017). 使用配对密码学在医疗大数据隐私保护的雾计算设施中保存医疗大数据隐私的安全模型。IEEE Access, 5, 22313–22328. [`doi.org/10.1109/ACCESS.2017.2757844`](https://doi.org/10.1109/ACCESS.2017.2757844).

* Website: [Https://Pixlr.Com/](http://www.Pixlr.Com). (n.d.). Accessed March 18, 2022. [`pixlr.com/`](https://pixlr.com).

* Kermany, Daniel, Kang Zhang, and Michael Goldbaum. (2018). 标记光学相干断层扫描 (oct) 和胸片 X 光图像用于分类。Mendeley 数据. 2(2): 651.

* Kore, A. and Patil, S. (2022). 基于层级加密的 IoT 智能医疗系统安全路由。无线网络, 28(1), 287–301. [`doi.org/10.1007/s11276-021-02850-5`](https://doi.org/10.1007/s11276-021-02850-5).

* Krishna, A. V. N. (2018). 基于完全同态加密和立方线曲线公钥加密的大数据安全机制。信息优化科学杂志, 39(6), 1387–1399. [`doi.org/10.1080/02522667.2018.1507762`](https://doi.org/10.1080/02522667.2018.1507762).

* Kumar, M., Soni, A., Shekhawat, A. R. S., and Rawat, A. (2022). 使用 LSB 隐写和 AES 加密技术的混合模型增强数字图像和文本数据安全。第二届人工智能智能能源会议论文集, 1453–1457. [`doi.org/10.1109/ICAIS53314.2022.9742942`](https://doi.org/10.1109/ICAIS53314.2022.9742942).

* Li, C., Dong, M., Li, J., Xu, G., Chen, X. B., Liu, W., and Ota, K. (2022). 使用关键词可搜索加密在健康链中的高效医疗大数据管理。IEEE 系统杂志, 16(4), 5521–5532. [`doi.org/10.1109/JSYST.2022.3173538`](https://doi.org/10.1109/JSYST.2022.3173538).

* Lin, C. H., Wen, C. H., Lai, H. Y., Huang, P. T., Chen, P. Y., Li, C. M., and Pai, N. S. (2023). 基于多层卷积处理网络的数字图像信息安全加密机制。过程, 11(5). [`doi.org/10.3390/pr11051476`](https://doi.org/10.3390/pr11051476).

* Maata, R. L. R., Cordova, R. S., and Halibas, A. (2020). 大数据中 Twofish 加密算法性能分析。ACM 国际会议论文集, 56–60. [`doi.org/10.1145/3436829.3436838`](https://doi.org/10.1145/3436829.3436838).

* Singh, J., Goyal, G., and Gill, R. (2020). 使用神经度量选择全通道业务最佳广告方法。企业信息系统, 14(2), 243–265, [`doi.org/10.1080/17517575.2019.16`](https://doi.org/10.1080/17517575.2019.16) 40392.

* Mothi, R. and Karthikeyan, M. (2019). 使用水印和 WPT 的生物医学虹膜图像保护技术。测量, 136, 67–73. [`doi.org/10.1016/j.measurement.2018.12.030`](https://doi.org/10.1016/j.measurement.2018.12.030).

* Parmar, M. and Shah, P. (2023). 物联网-区块链轻量加密用于智能应用的数据安全和完整性。国际电子计算机工程杂志, 13(4), 4422–4431. [`doi.org/10.11591/ijece.v13i4.pp4422-4431`](https://doi.org/10.11591/ijece.v13i4.pp4422-4431).

* Prabha, C., Singh, J., Agarwal, S., Verma, A., and Sharma, N. (2022). 计算智能在医疗保健中的介绍。计算智能医疗, 1–15. [`doi.org/10.1201/9781003305347-1`](https://doi.org/10.1201/9781003305347-1).

* Sharma, D. and Kawatra, R. (2023). 使用隐写和密码技术在大数据上实现安全技术。笔记本系统, 517, 279–302. [`doi.org/10.1007/978-981-19-5224-1_30`](https://doi.org/10.1007/978-981-19-5224-1_30).
