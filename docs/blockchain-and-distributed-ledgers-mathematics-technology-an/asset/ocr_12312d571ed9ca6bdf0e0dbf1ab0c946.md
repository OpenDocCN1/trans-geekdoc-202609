# Chapter 11 Current Research Topics | 373

![](bbox=[0.147, 0.093, 0.853, 0.335])

**Figure 11.13** DAG is a scalable alternative to the linear blockchain topology. Own graphics.

This figure shows that transactions can receive both direct and indirect approval from their peers. For instance, TX A is directly approved by TX C, and indirectly by TX E (either E->C->A or E->D->A). Of course, every transaction approves itself. The cumulative number of approvals determines whether a transaction is confirmed, unconfirmed, or by the tip of the tangle. TX A has 11 approvals in total and is confirmed; TX G has three approvals, and is unconfirmed; TX J has only one approval (from itself) and hence is a transaction. Similarly to the longest chain rule, shown in Figure 3.9 in the case of forging, TXs with the highest number of cumulative transactions survive, while others are disregarded, making a double-spend attempt impossible.

The best-known DAG-based protocols are IOTA and Hashgraph. capable of producing 250 TPS. However, as of writing (January 2021) the actual number of TPS is less than 10 because of the relatively low network density; see https://theangle.org.

Permissioned ledgers, such as Azur, Hyperledger Fabric, and Quorum rely on Proof-of-Authority (PoA) or PBFT algorithms; see Brown et al. (2016); Gupta (2017); Hearn (2016). They are scalable but certainly not decentralized. From a practical standpoint, the lack of decentralization might not be a severe.

# ## 11.4.4 Layer2 protocols

Lightning Network, Radien, Network, and Plasma achieve scalability by executing most inter-member transactions off the blockchain infrequently and setting the total counts amongst members on the main blockchain; see Poon and Dryja (2016); Poon and Buterin (2017); Raiden (2016). Figure 11.14 shows a typical setup. Recall that in Section 11.3 we discussed how to use Lightning Network to achieve better privacy.