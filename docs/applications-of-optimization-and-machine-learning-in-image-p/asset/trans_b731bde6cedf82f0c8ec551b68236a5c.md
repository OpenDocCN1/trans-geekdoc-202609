

## 2.2 云计算协议

### 2.2.1 HTTP

超文本传输协议（HTTP）基于请求–响应形式的消息传递。它是半双工 TCP 连接，因此是一种无连接协议。HTTP 遵循 REST [46, 47] 准则，该准则负责 Web 服务指南。Cloud IoT Core 支持 HTTP 1.1。可以向服务器发送请求，对数据执行创建、更新、读取和删除操作。这可以通过 HTTP PUT、GET、POST 和 DELETE 等方法实现。CRUD（创建-读取-更新-删除）操作让用户可以直接与目标资源交互并对其进行修改 [48]。HTTP 还为客户端和服务器提供一种称为内容协商 [49] 的机制。数据必须使用 base64 编码，并且此任务需要更多的网络和 CPU 资源。

### 2.2.2 MQTT

MQTT（消息队列遥测传输）[50–52] 协议旨在用于传感器网络。由于它主要针对传感器设计，因此最适合 IoT 和云。它由 IBM 开发，是一种轻量级的机器对机器通信方法。该协议背后的基本思想是，传感器并非用于处理，而是用于将数据传输到预定的中心位置。它使用全双工通信，是一种面向连接的协议。

## 2.3 结论

物联网（IoT）极大地改善并改变了我们生活的许多方面，带来了前所未有的益处和困难。医疗保健、农业、制造业、交通运输和智慧城市只是 IoT 转变的几个领域，它提高了效率、产量和便利性。对于企业、政府和个人而言，能够连接并与物体和设备通信、实时收集和分析数据以及自动化操作，开辟了新的机遇。智能家居、可穿戴技术、网联汽车和智能供应链只是 IoT 突破所实现的几个应用。通过提供个性化体验、最大限度地利用资源并实现预测性维护，这些进步提高了我们的生活质量。通过促进智能能源管理、减少浪费和精准农业等，IoT 还为环境可持续性做出了贡献。

## 参考文献

- [1] Ashton, K. (2009). 那“物联网”的事。 *RFID 杂志*, 22(7), 97–114.
- [2] Ding, S., Ward, H., & Tukker, A. (2023). 物联网如何影响物流行业的可持续性绩效——一个中国案例研究。 *更清洁的物流与供应链*, 6, 100094.
- [3] Koohang, A., Sargent, C. S., Nord, J. H., & Paliszkiewicz, J. (2022). 物联网（IoT）：从意识到持续使用。 *国际信息管理杂志*, 62, 102442.
- [4] Sinha, B., & Dhanalakshmi, R. (2022). 智慧农业中物联网的最新进展与挑战：一项综述。 *未来一代计算机系统*, 126, 169–184.
- [5] Friess, P., & Ibanez, F. (2022). 将物联网提升到下一个水平。在 *物联网应用——从研究和创新到市场部署* (第 3–6 页)。River Publishers.
- [6] Wojcicki, K., Biegańska, M., Paliwoda, B., & Górna, J. (2022). 工业中的物联网：研究概况、应用、挑战与机遇——一项综述。 *能源*, 15(5), 1806.
- [7] Salih, K. O. M., Rashid, T. A., Radovanovic, D., & Bacanin, N. (2022). 针对工业市场的物联网综合综述。 *传感器*, 22(3), 730.
- [8] Mishra, S., & Tyagi, A. K. (2022). 基于物联网的云应用中机器学习技术的作用。 *基于人工智能的物联网系统*, 105–135.
- [9] Bharanay, S., Sharma, S., Khalaf, O. I., Abdulsahib, G. M., Al Humaimedy, A. S., Aldhyani, T. H., & Alkahtani, H. (2022). 可持续云计算中节能技术的系统综述。 *可持续性*, 14(10), 6256.
- [10] Gazis, V., Götz, M., Huber, M., Leonardi, A., Mathioudakis, K., Wiesmaier, A., Zeiger, F., & Vasilomanolakis, E. (2015, August). 物联网技术综述。在 *2015 年国际无线通信与移动计算会议（IWCMC）* (第 1090–1095 页)。IEEE.
- [11] Chaudhary, H. A. A., Guevara, I., John, J., Singh, A., Margaria, T., & Pesch, D. (2022). 面向边缘分析的低代码物联网应用开发。在 *IFIP 国际物联网会议* (第 293–312 页)。Springer.
- [12] Wang, Z., Zhou, Z., Zhang, H., Zhang, G., Ding, H., & Farouk, A. (2022). 6G 空天地一体化电力物联网中的人工智能云边端协作。 *IEEE 无线通信*, 29(1), 16–23.
- [13] Barua, A., Al Alamin, M. A., Hossain, M. S., & Hossain, E. (2022). IoT 和可穿戴设备中蓝牙低能耗的安全与隐私威胁：一项全面综述。 *IEEE 通信学会开放期刊*, 3, 251–281.
- [14] Khanh, Q. V., Hoai, N. V., Manh, L. D., Le, A. N., & Jeon, G. (2022). 5G 中物联网的无线通信技术：愿景、应用与挑战。 Wireless Communications and Mobile Computing, 2022, 1–12.
- [15] Lazaro, A., Villarino, R., & Girbau, D. (2018). 基于能量收集的物联网应用 NFC 传感器综述。 Sensors, 18(11), 3746.
- [16] Shree, S. S., & Poovathy, J. F. G. (2022, August). 物联网及相关概念中的通信技术：一项综述。在 2022 第三届智能计算仪器与控制技术国际会议 (ICICICT) (第 310–314 页)。IEEE.
- [17] Kalanandhini, G., Aravind, A., Vijayalakshmi, G., Gayathri, J., & Senthilkumar, K. K. (2022, May). 基于体域网和散射网架构的物联网蓝牙技术。在 AIP 会议论文集 (第 2393 卷, 第 1 期, 第 020121 页)。AIP Publishing LLC.
- [18] Arnold, L., Jöhnk, J., Vogt, F., & Urbach, N. (2022). 工业物联网平台的架构特征——一种分类法和五种普遍原型。 Electronic Markets, 32(2), 927–944.
- [19] Mohamed, K. S. (2022). 物联网设备的蓝牙 5.0 调制解调器设计 (第 45–73 页)。Springer.
- [20] Padiya, S. D., & Gulhane, V. S. (2022). 物联网应用中蓝牙版本（4.0、4.2、5、5.1 和 5.2）分析。在 实施下一代无线通信的数据分析与架构 (第 153–178 页)。IGI Global.
- [21] Ullah, A., Nawi, N. M., & Ouahame, S. (2022). 云计算中 VM 任务分配系统的最新进展：2015 至 2021 年综述。 Artificial Intelligence Review, 1–45.
- [22] Huawei Technologies Co., Ltd. (2022). 云计算中的存储基础。在 云计算技术 (第 197–250 页)。Springer Nature.
- [23] Priyadarshini, I., Bhola, B., Kumar, R., & So-In, C. (2022). 面向空间物联网 (IoST) 的新型云架构。 IEEE Access, 10, 15118–15134.
- [24] Chyad, H. S., Mustafa, R. A., & George, D. N. (2022). 基于智能云管理的云资源建模。 电气工程与信息学通报, 11(2), 1134–1142.
- [25] Malik, S., Tahir, M., Sardaraz, M., & Alourani, A. (2022). 面向云数据中心的资源利用率预测模型：使用进化算法和机器学习技术。 应用科学, 12(4), 2160.
- [26] Dolan, E., & Widayanti, R. (2022). 针对热点网络用户实施身份验证系统以提高计算机网络安全性。 网络与 IT 服务管理国际期刊, 2(1), 88–94.
- [27] Pohlmann, N. (2022). 传输层安全 (TLS)/安全套接层 (SSL)。在 数字化中网络安全系统概念、原则、机制、架构和特性教程：网络安全 (第 439–473 页)。Springer Fachmedien Wiesbaden.
- [28] Mihailescu, M. I., & Nita, S. L. (2022). 面向云环境的具有生物识别身份验证和授权的可搜索加密方案。 密码学, 6(1), 8.

