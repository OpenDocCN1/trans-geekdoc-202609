

# 口腔黏膜纤维化检测中的 IoHT 15

类型为 `GasLevelMonitoring` 的变量通过 `USERNAME`、`DEVICE ID` 和 `DEVICE API KEY` 参数初始化，这代表了我们的模块，并允许我们通过 Wi-Fi 连接到传感器并获取数据。随后，在 `setup` 方法（该方法仅在应用程序启动时调用一次）中，执行了以下操作：

- 使用设备的 SSID 和 PASSWORD 设置设备的 Wi-Fi 连接。使用 `add Wi-Fi` 函数连接到无线网络。
- 上传代码后打开串口监视器以测试 Wi-Fi 是否正常。确保波特率为 115200。在这种情况下，如果 Wi-Fi 可用，气体水平将以百分比显示并传输到 ThingSpeak。如图 1.6 所示，正在使用 Arduino 软件的串口监视器。

在图 1.7 中，显示了 ThingSpeak 控制台的数值，数值定义了口腔不同区域气体的水平。

![](img/081dc7f102a3793cb08980a6e19b8f17_38_0.png)

图 1.6 串口监视器。

# 深度学习在网络物联网系统与安全的融合

![](img/081dc7f102a3793cb08980a6e19b8f17_39_0.png)

**图 1.7** ThingSpeak 控制台。

## 1.5 对比研究

口腔癌检测的方法有很多，从甲性蓝染色到刷刺活检、脱落细胞学、液体活检、CT 扫描、MRI、PET CT、HPLC、各种光谱学以及分子标志物等先进诊断工具 [30]。

在这些复杂的方法中，切除活检是口腔癌检测和最终诊断的金标准。活检不仅能确定疾病，还能分癌症等级（高分化、中度分化或低分化鳞状细胞）、恶性程度以及肌肉或腹膜浸润。

活检是一种侵入性程序，需要经验丰富的医生、大量的设备支持和基础设施保障，而且活检还会导致远处转移的发生。“活检”一词仍会让患者感到焦虑和担忧。在这里，我们讨论并制定了使用 IoHT 的数字传感器，它可以轻松使用并在极早期检测口腔癌，我们需要较少的基础设施支持且是非侵入性的。使用先进的基于 Web 的 API 是识别口腔癌阶段的一种有效方法，而且其使用和理解结果并不复杂。

# 口腔黏膜纤维化检测中的 IoHT 17

## 1.6 结论

本研究还包括所提系统的实现架构，以及患者端单元（PSU）的原型设计。建议的方法具有在保持同等水平医疗护理的同时，消除昂贵且乏味的医院之行的潜力。

目前没有可用于居家监测口腔健康的设备。该模型的目的是设计一种复杂的、多模态的个性化口腔检测设备，在实时环境中收集数据，并就口腔疾病和牙周疾病提供智能建议。图提供了口腔内受影响区域的可视化。识别出受影响严重的区域可以使治疗更容易并提高治愈率。

目前的诊断包括组织学切片评估的金标准方法，这是一种侵入性方法且耗时的过程。它有助于减少诊断中的主观误差。

## 参考文献

- 1. Schoder, D. and Hassan, Q.F, Introduction to the Internet of Things, in: Internet of Things A to Z: Technologies and Applications, pp. 1–50, John Wiley & Sons, Inc., Hoboken, USA, 2018.
- 2. Mehrot, R. and Gupta, D.C., Exciting new advances in oral cancer diagnosis: Avenues for early detection. Head Neck Oncol., 3, 1, 1–9, 2011.
- 3. Rai, V., Mukherjee, R., Ghosh, R., Routray, A.K., Chakraborty, C., “Omics” in oral cancer: New approaches for biomarker discovery. Arch. Oral Biol., 87, 15–34, 2018.
- 4. Rai, V., Bose, S., Saha, S., Kumar, V., Chakraborty, C., Delineating metabolic dysfunction in oral submucous fibrosis using 1H nuclear magnetic resonance spectroscopy. Arch. Oral. Biol., 97, 102–108, Jan 2019.
- 5. Rai, V., Bose, S., Saha, S., Chakraborty, C., Evaluation of oxidative stress and the microenvironment in oral submucous fibrosis. Heliyon, 5, 4–14, Apr 12 2019.
- 6. Rai, V., Mukherjee, R., Routray, A., Ghosh, A.K., Roy, S., Ghosh, B.P., Mandal, P.B., Bose, S., Chakraborty, C., Serum-based diagnostic prediction of oral submucous fibrosis using FTIR spectroscopy. Spectrochim. Acta A. Biomol. Spectrosc., 189, 322–329, Jan 15 2018.
- 7. Kruger, E. and Tennant, M.,' disadvantage and oral-health-related hospital admissions: 10-year analysis. BDJ Open, 2, 1–7, 2016.
- 8. Hassani, H., Andi, P.A., Ghodsi, A., Norouzi, K., Komandova, N., Unger, S., Shaping the future of smart dentistry: From Artificial Intelligence (AI) to Intelligence Augmentation (IA). IoT, 2, 510–523, 2021. https://doi.org/10.3390/iot2020026
- 9. Jung, S.-K. and Kim, T.-W., New approach for the diagnosis of extractions with neural network learning. Am. J. Orthodont.-Dentofacial Orthop., 149, 1–123, 2016.
- 10. Speight, P.M., Elliott, A.E., Julian, J.A., Downer, M.C., Zakrzewska, J.M., The use of artificial intelligence to identify people at risk of oral cancer and pre-cancer. Br. Dent. J., 179, 382–7, Nov 1995.
- 11. Bianco, R., Melisi, D., Ciardello, F., Tortora, G., Key cell signal pathways to therapeutic targets. E. J. Cancer, 42, 3, 290–44, Feb 2006.
- 12. Mathon, N.F. and Lloyd, A.C., Cell senescence and cancer. Rev. Cancer, 1,–203, 2011.
- 13. Diaz-Ruiz, R., Uribe-Carvajal, S., Devin, A., Rigoulet, M., Tumor cell metabolism and its common features with yeast metabolism. Biochem. Biophys. 1796, 2, 255–62, 2009.
- 14. Gupta, M., Hashk, S., Raghavendra, R., Oral fibrosis: Current concepts in etiogenesis People's Journal of Scientific Research (PSRJ), 1.
*(注：后续重复参考文献条目已根据要求省略，以避免重复输出原文)*

