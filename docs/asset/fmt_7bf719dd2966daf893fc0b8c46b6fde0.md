
Binder, Benjamin J.T., Pavlov, A., Tor, A. and Johansen, T.A. 2015. 使用移动时域估计估计带电潜泵井的流率和粘度. This work is funded by the Research Council of Norway and Statoil through the petromaks project no. 215684: Enabling high-performance safety-critical offshore and subsea automatic control systems using embedded optimization (emopt). IFACPapersOnLine 48(6): 140–146. 2nd IFAC Workshop on Automatic Control in Offshore Oil and Gas Production OOGP 2015.

Camilleri, L. and Zhou, W. (eds.). 2011. 从 ESP 压力计数据获取实时流率、水含量和储层诊断, volume All Days. SPE Offshore Europe Conference and Exhibition, 2011.

Camilleri, L., El Gindy, M., Rusakov, A. and Adoghe, S. (eds.). 2015. 将 ESP 实时数据转换为远程油井的流率和储层信息, volume Day 2 Wed., 16 September. of SPE Middle East Intelligent Oil and Gas Symposium.

Camilleri, L., El Gindy, M. and Rusakov, A. (eds.). 2016a. ESP 实时数据在非常规井中实现高频、高分辨率和高重复性的井测试, volume All Days. of SPE/AAPG/SEG Unconventional Resources Technology Conference.

Camilleri, L., El-Gindy, M. Rusakov, A., Bosia, F., Salvatore, P. and Rizza, G. (eds.). 2016b. 测试不可测试的——在远程 ESP 井上以高精度提供流率测量, volume Day 2 Tue., 08 November. Abu Dhabi International Petroleum Exhibition and Conference, 2016.

Camilleri, L., El Gindy, M., Rusakov, A., Ginawi, I., Abdelmotaal, H., Sayed, E., Edris, T. and Karam, M. (eds.). 2017. 利用 ESP 的高频高分辨率流率测量提高产量, volume Day 2 Tue., 25 April SPE Gulf Coast Section Electric Submersible Pumps Symposium, 2017.

Carpenter, C. 2019. 分析解决方案有助于识别井口抽油杆泵故障. Journal of Petroleum Technology 71(05): 63–64.

Cramer, R. and Goh, K-C. (eds.). 2009. 气井、海底井和多区井的数据驱动监测与优化, volume All Days. SPE Digital Energy Conference and Exhibition, 2009.

Cramer, R., Griffiths, W.N., Kinghorn, P., Schotanus, D., Brutz, J.M. and Mueller, K. (eds.). 2011. 大型海上项目启动期间的虚拟测量价值, volume All Days. IPTC International Petroleum Technology Conference, 2011.

# 参考文献

- Poulisse, H., Van Overschee, P., Briers, J., Moncur, C. and Goh, K-C. 2006. 连续油井生产流量监测与监控。论文发表于 SPE Intelligent Energy International，荷兰阿姆斯特丹，4月11–13日。

- Sabaa, A., El Ela, M.A., El-Banbi, A.H. and Sayyouh, Mohamed H.M. 2022. 用于预测电潜泵井生产率的人工神经网络模型。SPE Production & Operations, pp. 1–10. 9月。

- Takacs, G. 2018. 第1章 - 引言。pp. 1–10. 收录于：Gabor Takacs (编)。Electrical Submersible Pumps Manual (第二版)。休斯顿, 德克萨斯州：Gulf Professional Publishing,

- Vinogradov, D. and Vorobev, D. (eds.). 2020. 虚拟流量计 Novy Port  field 案例, 卷 Day 3, 周三, 10月28日。SPE Russian Petroleum Technology Conference。

- Zhang, S. and Tang, Y. 2008. 抽油机示功图的间接测量。pp. 952–955。收录于：2008 7th World Congress on Intelligent Control and Automation。

- Zhu, D., Alyamkin, S., Sesack, L., Bridges, J. and Letzig, J. (eds.). 2016. 基于时间序列生产数据分析的电潜泵运行优化, 卷 All Days。SPE Intelligent Energy International Conference and Exhibition。

- Zhu, D., Luo, X., Zhang, Z., Li, X., Peng, G., Zhu, L. and Jin, X. 2021. 基于周期性电流数据的地表示功图全复现。SPE Production & Operations 36(03): 594–603。

- Zhu, K., Wang, L., Du, Y., Jiang, C. and Sun, Z. 2020. DeepLog: 利用全卷积网络通过多测井信号识别致密气藏。IEEE Geoscience and Remote Sensing Letters, title=Prediction of Subsurface NMR T2 Distributions in a Shale Petroleum System Using Variational Autoencoder-Based Neural Networks 17(4): 568–571。

- Ziegel, P., Shirzadi, S., Wang, S., Bailey, R., Griffiths, P., Ghuwalela, K., Ogedengbe, A. and Johnson, D. 2014. 一种基于实时数据的北海资产建模与优化的数据驱动方法。论文发表于 SPE Intelligent Energy Conference & Exhibition，荷兰乌得勒支，2014年4月。doi: https://doi.org/10.2118/167850-MS。

# 第6章

## 基于数据驱动和机器学习方法估算智能井完井中多区ICV注水速率

Daniel Asante Otchere¹,²,* and Mohammed Ayoub Abdalla Mohammed³

¹ 地下地震成像研究中心, Universiti Teknologi PETRONAS, 32610, Seri Iskandar, Perak Darul Ridzuan, 马来西亚。

² 计算与数据科学研究所, Pennsylvania State University, University Park, PA, 美国。

³ 化工与石油工程, UAE University, Sheikh Khalifa Street at Tawam R/A, Maqam District, Al Ain, 阿联酋。

\* 通讯作者: ascotjnr@yahoo.com

## 1. 引言

“智能”或“智慧”井被认为是高度发展的一种非常规井类型。该说法指的是近年来引入的尖端井型。这些井的进步性体现在其收集和分析数据、监测和控制生产过程以及根据储层条件变化调整生产的能力上。“智能”或“智慧”这一术语的提出是为了突出这些井中高度自动化和先进技术的使用。典型的智能井具有定制完井，采用封隔器或密封部件分隔井筒，并在非均质地层的不同储层段落的生产管柱上安装井下传感器和压力控制阀。井下传感器可实现对储层温度和压力的连续监测，以及控制阀，可用于近似计算分层流量。相比之下，像流入控制阀（ICVs）这样的井下阀门在控制分层流量方面具有灵活性，并用作优化井以提高采收率的控制变量。智能井可以是多分支井，每个分支由一个ICV控制，也可以是单井眼井，每个区段由一个ICV控制。大多数新的油气田开发都包括智能井。它们在降低资本和运营成本的同时实现预期产量。

智能井完井是一种用于优化油气储层生产的 technology。它涉及收集、传输和分析完井、生产和储层数据，从而实现远程选择性分层控制。该技术的应用有助于提高产量和最终采收率，同时降低资本和运营支出。智能井完井系统经过精心设计，以满足全球对智能完井的需求，即使在最困难的条件下。这些系统由多种组件组成，例如永久监测和井下控制系统、分层隔离和区间控制装置、分布式温度传感系统、地表控制和监测系统、数据采集和管理软件以及系统附件。

多层储层为油气生产带来了独特的一系列挑战，而智能井完井技术非常适合应对这些挑战。通过将井完井划分为可独立控制的多个生产区，智能井完井可实现对储层不同区段生产的 selective 控制。这使得注水、气水突破和单层生产能力的有效管理成为可能，有助于提高最终采收率并降低资本和运营支出。

智能井完井技术还可以改善注水和气突破的管理，从而减少产水量并提高最终采收率。通过远程控制ICV，可以管理来自储层不同区段的流体流动，从而提高生产效率并降低成本。除了上述好处外，智能井完井技术还可以减少油田开发所需的井数，从而降低钻井和完井成本。此外，它还允许通过远程分层控制进行水管理，减少地表处理设施的规模和复杂性。

多区智能注水井的操作人员面临着估算和管理各储层区段通过分层ICV的流体分配的问题。基于可用的井筒、流体和井管柱数据，包括分层ICV的设定、几何尺寸、生产管柱、注入流体性质、井口P/T数据以及分层储层压力/注入能力数据，已开发出一种简单而精确的经验相关性来估算注入到每个储层区段的流体体积。然而，这些方程可能会失准，有时需要重新校准。新的井下压力制度、新流体（水/气）和井口压力都是需要重新校准的情况。

作为生产技术人员，最重要的工作之一是根据井底压力、油管压差和井口压力等运行参数估算来自/流向多个储层区段的油产量/注水量。这些工作流程或经验相关性大多在某种程度上假设了物理规律，这涉及许多假设。因此，本研究提出采用数据驱动的方法。该方法使用人工智能（AI）技术，计算机基于数据模式学习物理规律，无需假设和复杂的物理模型。该概念提出先进的数据分析技术，使人们能够获得对运行参数的新见解和理解（Otchere et al., 2022b）。先进的数据分析和机器学习将被用于构建模型，并利用实际油田的日生产或注入数据预测向多个储层注入的水量。本工作的主要目标是：

1. 研究并理解通过先进数据分析技术估算分层速率所需的关键运行参数。

2. 创建一种可靠的方法，使用机器学习模型计算多层储层中的生产速率。

鉴于人工智能在石油和天然气行业取得的成功，该倡议具有巨大的研究潜力。当前研究应用机器学习技术来优化ICV设定以提高产量。在本项目中，将采用八种机器学习模型来估算ICV设定失准时注入到每个储层的注水量，从而导致错误的分层估算。这种方法将取代重新校准经验相关性以估算注入多个区段的水量，从而导致油田生产中断。在获得可接受的结果后，该方法将应用于具有各种输入参数的油生产井。该研究可以提供一种简单而准确的数据驱动方法，根据运行参数估算每个储层单元的生产流体体积。该方法还可以提供产量的实时估算，有助于储层管理计划。本提案中提交的当前结果可扩展到储层管理计划的先进制定、满足关键目标的日生产运营变化以及运营商负责任地开发国内石油资源的政策。

## 2. 智能完井简述

智能完井系统通过收集、传输和分析与完井、生产和油藏相关的数据来提高产量。这允许对特定区域进行远程控制，最终提高油藏效率。该系统通过混合不同区域的产量来帮助提高产量，能够更好地管理注水和突破，并通过最大限度地减少所需井数和优化生产来降低资本和运营开支，而无需昂贵的人工干预。智能完井系统设计用于在各种环境中运行，并可包括用于区域隔离、区间控制、井下控制、永久监测和温度传感的设备组合，以及用于数据采集和管理的软件。

### 2.1 ICV 设置与确定

应进行多次生产模拟，以优化 ICV 的设计和尺寸。ICV 尺寸对生产速率有显著影响，而生产速率在不同油田中可能差异很大。为了实现特定目标，例如最大化采油量或最小化产水量，确定 ICV 的最佳配置至关重要。这可以通过设计 ICV 来确保每种设置产生唯一的生产速率来实现。这种方法对优化过程有很大影响，因为所得数据为达成预期结果的最佳 ICV 配置提供了宝贵的见解。

在 ICV 设计领域，确定最优设计的过程通常取决于每个分支的生产能力。然而，在实践中，一些石油公司通过采用油田平均生产速率作为设计基础，而不是单个分支的速率，简化了这一过程。这种方法通常被认为更方便，尤其是出于维护和监测等后勤目的。在本研究中，ICV 尺寸的选择基于特定设置下的单区域流量、两个区域合采时的流量（迭代计算）以及三个区域合采时的流量，同时监测井下压力。ICV 设置被离散化，使得每种设置产生与区域压力对应的生产速率。设计 ICV 时考虑的几个因素包括：

- 1. 运行模拟以确定每个区域在合采所有区域和依次单独生产单个区域时的最小和最大生产速率。

- 2. 通过建立预定义的中间设置（范围从 0 到 10）来实现 ICV 区域的离散化，这些设置对应于最小和最大生产速率。ICV 区域被分割为这些设置，以量化表示阀门的开度，其中 0 表示完全关闭，10 表示完全打开。

- 3. 根据井下压力监测，将 ICV（智能完井阀）调整到其最高设置范围（7–10）可实现最大生产速率，而最低 ICV 设置范围（0–3）则导致生产速率为零。

- 4. 如果不同区域之间的生产速率差异显著，则适当使用不同尺寸的 ICV，尽管这可能不是一种可行的方法。

- 5. 在新的 ICV 设置下，对不同的基础情形进行了测试，包括所有区域同时生产和单个区域单独生产。如果一个区域内超过半数的 ICV 设置产生相同的生产速率，则降低最大生产速率。此外，模拟的案例旨在捕捉特定区域出现生产问题（气/水突破）而不得不关闭的情况。虽然这些数据应用于注入井，但该方法是模拟生产井进行的，以捕捉各种情景和生产问题。

### 2.2 ICV 创新与机器学习应用的文献综述

在文献中，ICV 作为优化油气藏生产的手段被广泛研究。这些阀门用于管理进入井内的流体，从而实现对储层不同区域的选择性生产控制。这种选择性控制能够有效管理注水、气水突破和单个区域的生产力，从而有助于提高最终采收率并降低资本和运营开支。

人工智能已成功应用于石油行业，包括储层表征（Otchere 等人，2021）、地震解释（Otchere 等人，2022c）、油藏工程（Otchere 等人，2022a）以及许多其他领域。机器学习技术也被应用于 ICV 阀的优化。研究人员使用机器学习算法来模拟 ICV 设置与生产速率之间的关系，并预测给定条件下最优的 ICV 设置。这些模型可以考虑多种因素，如井筒几何形状、流体性质和储层特征。

人们提出了各种技术来提高智能井的生产力。例如，Mubarak 等人（2008）采用密集生产测试来减少三侧向智能井的产水量，发现侧向对 ICV 设置敏感。对于不同的产水来源，不同的设置被证明是可行的。类似地，Jalali 等人（1998）通过先无限制地生产顶层，然后逐渐解除底层节流，提高了智能气井的输气速率。此外，Yeten 等人（2002）采用基于梯度的方法来优化智能井的累积采油量。Naus 等人（2006）提出了一种方法来确定 ICV 设置导致的流量变化，并在两个储层中进行了测试，目标是实现最大最终采收率。此外，Brouwer 和 Jansen（2002）评估了智能完井在多个井目标和限制条件下的影响，而 Alhuthali 等人（2010）使用智能井和最优速率控制进行水驱优化。Yeten（2003）提出了一种通用方法，使用遗传算法、爬山算法和人工神经网络（ANNs）来优化井型、轨迹、位置和 ICV 设置。另一项由 Behrouz 等人（2016）进行的研究是利用智能井技术开发了一种新方法，用于选择和排序候选井和油田、确定区间控制阀（ICV）尺寸以及优化 ICV 设置。该研究提出了一种智能井中的高效 ICV 设置优化方法，可最大化累积油量、最小化产水量或同时实现两者。研究考虑了实际案例，以证明所提出方法的有效性和鲁棒性，使用所开发的方法使得目标函数有显著改善。

Huang 等人（2011）旨在通过优化井下监测、数据传输、智能优化和生产控制系统，在中国开发智能完井系统。作者开发了一种具有专有互联网协议（IP）的 ICV 系统，并在中国创建了第一套用于可测量、可优化油井开采的智能完井系统（ICS）。结果表明，该系统稳定可靠，石油产量增加了 10.5%。Malakooti 等人（2020）提出了一种集成控制与监测（ICM）算法，可以提高多区域 I 型井的产量。该算法采用两级优化过程，以最大化预测的区域或石油生产可靠性。作者将该算法应用于商业瞬态井筒模拟器进行验证。模拟结果表明，ICM 算法可以在减少所需流动测试次数的同时优化石油生产。此外，该研究强调，在多区域 I 型井中，精确估算区域属性并非实现最大石油产量的必要条件。该算法的有效性表明，它可能适用于优化多井流量分配和多区域 I 型井的启动过程。
