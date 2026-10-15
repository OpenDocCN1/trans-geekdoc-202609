
Muhammad Shafique (M’11 - SM’16) 获得了德国卡尔斯鲁厄技术学院 (KIT) 计算机科学博士学位，并于 2011 年获得该学位。随后，他作为 KIT 研究小组的创立者和负责人，带领该小组取得了显著成就，并参与了全球范围内的重要协作研发活动。除了在巴基斯坦创立一家技术初创公司外，他还发起并领导了一项 ICT 研发项目。自 2011 年以来，他一直与世界各地的多所大学建立了稳固的研究联系，积极参与并指导了多项研发活动和学生/研究生论文的指导，取得了高质量的研究成果和学术发表。加入 KIT 之前，他曾在 Streaming Networks Pvt. Ltd. 工作，期间参与了数年视频编码系统的研发工作。2016 年 10 月，他加入德国维也纳技术大学 (TU Wien) 计算机工程系的计算机体系结构与健壮、节能高效技术讲席教授职位。自 2020 年 9 月起，Shafique 博士加入纽约大学 (NYU)，目前担任 NYU-Abu Dhabi 在阿联酋的 eBrain Lab 负责人以及 Tandon 学院 NYU-New York City 在美国的全球网络教授。他还担任 NYUAD 多个中心的共同研究员/调查员，包括人工智能与机器人中心 (CAIR)、网络安全中心 (CCS)、面向城市互联网的交互中心 (CITIES) 以及量子与拓扑系统中心 (CQTS)。

Shafique 博士在获得备受瞩目的拨款、领导团队项目、按时完成演示、激励团队成员发挥最大潜能以及完成独立困难任务等方面展现了成功。他的经验得到了扎实的技术知识和卓越的教育背景（始终以金牌获得者）的佐证。他还深入理解各种视频编码标准和机器学习算法。他的研究兴趣涵盖人工智能与机器学习硬件与系统级设计、脑启发计算、神经形态计算、近似计算、量子机器学习、认知自主系统、机器人、可穿戴医疗、医疗 AI、节能系统、鲁棒计算、机器学习安全与隐私、硬件安全、新兴技术、电子设计自动化、FPGA、MPSoC、嵌入式系统以及量子计算。他尤其专注于计算与存储系统的跨层分析、建模、设计和优化。所研发的技术和工具已在物联网 (IoT)、智能物理系统 (CPS) 以及 ICT 发展 (ICT4D) 领域的应用场景中得到部署。

Shafique 博士在多个顶级会议上发表了多篇 keynote、邀请报告和讲习班。他还组织了多个重要会议的特别会议，如 DAC、ICCAD、DATE、IOLTS 和 ESWeek。他曾担任 IEEE Transactions on Computer Aided Design (TCAD)、IEEE Design and Test Magazine (D & T)、ACM Transactions on Embedded Computing (TECS)、IEEE Transactions on Sustainable Computing (T-SUSC) 以及 Elsevier MICPRO 等权威期刊的副编辑和客座编辑。他还担任 CODES+ISSS、IGSC、ISVLSI、PARMA-DITAM、RTML、ESTIMedia 和 LPDC 等会议的 TPC Chair；担任 ISVLSI、IGSC、DDECS 和 ESTIMedia 的总主席；在 DAC、ICCAD、DATE、IOLTS、DSD 和 FDL 担任 Track Chair；担任 ISVLSI 的 PhD Forum Chair。他还曾参与众多备受尊敬的 IEEE/ACM 会议的程序委员会，包括 ICCAD、DAC、MICRO、ISCA、DATE、CASES、ASPDAC 和 FPL。2022 年，他被任命为 ACM TODAES 评审委员会成员。他是 IEEE 和 IEEE 信号处理学会 (SPS) 的高级会员，ACM、SIGARCH、SIGDA、SIGBED 和 HIPEAC 的专业会员。他持有一项美国专利，合著 7 本专著、20 多章专著、350 多篇顶级期刊和会议论文，以及 100 多篇存档文章。

Shafique 博士荣获 2015 年 ACM/SIGDA 优秀新教员奖，2020、2022 和 2023 年 AI-2000 芯片技术最具影响力学者奖，2021 年 ATRC ASPIRE 研究卓越奖，其教育生涯中获得六枚金牌，以及在 CODES+ISSS、DATE、DAC 和 ICCAD 等顶级会议上多次获得最佳论文奖和提名，以及最佳硕士论文奖、DAC’14 设计跟踪最佳海报奖、IEEE 计算机杂志“本月特色论文”奖、最佳讲师奖等多项荣誉。他关于 GPU 老化优化的研究成果被《Nature Electronics》2018 年 2 月刊特别报道。Shafique 被列入 2021 年 NYU 教师荣誉名单。他的学生也在研究社区中获得了多项重要的学生和研究奖项。

# Chapter 1 Introduction

DOI: [10.1201/9781003530459-1](https://doi.org/10.1201/9781003530459-1)

在机器学习 (ML) 系统中，深度神经网络 (DNNs) 已成为计算机视觉、医学、金融和机器人等多个领域的重要里程碑。这导致了在资源受限的嵌入式系统上部署 DNN 推理工作负载的需求。然而，机器学习社区的当前趋势是朝相反方向发展，因为新兴的网络往往更深更复杂。例如，胶囊网络 (CapsNets) 是一种基于胶囊（神经元数组）的特殊 DNN 类型，能够比传统 DNN 更好地学习高层特征。因此，执行先进 DNN 的下一代计算平台将表现出高复杂度和高能耗，这对资源受限设备的可行性提出了挑战。

另一方面，脉冲神经网络 (SNNs) 作为高效计算基础设施，用于处理事件驱动的 DNN，它们更贴近人类大脑的功能认知。这推动了神经形态计算范式的发展，其硬件架构支持能量高效的事件驱动 SNN 执行。

另一个需要考虑的基本方面是部署先进深度学习 (DL) 架构时的安全性。系统在处理安全关键应用时，必须对各种漏洞威胁保持高度鲁棒性。攻击者可以通过攻击硬件和软件栈的不同层面，或扰动输入、内存或计算引擎来威胁 DL 系统的完整性。因此，必须在系统不同抽象层次上应用防御措施，这通常会带来一定的能耗和计算开销。此外，虽然传统 DNN 的安全性研究已相当充分，但研究先进 DL 系统的安全性则为利用其独特特性提供了独特机会。

除了这些约束和需求，不断变化的市场对快速交付优化的端到端系统施加了巨大压力。因此，加速设计流程的优化对于满足这些时间到市场的需求至关重要。

## 1.1 Optimization Objectives for Dnn Models and Architectures

### 1.1.1 Energy-Efficiency

先进 DNNs 耗费大量资源，需要大容量内存和昂贵的计算引擎。此外，实时系统的严格约束要求输出必须以快速响应生成。为使快速且高精度的 DNN 能够在资源受限的便携设备上使用，可以应用多种优化技术来提升 DNN 执行的能源效率。

