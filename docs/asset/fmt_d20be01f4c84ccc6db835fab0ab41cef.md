
# Open Banking Implementation Across Jurisdictions

One of the most important functions of UK open banking is to maintain full market competition in the banking and financial industry. In 2016, the UK Competition and Markets Authority (`CMA`) published a report on the UK retail banking sector, concluding that larger, older banks do not have to work as hard for consumers' business as smaller, newer banks.^[1] Therefore, open banking was chosen as one of the strategies to boost competition in UK retail banking. The Open Banking Implementation Entity (`OBIE`) was established to drive open banking, and the nine largest UK banks by market share were required to build and adopt a common open banking service. Regarding `PSD2`, although the UK confirmed Brexit after the referendum on June 23, 2016, the UK chose to continue complying with `PSD2` by introducing the Payment Services Regulations 2017, which came fully into force in January 2018.

## Australia

Open banking is one of the first applications of the Consumer Data Right introduced by the Australian government. Following the Federal Treasurer's announcement that the government would introduce open banking in the 2017-2018 Budget, an Open Banking Review was conducted to recommend the best way to implement open banking in Australia. The review was published in late 2017, themed around giving customers choice, convenience, and confidence. The Australian government subsequently released a draft Consumer Data Right (`CDR`) Rules Framework^[2] for consultation in September 2018. It has been determined that `CDR` will be applied first to the banking sector. The Australian four major banks were required to provide data according to the implementation timeline, and all other banks must follow up 12 months after the dates set for the four major banks. Other sectors such as energy and telecommunications have also been proposed to follow suit.

## Singapore

Singapore adopts a supportive, guidance-based approach to open banking. In November 2014, an initiative to drive digitalization and smart technology adoption was proposed as one of the Smart Nation strategies, marking the start of open data and payments. Subsequently in 2016, the Monetary Authority of Singapore (`MAS`), together with the Association of Banks in Singapore (`ABS`), released a detailed roadmap titled "Finance-as-a-Service: API Playbook", covering recommended APIs, API standards, governance, and use cases. `MAS` also established the Financial Industry API Register as the first landing page for open APIs from financial institutions.^[3] The API Exchange (`APIX`) was launched in November 2018 as a collaboration platform to bridge financial institutions and fintech companies. However, there is no legislated or mandated timeline for open banking adoption yet.

## Hong Kong

The Hong Kong government adopts a collaborative and phased approach to advance open banking. The Hong Kong Monetary Authority (`HKMA`) announced its commitment to a new era of smart banking in September 2017. Open banking is part of this long-term strategy. After 6 months of consultation and receiving 41 submissions, `HKMA` released the "Open API Framework for the Hong Kong Banking Sector". The framework outlines 4 phases for implementing open banking in Hong Kong and provides guidance on API selection, implementation, and governance. Banks are required to provide open API implementation roadmaps to `HKMA`.

## China

虽然中国并未强制要求开放银行，但中国早已在全国范围内大力推动大数据发展。2018 年 5 月，中国银行保险监督管理委员会（`CBIRC`）发布了《银行业金融机构数据管理指引》^(4)，要求所有相关银行业金融机构遵循该指引，统一其数据治理方法。这被视为为未来几年银行业的大数据应用奠定了基础。工业和信息化部还发布了《大数据产业发展规划（2016–2020）》^(5)，鼓励资源丰富、技术先进的大数据龙头企业建设大数据平台，开放平台数据、算力、开发环境等基础资源，降低创新创业成本。2020 年 2 月，中国人民银行（`PBOC`，中国的中央银行）发布了商业银行应用程序接口安全管理规范（`JR/T 0185-2020`）。^(6) 该规范参考了英国的开放银行标准、香港的开放 API 框架以及新加坡的 API 行动指南。该规范主要关注 API 设计、部署、集成、运行和维护的安全性。

## United States

美国没有类似`PSD2`的立法或待定立法来为美国开放银行的实施创建框架。然而，多个监管机构已发布其他相关指南。消费者金融保护局（`CFPB`）发布了一套关于消费者数据获取和使用的数据共享原则；联邦金融机构检查委员会（`FFIEC`）发布了关于零售支付系统和外包技术服务的指南。一些行业团体也自行制定了开放银行标准。这些文件从不同角度为美国开放银行的实施提供了指导支持。

图 15.4 显示了不同司法管辖区开放银行覆盖范围和实施模式的摘要。欧盟强制要求所有 EEA 成员将`PSD2`转化为其本地立法；英国要求`CMA9`实施开放银行；澳大利亚先让四大银行开放数据，其他银行随后跟进。对于新加坡、香港、中国和美国，由于开放银行非强制性，覆盖范围不具体。

![](img/p503.jpg)

**图 15.4.** 不同地区及其银行覆盖范围

注：*英国直到 2020 年 1 月 31 日一直是欧盟成员国。*

根据不同司法管辖区监管机构实施开放银行的时间线，新加坡是最早发布开放 API 详细技术指南的地区之一（2016 年），而 2018 年是多个地区/国家发布开放 API 指南的共同年份。欧盟发布了其监管技术标准，英国将其开放银行标准更新至 3.1 版并推出了客户体验指南。香港也在 2018 年中咨询后发布了最终的开放 API 框架。表 15.1 总结了不同国家/地区监管机构实施开放银行的详细情况。

尽管不同国家或地区可能选择按不同的时间表或功能实施开放银行，但大多数都是从通过 API 开放公共信息数据开始，到客户交易数据，再到支付功能，从只读访问到读写访问。图 15.5 概述了欧盟、英国、澳大利亚和香港的开放银行实施时间表。

`PSD2`于 2016 年 1 月 12 日生效，所有 EEA 成员须于 2018 年 1 月 13 日或之前将其转化为本地立法。所有 EEA 成员均已成功转化其对应的`PSD2`本地版本，且`PSD2`自 2019 年 9 月 14 日起全面生效。对于英国，`CMA9`首先提供银行公共信息 API，如网点定位 API 和 ATM 定位 API。中间数据（如客户交易数据、账户余额）拟于 2017 年第一季度开放。一年后，由开放数据和匿名化及聚合数据支持的大多数用例应予以开放。至 2019 年第一季度，应提供交易（即支付）的读写访问权限。2020 年，英国客户能够通过开放银行 API 管理财务、获取信贷和进行支付。英国于 2020 年批准了开放银行路线图的最后阶段。预计未来将提供更多支付功能，如退款。

同样，澳大利亚四大银行被要求在 2019 年 7 月 1 日前提供信用卡和借记卡、存款和交易账户的产品参考数据，在 2020 年 2 月 1 日前提供抵押贷款数据和联名账户数据，在 2020 年 7 月 1 日前提供所有建议产品的消费者数据。澳大利亚其余银行通常被要求在四大银行之后额外 12 个月内遵守该时间表。到目前为止，澳大利亚客户可以授权第三方数据接收方访问其抵押贷款和联名银行账户数据。

**表 15.1.** 从监管机构视角按国家/地区划分的开放银行实施摘要

![](img/p505.jpg)

![](img/p506.jpg)

![](img/p507.jpg)

![](img/p508.jpg)

**图 15.5.** 不同国家/地区开放银行实施时间表概览

香港将开放银行实施分为四个阶段。在截至 2019 年 1 月的前六个月阶段，拟提供产品和服务信息的只读访问。客户获取流程是针对随后 12 至 15 个月的第二阶段。剩余两个阶段（账户信息检索与变更以及支付功能）的时间表拟稍后确定。第一阶段按计划进行，所有开放 API 均可在香港科技园的一个名为 Data Studio 的网站上找到。`HKMA`也于 2018 年发布了其自有的开放 API 平台。然而，由于对数据安全的担忧，进展自 2019 年 11 月起已暂停。^(7) 预计第三、四阶段的进一步安排将于 2021 年下半年发布。

### 15.3.2 API Providers

对于受监管的银行，它们通常别无选择，只能遵守监管机构的要求。然而，有趣的是，`CMA9`中的六家银行曾告知`CMA`，它们无法在 2018 年 1 月 13 日前发布所有个人活期账户和企业活期账户的读/写数据集。因此，`CMA`分别向这六家银行发布了指令，规定交付剩余数据集的时间表。目前，英国和 EEA 的大多数银行已开始采用开放银行，并按立法要求向授权第三方开放其数据，为其本地市场提供了新机遇。

同样，在澳大利亚，Westpac 和 CommBank 也曾因高成本和安全问题呼吁延长开放银行截止日期。^(8) 另一方面，澳大利亚国民银行（`NAB`）和澳新银行集团（`ANZ`）已推出自有的开放银行 API 平台，支持汇率、网点和认证 API。2020 年 7 月 1 日，这四家银行均按时开放其数据，启动了澳大利亚的开放银行进程。

### 15.3.3 API Consumers

随着金融机构提供的 API 数量不断增加，许多企业应运而生，为客户提供聚合服务，包括用于个人财务管理的 Mint 和 Quicken、用于聚合支付服务的 PayPal 和 Apple Pay，以及一些其他产品比较网站。

除了金融科技初创公司，金融机构自身也充当了使用开放数据的活跃参与者。汇丰银行在英国推出了 Connected Money 应用程序^(10)，使客户能够在一个地方查看其在不同银行的账户。巴克莱银行还在其手机银行应用程序中整合了开放银行服务，允许其客户在一个地方查看其在其他银行的活期账户。^(11)

卡组织（如 Visa 和 MasterCard）是一类特殊的 API 用户。它们天然聚合来自多家银行的数据和支付功能，这使它们成为天然的服务聚合者。两大国际卡组织 Visa 和 MasterCard 积极拥抱开放银行。2020 年，MasterCard 收购了 Finicity，这是一家为信贷决策提供金融数据聚合服务的初创公司。^(12) 同样在同年，Visa 提议收购 Plaid，后者是一家为公司提供金融科技解决方案、将人们的财务数据连接到应用程序和服务的金融科技公司。^(13) 尽管 Visa 的收购因监管反垄断担忧而失败，但这仍显示了 Visa 在开放银行领域的战略考量。从银行的角度来看，看到这些成熟的银行卡组织积极参与开放银行也符合银行的利益，因为它们作为开放银行底层基础设施的一部分，在 API 数据/功能共享过程中承担了某些风险。

## 15.4 中国的演进

尽管开放银行在中国并非强制性的，但中国的银行也抓住了这一机遇，探索业务潜力。考虑到移动支付服务在中国的强势地位，观察银行如何借助开放银行为自己定位颇具趣味。中国银行业的数字化进程也可为其他国家/地区提供良好参考。同时，各类服务聚合者应运而生，覆盖支付、财富管理、个人财务管理和贷款申请等领域。

### 15.4.1 银行

与一些西方国家类似，中国的银行业由几家主要银行主导，包括中国工商银行（`ICBC`）、中国建设银行（`CCB`）、中国农业银行（`ABC`）和中国银行（`BOC`）。还有 12 家全国性股份制商业银行，其市场份额近期不断增加。城市商业银行、民营银行和外资银行等其他银行在中国银行业也扮演着重要角色。

在中国，移动支付实现了爆发式增长，覆盖了各类日常支付场景。在此基础上，网购在全国范围内也变得越来越普及。希望满足客户移动支付和网购需求的银行，必须向各类第三方移动支付服务商或在线商户开放其支付及支付相关 API。此外，通过主动提供 API，银行也有更高的可能性与更多机构合作，这有望增加其自身银行服务的使用量。因此，中国的银行并非仅从信息类 API 起步，而是引入支付 API 以保持自身竞争力。

除了支付相关服务，银行近期还推出了更广泛的 API，如信用卡申请、贷款申请和财富管理服务。这些 API 渗透至各类场景，并产生新的业务构想以支持银行业务。例如，浦发银行在支付宝上开通了信用卡申请渠道。支付宝是中国广泛使用的移动支付应用，还连接了多家线上线下商户。客户通过支付宝申请该行信用卡后，可享受支付宝为该信用卡专门定制的多重优惠。因此，客户更有可能使用其新信用卡，从而提高了该行新信用卡客户的留存率。

开放银行传统上更关注零售客户，即面向 C 端。由于银行天然与机构有更深的金融关系，中国的银行也探索与企业客户和政府的 API 业务机会，即面向 B 端和面向 G 端。例如，企业需要向员工或客户付款，这些是高频、金额各异的支付场景。工商银行、平安银行、民生银行等已介入提供 API 解决方案，以支持这些高频企业支付场景。工商银行已将此用例应用于华为和中国人寿保险股份有限公司。随着中国数字化进程的推进，中国政府也发起了简化政务服务的举措。主要途径之一是建立各类智慧城市在线服务平台。一些银行也抓住了这一机遇。建设银行利用其金融科技能力，与全国各级政府合作，支持这一举措。

表 15.2 总结了中国银行的开放银行平台。这些银行主要是国有大型商业银行或全国性股份制商业银行。它们通常支持通用技术功能，如为主流编程语言提供软件开发工具包（`SDK`）并适用于各类平台。其 API 类别主要涵盖产品信息、银行账户服务、贷款服务、财富管理服务和支付服务。部分银行（如招商银行）还提供其他关键技术功能的 API，如 OCR 和人脸识别，以补充其银行业务。这些开放银行平台通常面向外部开发者开放，而中行、招行和平安银行等银行也利用该平台面向内部员工，以鼓励内部创新。

**表 15.2.** 中国开放银行平台汇总

![](img/p514.jpg)

![](img/p515.jpg)

### 开放银行平台的使用与发展

#### 开发者注册与验证流程
