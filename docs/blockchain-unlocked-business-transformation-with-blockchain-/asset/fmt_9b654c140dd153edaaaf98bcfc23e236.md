
## 参考文献

^([3](#ch13.xhtml#ich13fn3)) Musavuli Nzanzu Guylain, Vambe, et al. “Integration of ICT in Health Service Management in Health Africa Hospital in DR Congo.” *Global Journal of Engineering, Design, and Technology*, vol. 2, no. 3, 2013, pp. 52–59., [www.longdom.org/articles/integration-of-ict-in-health-service-management-in-heal-africa-hospital-in-drcongo.pdf](http://www.longdom.org/articles/integration-of-ict-in-health-service-management-in-heal-africa-hospital-in-drcongo.pdf).

^([4](#ch13.xhtml#ich13fn4)) Thielman, Sam. “Your Private Medical Data Is for Sale – and It’s Driving a Business Worth Billions.” *The Guardian*, 10 Jan. 2017, [www.theguardian.com/technology/2017/jan/10/medical-data-multibillion-dollar-business-report-warns](http://www.theguardian.com/technology/2017/jan/10/medical-data-multibillion-dollar-business-report-warns).

^([5](#ch13.xhtml#ich13fn5)) “MedicalChain: Is Blockchain Health Records the Future? *Token Investor Point of View*.” *Hacker Noon*, June 2018, [hackernoon.com/medicalchainis-blockchain-health-records-the-future-token-investor-point-of-view-82755fd7fd9f](http://hackernoon.com/medicalchainis-blockchain-health-records-the-future-token-investor-point-of-view-82755fd7fd9f).

^([6](#ch13.xhtml#ich13fn6)) Daley, Sam. “15 Examples of How Blockchain Is Reviving Healthcare.” *Built In*, July 2019, [builtin.com/blockchain/blockchain-healthcare-applications-companies](http://builtin.com/blockchain/blockchain-healthcare-applications-companies).

## 用例 6：保险

| ![image](images/ch-14.jpg) | **用例 6：保险** |
| --- | --- |

2016 年 5 月，来自世界各地的五大保险公司聚首成立了 **Bi3（区块链保险行业倡议）**，这是一个联盟，也是采用和利用区块链技术的载体。Bi3 的成立紧随其后的一新兴趋势，当时主要银行和技术公司刚刚成立了 **Hyperledger** 和 **R3**——银行业两大区块链联盟。自那时起，Bi3 的成员数量持续增长。在本书撰写之时，成员数接近 50 家，其中包括 **Allianz**、**Swiss Re** 和 **Generali Group** 等巨头。

最初，Bi3 走了一条不同于 Hyperledger 和 R3 的路线：它尝试在 **Ethereum** 区块链上进行实验，以观察第二大区块链是否能支持该行业的特定解决方案。后两个联盟则直接着手构建自己的区块链，这类区块链后来被称为私有、许可型分布式账本技术（**DLT**）或企业级区块链。Bi3 最终决定转向并拥抱这种新型区块链，但并未自建；2017 年，它们采用了新发布的 **Hyperledger Fabric**。

然而，**Hyperledger Fabric** 显然未能满足其特定需求，Bi3 很快又转向了 **Corda**——由 **R3** 设计并构建的区块链平台。2019 年 7 月，Bi3 在 Corda 上发布了其首个应用：**B3i Cat XoL**，该应用专门设计用于修复再保险流程、合同和交易的设置与管理相关问题。

### 区块链为保险业带来的收益

再保险只是将从区块链技术中受益的保险四大核心领域之一。其他三大领域分别是：(1) **健康与人寿保险**，(2) **欺诈检测与预防**，以及 (3) **财产与意外险**。让我们看看区块链如何颠覆保险业的各个领域。

#### 再保险

再保险是保险业的关键组成部分。没有它，行业内的企业将更频繁地倒闭。尽管保险公司承担风险并为理赔提供资金，但它们需要盈利，这是该行业任何商业或投资活动的首要动力。保险公司需要赚取足够的资金来支付理赔、覆盖运营成本，并保留一定余额作为投资回报。

然而，很难预测可能发生的损失程度，以及保险公司可能需要支付的理赔金额。极有可能出现一笔巨额理赔，不仅威胁企业的利润率，还威胁其持续经营的能力。例如，如果保险公司承保地震相关风险，一旦在其大多数客户居住的几个城市和城镇发生大地震，它可能面临大量理赔。又如在火灾保险中，城市大面积起火可能波及许多客户。在这些情况下，保险公司可能发现自己支付的支票超出其资金承受能力，从而轻易倒闭。

发明再保险正是为了解决这个问题，其安排有助于将保险公司从可能导致其财务不稳定的巨额理赔中隔离出来。简单来说，一家保险公司与另一家或多家保险公司达成安排以分担风险。因此，一旦发生真正的巨额理赔，各方只需承担较小的一部分。理所当然，此类合同包含对被保险人缴纳保费的分摊。

这种分散风险的形式源于中国古代商人的实践。将货物从产地运往市场时，每位商人会将自家货物的一部分交给其他商人的船只运输。作为回报，他们也在自家船只上装载他人的货物。即使一艘船沉没，群体中每位商人可能都会损失一部分货物，但无人会损失全部存货。

同样，在再保险中，每家保险公司选择与他人分担自身风险，同时也承担他人的部分风险。因此，一旦出现重大理赔，没有任何一家保险公司需要独自承担全部负担^([1](#ch14.xhtml#ch14fn1))。

这种安排虽对保险公司大有裨益，但始终伴随着成本。参与方须经历漫长的谈判过程，包括反复的文书工作。正如人们所想，这需要多份合同来处理保险公司间的风险分担、保费分摊和理赔处理。例如，如果一份保单由十家保险公司共同承保，则至少需要谈判、签署和管理十份合同。大量精力耗费在寻求共识和为所有利益相关者构建透明环境上。

**B3i** 将保险的这一环节确定为最需要区块链技术的部分，这极有可能是其首创应用 **B3i Cat XoL** 专门服务于该领域的原因。它加快了谈判进程，减少了文书工作，并促进了合同的实施与执行。

值得注意的是，区块链架构在以下方面与再保险安排非常契合：(1) 每家保险公司都是独立实体，如同区块链网络上的节点；(2) 网络上的各保险公司必须相互信任；(3) 再保险安排中的所有保险公司都需要一个共同的真相来源；(4) 合同条款指导保险公司间的互动。

在再保险安排中，任何实体都不会失去独立性；各方继续作为独立业务运营，并与其他方保持工作关系。尽管如此，它们需要紧密合作，包括共享共同促成的保单的信息和价值。区块链用协议取代了人工步骤，从而加速了流程。

区块链架构促进了各独立实体间的顺畅交易。所有利益相关者可实时达成共识，使原本可能耗时数天甚至数月的流程在几分钟内完成。在 **B3i** 设计构建的保险应用中，每个经纪人、保险公司或再保险公司并非真正是网络上的一个节点。然而，该技术仍为它们提供了一种机制，使其作为独立参与者达成共识。
