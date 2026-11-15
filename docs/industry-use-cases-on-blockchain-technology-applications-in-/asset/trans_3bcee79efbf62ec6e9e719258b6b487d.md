

## 区块链拥塞

在供应链应用中，最终用户产品在将资源转化为最终用户产品的过程中经历了一系列交易。区块链网络中存在中间参与者，他们将主要资源开发成各种产品并分发给客户。这些场景将向区块链添加数百万条记录。这导致了区块链网络中区块拥塞以及参与者处的数据冗余等多个挑战。产品生命周期中发生的所有交易对区块链网络中的所有参与者并不同样重要，因此需要一种交易验证的补偿模型。如图7所示，P4从主要资源制作不同的产品并将其分发给P5和P6。

(T01, T02) -> (T1 ... Tn1), (Tn1... Tn2), (Tn2 ... Tn3), ........ 其中 n1, n2, n3 ∈ Z
(Ti1, Ti2) -> (Ti1 ... Tmi), (Tmi1... Tm2), (Tm2 ... Tm3), ... 其中 m1, m2, m3 ∈ Z
(T...) -> (T21 ... Tkl), (Tk1... Tk2), (Tk2 ... Tk3), ............ 其中 k1, k2, k3 ∈ Z

在P4处，交易T01和T02基于产品创建和客户要求创建一组交易。同样适用于T11、T12和T..。如果存在多个开发子产品的P4类型中间参与者，这将向区块链添加数百万条记录，在区块链网络中产生实时拥塞。此外，这将向区块链添加冗余数据。这是一种不断增长的实时开销，对区块链网络的可扩展性产生负面影响。为供应链应用管理时序数据以减少交易冗余和交易验证仍需要重大发展。IoT设备与供应链集成，并在整个供应链中生成数百万条记录。可以采用临时解决方案来管理这些记录，例如，Hyperledger Fabric支持即插即用本地数据存储来记录IoT数据，且只有数据集的哈希值会记录在区块链中。IoT与供应链的集成是一种常见场景，因此区块链与IoT集成需要新的标准。

此外，供应链应用需要遵守各地区制定的法规。各地区的监管组织仅对供应链交易中特定一组信息感兴趣，以进行合规性检查。在当前的区块链架构中，参与者将维护完整的区块链，因此监管者作为区块链网络参与者的角色不切实际。迄今为止，没有任何区块链架构提供将监管者定位在区块链中所需的必要标准。

如图9所示，作者提议一个私有通道，供监管组织仅与所需参与者连接以进行合规性检查。参照图9，ORG 1至4和ORG 1至3连接在两个区块链网络中。REG ORG有一个私有通道，连接两个不同区块链网络中的ORG3和ORG 2。各地区的监管组织可以成为该私有通道的授权成员，从而加快供应链交易验证速度，避免当前系统中的长时间延迟。这还可以为任何需要通过供应链发送物品的人提供透明的合规性检查支持。该主题领域需要进一步阐述，因为迄今尚无适当的标准或成熟产品来加快监管合规，且区块链技术在此领域已显示出巨大潜力。

Figure 9. Regulatory organization in blockchains

![](img/c4fdb01b72024490068fd1d70a4679bb_104_0.png)

在我们提出的架构中，需要监管合规的交易将被导向监管组织，分布式账本将使用批准或拒绝交易的区块进行更新。一批批准或拒绝的交易将作为{hash(block), block}保存在监管者数据存储中。区块的哈希值记录在区块链中。在此方法中，监管者不需要保留不必要的记录，他们只保留其处理过的记录（批准或拒绝的记录）。未来应用程序可以使用这些记录的数据。例如，由于这些区块在区块链上具有必要的哈希键，审计追踪可以连接到网络中参与者的账本。

## 用例

JLP Meats Trading组织（JLP Meats，2020）从澳大利亚、南美洲和欧洲进口肉类，并在英国销售。其客户是英国的餐厅、零售店和肉铺。JLP Meats生产数百种定制肉类产品并分发给客户。农场到餐桌流程的抽象视图如图10所示。作者已使用Hyperledger Fabric实施了一个区块链解决方案，以说明端到端追踪、产品召回、交易拥塞等。

Figure 10. Use Case of JLP Meats, London

![](img/c4fdb01b72024490068fd1d70a4679bb_104_1.png)

为进行说明，作者考虑了以下特定场景。农民Samex使用物流公司Sandford group将草饲和谷饲牛肉出口到英国的JLP Meats。JLP Meats将牛肉转化为300至500克的包装，并供应给其客户ASDA和TESCO商店。从TESCO（或ASDA）购买一包牛肉的买家想要了解该产品的端到端详情。在此，典型的一组交易可以按图11所示建模。

Figure 11. Transactions in the Use Case scenario

![](img/c4fdb01b72024490068fd1d70a4679bb_105_0.png)

JLP Meats供应各种类型的产品，产生数千笔交易，导致区块链中的交易拥塞。交易验证由网络中获许可的验证者执行，此过程应获得补偿。然而，本章不涵盖补偿过程；质量控制由监管者管理。本章提议一个监管者私有通道网络，他们可以连接到区块链网络以执行监管活动和必要的背书，如图9所示。

## 设计、实现与测试

作者使用公共和许可的区块链，使账本去中心化，并且选定的一组节点参与共识程序。作者已在Ubuntu 18.04上使用Hyperledger Fabric⁵、Composer Playground、Hyperledger Explorer和Docker实现了上述用例。

使用Hyperledger Fabric的拟议解决方案的高层架构如图12所示。

Figure 12. The High-level Architecture Based on Hyperledger Fabric

![](img/c4fdb01b72024490068fd1d70a4679bb_106_0.png)

对等节点是区块链网络的成员。业务网络在上述对等节点上开发和安装，并创建了一个REST-API⁶来执行物品的端到端追踪。Hyperledger Composer Playground用于实现和测试场景，Hyperledger区块链浏览器用于可视化区块链统计信息。Swagger⁷用于可视化和测试REST端点。肉类包装的交易事务定义如图13所示。对等节点可以是授权的矿工或参与者，用于挖掘供应链交易，应为交易验证引入补偿模型。然而，迄今尚无适当的标准或可用矿工来挖掘供应链交易。这些必要的发展可以进一步革新未来的供应链系统。

Figure 13. Trading Transaction for Packets

```
/**
 * Track the trade of a packet from one trader to another
 * @param {org.jlp.trading.TradePacket} trade - the trade to be processed
 * @transaction
 */
async function tradePacket(trade) { // eslint-disable-line no-unused-vars
    // set the new owner of the packet
    trade.packet.owner = trade.newOwner;
    const assetRegistry = await getAssetRegistry('org.jlp.trading.Packet');

    // emit a notification that a trade has occurred
    const tradePacketNotification = getFactory().newEvent('org.jlp.trading', 'TradePacketNotification');
    tradePacketNotification.packet = trade.packet;
    emit(tradePacketNotification);

    // persist the state of the packet
    await assetRegistry.update(trade.packet);
}
```

