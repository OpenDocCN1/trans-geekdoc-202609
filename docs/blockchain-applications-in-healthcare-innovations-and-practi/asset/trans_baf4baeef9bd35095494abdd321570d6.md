

MedRec 的块信息代表了私有 P2P 系统用户维护的所有权和查看权限。科学家使用以太坊智能合约来注册患者交互，方法是将健康文件与读取权限和数据检索命令（本质上是数据指针）相关联，以便在其他系统上实现。为确保数据完整性，调查人员将项目的加密哈希上传到区块链，以避免篡改。消费者可以授权在医生之间共享记录，供应商可以创建链接到特定客户的新记录。研究人员使用公钥加密和类似 DNS 的解决方案来验证身份，将真实且广泛接受的 ID 与个人的以太坊地址关联。

![](img/9f63232d0022c87774dc3933e40b24aa_113_0.png)

图 5.7. MedRec 的工作原理（Xia et al. 2017）。此图的彩色版本，请参见 www.iste.co.uk/choudhury/blockchain.zip

### 5.8.2. 基于 AI 的 EHR 解决方案

启用人工智能（AI）并由区块链驱动的 EHR 管理平台具有巨大潜力，可支持可信、安全且具有弹性的 EHR 存储服务。此类 EHR 系统还将使学者、医生和官员更容易获取数据以进行研究、执行分析并做出明智决策。

Mistry 等人（2021）提出了 MedBlock，这是一种基于 AI 和区块链的安全 EHR 解决方案，用于保护 Covid-19 阳性患者的隐私。它涉及多个组织，包括医生、员工、公职人员、医院和消费者。仅当数据传输符合智能合约参数时，MedBlock 中的数据传输才允许使用以太坊网络。MedBlock 还确保 EHR 不会被篡改或用于恶意目的。由于在疫情期间 Covid-19 患者的信息传输至关重要，所提系统使用了 6G 网络通信信道，将信息传输延迟降低至 10–100 秒，可靠性为 99.99999%。MedBlock 的层结构如下：（i）数据收集与汇总，（ii）AI，（iii）区块链和（iv）可访问性。前一层收集和汇总的数据被发送到 AI 层。AI 根据提供的数据做出决策。人工神经网络（ANN）接收患者的 Covid-19 实验室和 CT 扫描结果。它根据输入参数充当二进制分类器。ANN 模型用于确定患者是 Covid-19 阳性还是阴性。EHR（可能是阳性或阴性）作为下一层的输入。算法 5.1 描述了基于 AI 的 Covid-19 患者分类的逐步方法。

**Input:** \(\alpha\) 是数据集 \(\Pi\) 中的数据条目数量，最多 \(\delta\) 个条目。\(\Pi_X\) 和 \(\Pi_Y\) 分别是用于训练目的的 \(X_{train}\)（输入）和 \(Y_{train}\)（所需输出）。

**Output:** 分类器训练

```
procedure CLASSIFIERTRAINING(X_train, Y_train)
while (True) do
applyPCA(\(\alpha\), ncomponents = optimalnumber)
Choose the best number for the main components.
if (isNull(\(\Pi\))) then
Return (“Enter the trainingdata.”);
else if (\(\alpha > \delta\)) then
EndTraining();
ModelTestonTestData();
else
\(\alpha = \alpha + 1\);
trainingANNonTrainingData(Xtrain, ytrain);

ρ = ΠRecord   //Here the ρ is the record
ObtainNextData(Π, ρ);

Continue;

end if

end if

end while

end procedure
```

### 算法 5.1. 基于 AI 的训练程序（Mistry 等人，2021）：

### 5.8.3. 利用区块链改进医疗记录保存

phrOS（phrOS – 医疗区块链操作系统）最近由台北医学大学医院和数字金库公司（DTCO）推出（参见 DTCO n.d.）。它试图通过将患者的所有医疗记录存储在区块链上，来促进医疗组织之间的开放性。它包含照片以及关于患者病情的大量信息。智能手机应用程序允许临床医生和患者查看信息。它还通过去中心化账本技术（DLT）提高了医疗数据的安全性。开放框架允许自主和安全的解决方案，使智慧医疗成为现实。它为患者生成匿名数字身份，以帮助患者验证和识别，以及患者数据记录和查询，涵盖治疗和用药规划。智能合约可用于临床试验中的方案更改、试验入组延迟等。患者授权的索赔，包括时间戳和医疗记录，以及所有授权文件，都带有数字签名，可以随时评估，而无需第三方服务来解决冲突。

## 5.9. 结论

区块链在应用领域的使用在当今的医疗业务中至关重要。它可能导致自主的数据收集和身份验证程序，以及来自多个来源的可信和集成信息，该信息持久、防篡改且安全，盗窃风险较低。在本章中，提出了基于区块链的 EHR 框架。其主要目的是应用区块链技术于 EHR，通过解决其关键属性，提供防篡改、分布式、不可撤销、透明、可靠且可供审查的远程医疗服务。此外，本章讨论了区块链技术在医疗系统中的潜在好处。它还包括关于医生用于存储健康数据的当前基于区块链的电子健康记录的讨论。本章最后列出了必须解决的一系列挑战，以便通过即将到来的基于区块链的网络改进电子健康记录系统。

## 5.10. 参考文献

- Aggarwal, S., Chaudhary, R., AuJla, G.S., Kumar, N., Choo, K.K.R., Zomaya, A.Y. (2019). 面向智能社区的区块链：应用、挑战与机遇. 网络与计算机应用期刊, 144, 13–48. DOI: 10.1016/J.JNCA.2019.06.018.
- Al-Karaki, J.N., Gawanmeh, A., Ayache, M., Mashaleh, A. (2019). DASS-CARE：一种基于区块链的分布式、可访问、可扩展且安全的医疗框架. 2019 年第 15 届国际无线通信与移动计算会议，IWCMC 2019，330–335. DOI: 10.1109/IWCMC.2019.8766714.
- Andreev, R.A., Andreeva, P.A., Krotov, L.N., Krotova, E.L. (2018). 区块链技术综述、区块链类型及其应用. 生产中的智能系统, 16, 11. DOI: 10.22213/2410-9304-2018-1-11-14.
- Azaria, A., Ekblaw, A., Vieira, T., Lippman, A. (2016). MedRec：使用区块链进行医疗数据访问和权限管理. 2016 年第 2 届开放与大数据国际会议论文集，OBD 2016，25–30. DOI: 10.1109/OBD.2016.11.
- Bhushan, B., Khamparia, A., Sagayam, K.M., Sharma, S.K., Ahad, M.A., Debnath, N.C. (2020). 面向智慧城市的区块链：架构、集成趋势和未来研究方向综述. 可持续城市与社会, 61, 102360. DOI: 10.1016/J.SCS.2020.102360.
- Dagher, G.G., Mohler, J., Milojkovic, M., Marella, P.B. (2018). Ancile：使用区块链技术的电子健康记录访问控制和互操作性隐私保护框架. 可持续城市与社会, 39, 283–297. DOI: 10.1016/J.SCS.2018.02.014.
- DTCO (n.d.) phrOS – 医疗区块链操作系统 [在线]. 可用网址：https://phros.io/ [访问日期：2022 年 7 月 12 日].
- Gatteschi, V., Lamperti, F., Demartini, C., Prantedo, C., Santamaria, V. (2018). 保险领域的区块链与智能合约：技术是否足够成熟? 未来互联网, 10(2), 20. DOI: 10.3390/FI10020020.
- Glass, B.D. (2014). 发展中国家的假药和医疗器械. 热带医学研究与报告, 5, 11. DOI: 10.2147/RRTM.S39354.

