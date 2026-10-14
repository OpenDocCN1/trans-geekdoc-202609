
第三类风险评估侧重于评估生命体征，以检测健康恶化的早期迹象。早期预警分数（EWS）最初被引入为评分系统。值得注意的是，EWS 因得到 NICE 的支持而在大多数英国医院被广泛采用，并已被证明有效（`[Khan et al., 2021](#ch15.xhtml#ref15_12)`）。EWS 基于计算数据，通过在不同时间间隔分析多个参数来评估患者的健康状况。用于 EWS 的生命体征数据可以手动或自动输入到患者的电子健康记录（EHR）中，这使得 EWS 分数能够随时间持续计算和可视化。该数据管理过程可使用机械式或手动式 EWS 设备完成，包括基于纸张的系统。

EWS 初始分数是基于血压、体温、心率、呼吸率和意识水平等生命体征计算得出的（`[Liu et al., 2014](#ch15.xhtml#ref15_13)`）。每项生命体征都会与既定标准进行比较，以确定个体分数，血压的取值范围为 0–6，其他参数的取值范围为 0–3。整体 EWS 分数通过将每项生命体征的分数相加，并加上相应的标准值得出。值得注意的是，EWS 存在多种版本。其中一种变体是修正早期预警分数（MEWS），它将尿液产量作为第六项生命体征纳入。此外，体温计早期预警分数（ViEWS）提供了一种基于 PDA 的床旁生命体征监测方案。另一种系统 —  — 威靈頓生理评分系统（Worthing Physiological Scoring System），在评估患者不良结局风险时，考虑了更广泛的生命体征，包括呼吸率、心率、动脉压、体温、氧饱和度以及意识水平。第三类风险评估方法结合了前几类的易用性，并借助 EWS 及其变体提供的更高灵敏度。

所有这些方法都基于启发学。这些方法将生理指标与预设标准进行比较，导致许多假阳性。此类检查可能采用人工智能（AI）以更准确地诊断患者。

### C. 健康信息记录

PCC 程序员在入院时及住院期间均记录生理观察数据。因此，医务人员使用电子健康记录（EHR）系统。医疗从业者大多管理这些 EHR 系统。这些系统仅监测当前医疗提供者的患者数据。将多个 EHR 系统的数据合并并不提供完整的患者 EHR（`[Chen et al., 2016](#ch15.xhtml#ref15_14)`）。

个人健康记录（PHR）是实现患者健康全貌统一视图的一种选择。PHR 是个人对自身健康记录的自我呈现，可能由独立的数据片段组成，也可能包含来自多个来源的数据。患者对其 PHR 拥有完全控制权，包括委托代理人或设置访问权限的能力。让患者参与健康信息的管理，能够提升协作并增加对疗法的参与度（`[Sundas et al., 2021](#ch15.xhtml#ref15_15)`）。此外，移动设备和可穿戴设备的出现极大改变了患者参与 PHR 的角色，使其能够实时监测生命体征、补充健康信息，并实现更主动的干预。当前趋势是患者将自身可穿戴设备和移动设备收集的数据补充至医护提供者的 EHR 数据（`[Sundas et al., 2022](#ch15.xhtml#ref15_16)`）（`[Figure 15.1](#ch15.xhtml#fig15_1)`）。

![Figure 15.1 Provider-controlled electronic health records (EHR) and patient-controlled, mobile, wearable sensor-based personal health records (PHR) are two types of electronic health records (EHR)](images/fig15_1_C.jpg)

[Figure 15.1 Provider-controlled electronic health records (EHR) and patient-controlled, mobile, wearable sensor-based personal health records (PHR) are two types of electronic health records (EHR)](#ch15.xhtml#R_fig15_1)

## III. Internet of health things

自 1999 年以来，物联网（IoT）已发展成为全球传感器、无线通信和信息处理的网络。IoT 依赖于智能项，这些项能够传输和分析信息，实现自主交互。最近的努力旨在定义 IoT，包括感知环境数据、提供通信服务、分析、应用以及信息交换。IoT 可以是以物为中心（传感器导向）、以网络为中心（中间件和架构导向）、以语义为中心（知识导向）或以用户为中心（面向人群的创新应用） (`[Vistisen et al., 2019](#ch15.xhtml#ref15_6)`)。本文利用 IoT 监测住院患者的生命体征。

能够共享并解释数据以提供更好患者护理的联网医疗设备构成所谓的“IoHT”。该患者导向的焦点包含四个分析层（`[Figure 15.2](#ch15.xhtml#fig15_2)`）。

![Figure 15.2 Acquisition, storage, processing, and display are shown at the bottom of this schematic of the Internet of Health Things (IoHT)](images/fig15_2_C.jpg)

[Figure 15.2 Acquisition, storage, processing, and display are shown at the bottom of this schematic of the Internet of Health Things (IoHT)](#ch15.xhtml#R_fig15_2)

智能健康物体（SHO）包括可穿戴设备和医疗器械，它们在第一阶段被获取。SHO 的主要职责是记录患者的生命体征及其他生理状态。

标准协议（如 ISO、HL7、DICOM 等）以及蓝牙、Wi‑Fi 等技术常用于其通信能力。

例如，“存储”负责以可扩展且可互操作的方式表示收集的数据。依据 Rana 等人的研究，我们建议采用云计算，因为其固有特性包括按需自助服务、广泛的网络访问、资源池以满足规模化需求、快速的灵活性以及计费能力。最近，一种云计算模式被推广为 IoHT 解决方案，以应对健康监测系统的过高延迟。雾计算是一种将本地设备（也称为边缘计算）与云资源在分散式方式相结合的云计算形态。

患者数据在语义上可互操作的个人健康记录（PHR）中登记，这是另一项重要特性。

对患者信息的处理涉及对这些信息的分析。我们建议使用基于机器学习（ML）的智能算法取代传统的启发学方法。通过前沿数据融合和预测分析，提升患者健康恶化推断的准确性，从而实现更好的资源分配。

结果在前面各层次的综合 —  — 即“展示” —  — 阶段呈现。这些结果可能以通知、推荐步骤、图表或图形的形式出现。来自特定地理区域、大都市区或医疗机构的多个去标识化 PHR 数据可合并提供流行病学视角。IoT 医疗应用仍处于起步阶段。节省成本、提升生活质量和增强用户体验均为可能的结果（`[Tang et al., 2020](#ch15.xhtml#ref15_7)`）。

从医疗提供者的角度来看，IoHT 可以减少服务中断，精准判断何时最便利地补货，并最大限度地利用稀缺资源。

### A. IoT 连接工具

