
| 表 4.6 DWT 水印 | 参考文献论文 | HDL 编译器 | 硬件平台 | 时钟频率 | 功耗 | 最大 PSNR (dB) | 主图像类型 | 可见/不可见 | 鲁棒/脆弱 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Mulani and Mate (2017) | Verilog | FPGA Xilinx Design Suite 13.1 和 xc66csc-2F84 | 228.064 MHz | N/A | N/A | 灰度图像 | 不可见 | 鲁棒 |
| Lad et al. (2011) | MATLAB 和 VHDL | FPGA Xilinx Chip-Scope Pro 和 Virtex-II | 29.107 MHz | 3.75 mW | 44.408 | 灰度图像 | 未 | 鲁棒 |
| Mathai et al. (2003) | 未 | 0.18um CMOS 技术芯片 | 75 MHz | 160 mW | 40 | 灰度图像 | 不可见 | 鲁棒 |
| Hsiao et al. (2001) | 未 | ASIC 定制 IC | 未报告 | N/A | N/A | 灰度图像 | 不可见 | 鲁棒 |

| 表 4.7 高级水印技术 | 参考文献论文 | HDL 编译器 | 硬件平台 | 硬件板卡 | 频率 | 功耗 | 最大 PSNR (DB) | 主图像类型 | 可见/不可见 | 鲁棒/脆弱/未报告 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Nayak et al. (2017) | VHDL | FPGA Xilinx ISE 14.3, 仿真工具, Kyntex 7 套件 (7K325bfg6-3) 和 Spartan 6 | 351.457 MHz | 5.029mW | 45.23 | 灰度图像 | 不可见 | 鲁棒 |
| Maity and Kundu (2013) | VHDL | FPGA Xilinx Spartan, (65x145tgg484-3) XCS05 | 80 MHz | N/A | 41.02 | 灰度图像 | 不可见 | 未报告 |

| 表 4.8 硬件水印 |
| 参考文献 | HDDL/ 编译器 | 硬件板 | 硬件平台 | 时钟频率 | 功耗 | 最大 PSNR (DB) | 宿主类型 | 可见性 | 鲁棒性 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Harinati 等 (2017) | C/C++ 和 GNU | Xilinx Platform Studio | FPGA | 80.749 MHz | N/A | N/A | 彩色图像 | 不可见 | 脆弱 |
| Venugopala 等 (2017) | Android | Android 智能手机 | Android | N/A | 666 mW | N/A | 彩色视频 | 不可见 | 脆弱 |
| Joshi 等 (2012) | VHDL | Xilinx project navigator | FPGA | N/A | 69 mW | N/A | 彩色图像和色彩 | 不可见 | 鲁棒 |
| Karmani 等 (2009) | VHDL | ISE 9.1 和 STANPART | FPGA | 100 MHz | N/A | N/A | 31 到 32 | 灰度图像 | 不可见 | 脆弱 |
| Matty 等 (2009) | VHDL | Xilinx Spartan, XCS45 | FPGA | 80 MHz | 0.3 mW | 无 | 灰度 | 可见 | 鲁棒 |
| Sec 和 Kim (2007) | VHDL | Xilinx Spartan, XCS40 | FPGA | 80 MHz | N/A | N/A | 灰度图像 | 不可见 | 无 |
| Altera kit (2003) | VHDL | APEX200KC | FPGA | 82 MHz | N/A | 32.3 | 灰度图像 | 不可见 | 鲁棒 |
| Phillips 等 (2000) | C.code | TriMedia TM-1000 | DSP | 100 MHz | N/A | N/A | 图像和视频 | 不可见 | 鲁棒 |
| Cassatto 等 (2000) | MATLAB | 半导体处理器 | DSP | N/A | N/A | 21 | 音频 | 无 | 报告 |

## 126 数字图像水印

所有权。在变换域水印中，宿主图像的变换系数通过水印进行修改。该技术的硬件级实现比空域技术更复杂，因为它需要额外的硬件模块和资源来实现正向和反向变换；而这种实现最适合并行、流水线架构。还有一些方法是将变换/反向/提取操作在 MATLAB 中完成，而算法的其他步骤由 FPGA 硬件完成。目前还有许多用于安全相机的数字图像水印原型，其主要组件包括图像传感器、模数转换器（A/D）、水印单元、临时内存、闪存、控制器单元和液晶显示器（LCD）面板。

## 4.4 挑战与未来方向

基于硬件的实现仅针对少数加性水印技术开发，例如 LSB 替换、SS 技术以及使用 FPGA 板或或 DSP 套件的 DCT/DWT 基于的技术。许多基于通道编码算法、相位一致性、奇异值分解、曲线波变换、轮廓波变换、脊线波变换、混合组合、机器学习和生物启发算法的先进软件水印技术尚无硬件级实现。因此，这些类型的先进水印技术需要新的硬件实现方法。还需要开发高效的硬件水印架构，这些架构能够在更高频率下运行，涉及更少的资源和计算，同时保持良好的不可感知性和针对不同类型攻击的鲁棒性。使用 XSG 设计数字图像水印原型需要对时间、面积和成本进行降低，以及资源利用和延迟的优化，所有这些都要便于设备的集成和配置。

## 127 硬件实现

某些基于硬件的水印实现是软硬协同设计的以节省功耗和时间。某些高性能操作在硬件中设计，而计算密集型操作则在软件中实现。这些设计在硬件和软件实现之间取得了平衡，未来可以进一步改进。

## 参考文献

Ali, Mohammad I., Khaldoon M. Mahaid, and Inad A. Aljarrah. “在 FPGA 硬件上实现图像处理”。在 IEEE 应用电气工程与技术会议 (AECT’13)，1–5。

Cassuto, Yuval, Michael Lustig, and Shay Mizrachny. “使用感知掩蔽的音频实时数字水印系统”。在 TI (德州仪器) DSP 和模拟挑战赛，达拉斯。

De Strycker, Pascale Termont, Jan Vandewege, J. Haitsma, A. A. C. Muller, Marc Maas, and Geert Deoper. “在 TriMedia VLIW 处理器上实现实时数字水印过程”。IEEE 视觉、图像与信号处理 147(4): 371–376。

Do Vinh, and Insoo Ko. “基于 LSB 的隐写”。信息与通信工程期刊 15(3): 151–159。

Garimella, Annajirao, M. W. Satyanarayana, P. S. Murugesh, and U. C. Niranjan. “用于彩色图像水印的 ASIC”。在第 3 次信号处理工作坊，2004 IEEE 第 11 次信号处理工作坊，292–296。

Garimella, Annajirao, M. C. Niranjan, R. Satish Kumar, P. S. Murugesh, and U. Niranjan. “用于 8 位灰度图像的差编码在线数字水印技术的 VLSI 实现”。在第 16 次国际 VLSI 设计会议论文集中，283–288。

Ghosh, Sudip, Nakicheita Das, Subhaj Das, Santi P. Maity, and Hafiz Rahaman. “使用差分扩展插值的可逆水印的 FPGA 和 SoC VLSI 架构”。在印度会议 (INDICON)，2014 年 IEEE，1–6。

（注：页码 141-142 的 OCR 文本包含重复/乱码条目。我已根据提供的结构清理了唯一参考文献列表。）

## 130 ■ 数字图像水印

Mohanty, Sarajevo, P., 和 Sridhara Nayak. “基于 FPGA 的不可形鲁棒图像水印编码器实现。”《智能信息技术》，第 344–353 页。Springer, 柏林, 海德堡, 2004.

Mohanty, Sarajevo, P., Elias Kougianos, 和 Nagarajan Ranganathan. “用于结合不可形鲁棒与脆弱水印的 VLSI 架构与芯片。”IET Computers & Digital Techniques (5): 600–617, 2007.

Mohanty, Sarajevo, P., N. Ranganathan, 和 Ravi K. Namballa. “面向开发安全 JPEG 编码器的不可形数字水印算法的 VLSI 实现。”IEEE 信号处理系统研讨会，2003。SIPS 2003，第 183–188 页。IEEE, 2003.

Mohanty, Sarajevo, P., Nagarajan Ranganathan, 和 Ravi K. Namballa. “用于安全静态数码相机 (S/sup²/DC) 设计的可见水印 VLSI 架构（修正版）。”IEEE 超大规模集成 (VLSI) 系统汇 13(8): 1002–1012, 2005.

Morita, Y. E. Ayeh, O. B. Adamo, 和 P. Guturu. “基于 DCT 的水印算法的软硬件协同设计方法。”第 52 次国际西部电路与系统研讨会，2009。MWSCAS’09，第 683–686 页。IEEE, 2009.

Mulani, Altaf O., 和 P. B. Mane. “可重构平台上的水印与加密图像的身份认证。”电气工程与信息学报 6(2): 181–187, 2017.

Nayak, Manasanjan, Joyashree Bag, Subir Sarkar, 和 Subir Kumar Sarkar. “基于相位相干与奇异值分解技术的新型水印硬件实现。”AEU-国际电子与通信国际期刊 71(1): 1–8, 2017.

Nelson, Graham R., Graham A. Jullien, 和 Orly Yadid-Pecht. “具有水印能力的 CMOS 图像传感器。”IEEE 国际电路与系统研讨会，2005。ISCAS 2005，第 5326–5329 页。IEEE, 2005.

Pemmaraju, Manasa, Sai Chandashetty, Srinivas Aruva, Mohansankar Sadvalley, 和 Bharat Babu Edara. “基于 FPGA 的小波域图像融合实现。”国际电子与信息趋势国际会议 (ICEI’17)，第 500–504 页。IEEE, 2017.

Petitjean, Guillaume, Jean-Luc Dupelay, Sophie Gabrielle, Christian Rey, 和 Jean Nicolai. “面向片上系统的实时视频水印。”IEEE 国际多媒体会议与博览 (ICME’02)，第 1 卷，第 597–600 页。IEEE, 2002.

## 硬件实现 ■ 131

Power, Prachi V., 和 S. S. Agrawal. “使用 MATLAB Simulink 的数字视频水印方案设计。”工程与技术国际期刊 2(5): 826–830, 2013.

Que, Zhiqiang, Yongxin Xu, Xuan Wang, Jibo Yu, Tian Huang, Zhe Zheng, Li Yang, Feng Zhao, 和 Yuzhu Fu “使用 SysGen 和 simulink 的高效工作流在独立 FPGA 系统上实现 CT 算法。”IEEE 第10 次国际计算机与信息技术会议 (CIT'10)，第 2391–2396 页。IEEE, 2010.

Rahimnussa, K., P. Karthigaikumar, Soumiya Rasheed, J. Jayakumar, 和 S. Suresh Kumar. “高吞吐量折叠并行架构算法 的 FPGA 实现。”安全与通信网络 7(1): 2225–2236, 2014.

Rajagopalan, Sudararaman, Palakalati J. S Prabhaker, Sudheer Kumar, N. V. M. Nikhil, Har Narayan Upadhyay, J. B. Rayappan, 和 Rangarajan Amitharaj. “FPGA 平台上基于 MSB 的集成：自适应 RGB 阶段嵌入。”信息技术杂志 13: 1945–1952, 2014.

Roy, Jonny Deb, Xin Li, Yonatan Shosh, Alexander Fish, 和 Orly Yadav-Pech. “数字水印认证的硬件实现。”IEEE 视频技术电路与系统汇 23(2): 289–301, 2013.

Samanta, D. A. Basu, T. S. Das, V. H. Mankar, 和 Manish Das. “空域鲁棒水印的硬件实现。”电气工程国际会议 (ICE)，第 986–993 页。

Seo, Young-Ho, 和 Dong-Gook. “用于 JPEG 编码的盲水印硬件实现。”水印研讨会，第 88–93 页。

Shah, D. A. “图像的身份认证。”诺诺伊利斯州大学，德尔巴。

Shet, K. Sathish, A. Aswath, 和 Hanuman. “数字水印的可重构架构设计。”多媒体工具与应用 76(11): 13197–13219.

Shih, Frank Y. “水印与隐写术。”CRC Press, 博卡拉顿。

Tsai, S. E., 和 M. Yang. “用于数字处理器的快速 DCT 水印。”数学问题 2017.

## 132 ■ 数字水印

Tsai, T. H., 和 C. Y. Lu. “用于嵌入系统的系统级设计。”IEEE 智能信号处理与通信研讨会，第 20–23 页，2001.

Tsai, Tsung-Han, 和 Chih-Yen Wu. “视频编码器数字水印系统实现。”IEEE 消费者电子会议 (ICCE’03)，第 216–217 页。IEEE, 2003.

Venugopala, P., H. Sarojdevi, 和 Niranjan. “使用移动设备嵌入水印。”可持续计算：信息与系统 15: 82–87, 2017.

Zavaleta, Z., Claudia Feregrino, 和 René Cumplido. “用于放射医学图像的可逆隐藏算法。”可重构计算与 FPGA 国际会议，第 444–449 页。IEEE, 2008.

## 应用实例与未来展望

水印大多是可见的，发现于货币、邮票、护照、纸币等。在发明的早期，数字水印仅限于证明所有权。后来，随着互联网的快速发展，数字水印被广泛应用于，如电子广告、电子交付、电子治理、电子教育、电子投票、军事、秘密通信、医疗、网络出版、数字取证、数字图书馆、机器人、硬件/芯片保护、设备控制、增强、媒体文件存档。数字水印保护信息并能够检测非法使用。鲁棒不可形水印是所有者故意隐藏在主机图像中的不可感知信息，以便在后期用于各种用途，如版权保护、认证、所有证明、复制和使用控制、指纹、篡改检测/证据、交易跟踪和广播监控（Suresha and Swamy, 2012; Suresh et al., 2012, 2016）。

## 134 ■ 数字水印

水印系统的需求取决于应用类型。本章讨论了医疗、遥感、军事和工业领域的各种应用及可能的需求。

## 5.1 水印的应用

DRM 系统建议在具有不同鲁棒性和其他要求的应用中使用水印。本节讨论了数字水印的一些应用。

- 所有者识别：通过在发布在 Web 上的图像嵌入水印来实现所有权证明，这可能传递有关作者或来源的信息，以传递所有权并解决所有权。该应用要求水印具有鲁棒性、无歧性，并对抗添加额外水印。
- 复制保护：通过应用“不复制/复制一次”水印防止非法复制/下载。例如：DVD 系统。
- 指纹/复制或使用控制：在开放和分布式系统中，复制保护极其困难。授权用户在开放网络上对许可协议的非法违反/复制/使用/分发可以通过可以防止或识别为每张图像副本分配唯一的标识符进行指纹识别。指纹识别的主要要求是对共谋攻击的鲁棒性。例如：Divx 系统、从盗版副本中进行影院识别。
- 数据身份验证与完整性/篡改检测：数据篡改非常容易，特别是在数字取证应用中应当被检测出来。签名/头部/元数据无法指示对图像所做的更改。脆弱性水印（即当数据被修改时水印会消失）的鲁棒性极低，更适用于识别数据是否保持完整。在处理涉及医疗、军事和卫星图像的应用时，篡改检测至关重要。
- 广播监控：水印可以用于监控图像的广播，作为版版税和营销问题的解决方案。
- 交易跟踪：不可见水印可以插入到图像中，以跟踪电子商务应用程序中的交易。这是分发过程中的一种远程触发。
- 内容存档/过滤/分类/电子商务：可以在图像中插入唯一的数字水印，以便于为了分类和存档目的对其进行快速识别。
- 身份安全：身份证和证件经常被攻击者盗窃、复制、伪造、更改或重新生成。可以扫描身份证以检测水印，用于身份验证、欺诈检测、取证分析和跟踪。

## 136 数字图像水印

## 5.2 远程医疗中的水印

互联网和通信技术的快速增长以及数字图像存档与通信系统（PACS）、医院信息系统（HIS）和放射信息系统（RIS）的部署，使得远程医疗成为可能。这包括在多个实体之间共享和交换经验、放射图像和电子患者记录（EPR）（Thanki and Borra，2018）。
