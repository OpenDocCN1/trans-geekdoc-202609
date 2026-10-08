

## 表 6.2 计算成本对比

| 方案 | 计算成本 |
|---|---|
| Wu 等人 [16] | 387.46 ms |
| Khatoon 等人 [18] | 347.1 ms |
| Sengupta 等人 [20] | 227.48 ms |
| 本文提议方案 | 193.76 ms |

- Xbp: 双线性配对运算的计算成本为 17.4 ms。
- Xhp: 哈希过程的点映射映射，计算成本为 42.10 ms。
- Xexp: 模幂运算的计算成本为 15.80 ms。
- Xmul: 执行点标量法的计算成本为 13.50 ms。
- Xadd: 点加运算的计算成本为 0.48 ms。

由于计算需求较低，所建议的方法忽略了异或（EX-OR）函数和单向哈希值的开销。考察了登录和验证程序的时间。首先，Wu 等人 [16] 方案的总计算成本为 2Tbp+1Tmul+4Thp+2Tadd=387.46ms。Khatoon 等人 [18] 方案的总计算时间为 4Thp+2Tbp+7Tmul=347.1 ms。该方案的整体计算时间为 4Tbp+4Tmul+2Thp+4T= 227.48 ms。此外，提议系统的时间成本为 2Tbp+Thp+8Tmul=193.76ms。同样证明了这些成本如何随着验证次数的增加而增加，而表格对比了计算成本。如表 6.2 所示，所建议的程序的计算成本低于前述的方法 [16, 18, 20]。

2. 通信成本：如图 6.3 和表 6.3 所示，考察了新方法与现有协议 [16, 18, 20] 的通信成本。确定了标识、随机整数、过期日期或加密哈希结果中的字符集以及 G1 的位宽。成本随着验证次数的增加而增加。

![](img/5575f2d1bada0bd1c2731bf9be91c7c9_201_0.png)

**图 6.3** 计算成本。

| 方案 | 总通信比特 |
| --- | --- |
| Wu 等人 [16] | 5,664 bits |
| Khatoon 等人 [18] | 2,624 bits |
| Sengupta 等人 [20] | 5,184 bits |
| 本文提议方案 | 4,672 bits |

在文献 [16] 中，第一条消息是 (Id, Rin, Ril, Rsi, Y₁)，下一条是 (Id, Rr, RXI, h)，包含包含五个元素的 G1 集合、两个或多个标识符的输出以及时间戳。通信成本总计为 5120 + 256 + 256 + 32 = 5,664 bits。Khatoon 等人方案 [18] 的第一条消息是 (R₁, A₁)，下一条是 (R₁, Tₙ, Aₙ)。这些消息的总比特成本为 2048 + 512 + 64 = 2,624 bits，包含两个 G1 元素集合、两个哈希函数输出和两个时间戳。

Supta 等人 [20] 有两部分信息，最重要的是 (CID, N$_p$， Zi, Fi, Ti)，下一条是 (Tss)。总计 5120 + 64 = 5,184 个比特，因为它们有五个 G1 组件和两个时间戳。所建议方案的第一条是 (U$_z$， SID$_k$, M$_k$, X$_i$, Y$_3$)，第二条是 (U$_l$, L$_p$, Y$_4$)，四个元素、两个时间戳和两个哈希函数结果为 4096 + 512 + 64 = 4,672 bits。所建议的方法比现有方法 [16, 20] 更有效。此外，所建议协议比文献 [18] 中的方法更安全且通信成本更。

## 6.5 结论

在本章中，为基于区块链的数字孪生环境设计了一种系统模型和隐私保护机制。根据所建议的方法，物理资产产生的数据由数据所有收集并传输到云中心，随后安全地通信给数据消费者。在响应数据请求之前，区块链允许数据所有验证身份。通过正式测试，我们证明了建议技术对各种攻击的抵抗力。

## 关键词

- 增强现实
- 认证标准
- 区块链
- 通信机制
- 数字孪生
- 高级加密标准
- 加密算法

## 参考文献

- 1. Jia, P., Wang, X., & Shen, X. (2023). 使用端到端同步和多属性数据的精确数字孪生构建。IEEE Internet of Things Journal, 10, 4857–4870.
- 2. Aruchamy, P, Sabeena, G., & Sowdarya, K. (2023). 用于无线传感网络的能量感知入侵检测。Concurrency and Computation, 1–28.
- 3. Jayachitra, S., Prasanth, A., & Hariprasath, S. (2023). 智能医疗中的 AI 模型。在 AI Models for Blockchain-Based Intelligent Networks in IoT Systems: Concepts, Methodologies, and Applications (pp. 141–161).
- 4. Dhiviya, S., Malathy, S., & Kumar, D. (2018). 物联网 (IoT) 元素、趋势和应用。Journal of Computational and Theoretical Nanoscale, 15, 1639–1643.
- 5. Pushpaltha, N., Sudha, M., & Sivaranjani, S. (2023). 企业数据织网架构：数据驱动的应用。5, 95–116.
- 6. Mengnan, L, Fang, S, Huiye, D., & Cunzhi, X. (2020). 数字孪生概念、技术和工业应用述。Journal of Manufacturing Systems, 58, 1–16.
- 7. Liu, B., Yu, X. L., Chen, S., Xu, X., & Zhu, L. (2017). 基于区块链的物联网数据完整性框架。IEEE International Conference on Web Services, 1, 468–475.
- 8. Wei, P. C., Dahu, W., Zhao, Y., Tyagi, S. (2019). 用于远程医疗系统的新型安全 ECC 认证和密钥管理协议。IEEE Access, 5, 1–18.
- 9. Chen, Y., Martinez, J. F., Castillejo, P., & López, L. (2019). 用于电网通信的增强型配对认证。IEEE Access, 7, 47962–47971.
- 10. Nikoogadam, M., Amintoosi, H. (2019). 用于远程医疗系统的新型安全 ECC 认证和密钥管理协议。IEEE Access, 5, 1–18.
- 11. Liu, Y., Lin, Z., Yuan, Y., & Zhou, L. (2021). 工业 4.0 中的数字孪生服务 (DTaS)。Advanced Engineering Informatics, 47.
- 12. Son, S., Lee, J., Park, Y., Park, Y., & Das, A. (2022). 用于 VANET 的基于区块链的轻量级 V2I 切换认证设计。IEEE Transactions on Network Science and Engineering, 9, 18.
- 13. Huang, W., Hu, T., Zhang, C., & Ma, S. (2021). 基于区块链的数字孪生创建方法。IEEE Access, 8, 34113–34126.
- 14. Wang, C., Cai, Z., Li, Y. (2022). 基于区块链的大数字孪生安全共享。Journal of Manufacturing Systems, 54, 338–371.
- 15. Sengupta, A., Singh, A., Kumar, P. J., & Dhar, T. (2022). 用于信息物理系统的椭圆曲线和双线性配对的双因子认证方案。Multimedia Tools and Applications, 81, 22425–22448.
- 16. Wu, T., Lee, Y., Chen, C., Tian, Y., & Al-Nabhan, N. (2021). 用于智能电网通信的增强型配对认证。Journal of Ambient Intelligence and Humanized Computing, 5, 13.

