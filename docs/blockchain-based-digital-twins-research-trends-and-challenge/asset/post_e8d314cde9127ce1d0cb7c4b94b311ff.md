## Ethereum blockchain explorer

The left side of the explorer shows the latest blocks created, and the right side shows the latest transactions. Transaction parameters are listed in Figure 3.5. Let us observe the parameters of one of the blocks in the explorer, as depicted in Figure 3.6. Block Height defines the Block Number, and Block Hash uniquely represents the block. Block Hash is never stored in the same block where it is developed. It is stored in the Block Header as “Previous Block Hash (PBH).” It creates a linkage between the blocks. This is precisely how they are chained. These blocks are linked with the parameter “PBH,” and this process is continuous and forever. That is why it is termed blockchain.

## FIGURE 3.5 Transaction parameters.

Block #16281588

| Overview | Consensus | Comments |
|---|---|---|
| Block Height | 16281588 < > | Block ID |
| Status | Finished | |
| Timestamp | 24 mins ago (Dec-20,2022 06:54:23 AM +UTC) | |
| Proposed On | Block proposed on slot 546870, epoch 170277 In this block |
| Transactions | 102 transactions and 44 external transactions | |
| Fee Recipient | 0xb8f0c2a77a9d55931185f511155114 (MEV Builder: 0xbBaf...a19) in 12 seconds Hash of block Which: would be passed in the next Block Header |
| Block Reward | 0.018364375692021 Ether (+0.015428603790537, -0.01147000936529604) PBH |
| Hash | 0x760053d1e5f2f4a2c5f743a5b5a8492f11f3b8a5a845a855af2290 |
| Parent Hash | 0xd5e236d377c5f43a5b24e4b5a7f6a3b736b373925555211221 | |

## FIGURE 3.6 Block parameters.

Ledger is not unique, but a collective term given to a chain of blocks connected. One can compare the Ledger with the collective term, Humans. Humans are a group of people. Each individual in that group possesses their own identity and features. Similarly, a Ledger is a group of Blocks. Each block is unique in itself.

## 3.2.2 BLOCKCHAIN NETWORK TOPOLOGY ARCHITECTURE

To understand the Blockchain architecture [4], let's study in complete form in a Centralized, Decentralized, and Distributed Network.

## 3.2.1 CENTRALIZED NETWORK ARCHITECTURE

In this architecture, everyone is dependent on a single centralized node. This single node handles data availability, data accessibility, and data upgradability. For example, consider a real-time application such as a Banking organization; in this case of a network, there is no freedom for users to make decisions. Everything is dependent on the single central node. It acts as a single central decision-making point [15] as depicted in Figure 3.7.

## CW1 Sellers List Products on CW1

## CW1 Buyers buy Products from CW1

![](img/5575f2d1bada0bd1c2731bf9be91c7c9_110_0.png)

Figure 3.7 Centralized network architecture.

Let us take another real-time example of an e-commerce web application (CW) such as Flipkart, Amazon, etc., where multiple sellers list their products on the commerce web application CW1. 1000s and 1000s buyers of CW1 associated with the site to purchase products of CW1 sellers. All sellers and buyers of CW1 are dependent on CW1 owners. CW1 owners have complete control over the data displayed on the application. CW1 can only update the value of products, Quantity of Products, etc. CW1 holds the ledger copy. It becomes the critical node in the network and the most vulnerable too.

## 3.2.2.2 DECENTRALIZED NETWORK ARCHITECTURE

In the decentralized environment, CW1 acts as one of the critical nodes. There will be multiple nodes. Let us consider five sellers who are maintaining a copy of the ledger. All of them collaboratively work together in managing the data. As each holds a copy of the ledger, even if one or two nodes go down, we have other nodes that can provide the data, as depicted in Figure 3.8. However, no one can provide the data if CW1 goes down in a centralized network. Consider a situation where if the Bank Server goes down, it notifies its customers that it is down. At that time, no customer could access the account.

So mainly, if the server needs any maintenance time, it's done at night, so customers do not get impacted.

![](img/5575f2d1bada0bd1c2731bf9be91c7c9_111_0.png)

FIGURE 3.8 Decentralized network architecture.

A second important aspect in a decentralized environment is that CW1 is the network initiator but does not have complete control over the network. It acts as one of the entities responsible for ensuring data upgradability. All of them collaboratively work together. Sub-node customers are connected to each seller. One of the seller nodes and customers is depicted in Figure 3.9. Customers are the sub-nodes as they help understanding the complexity of the network. CW1, in this case, loses power and ownership. It is the only source to exchange information.

![](img/5575f2d1bada0bd1c2731bf9be91c7c9_112_0.png)

**FIGURE 3.9.** Seller and customer relations.

## 3.2.2.3 DISTRIBUTED NETWORK ARCHITECTURE

It is a closed compact network. Everyone is connected without depending on anyone absolutely. Anybody can view or transfer the data. Referring to Figure 3.10, white nodes hold a copy of the ledger. Peers are responsible for gathering, sending, and receiving the data. Nodes N1 to N4 are responsible for data availability and storing a copy of the data within them. The same copy of data is available at all four nodes, ensuring trustability, transparency, and security in the network. Multiple nodes storing the same data undoubtedly increase data redundancy, but this is important when constant availability is required.

![](img/5575f2d1bada0bd1c2731bf9be91c7c9_113_0.png)

## 3.3 BLOCKCHAIN-BASED NETWORK APPLICATIONS AND THEIR SOLUTIONS

A question always comes to mind about what additional things blockchain brings to the world apart from existing ones. The answer to this is the utmost level of:

- Trust;
- Transparency;
- Security.

Blockchain is upkilling these three factors. There is no beyond level after this grade. The level of these three factors is unmatched by any other technology. Figure 3.11 is not new but shows the network topology followed by the blockchain environment.

## All The Nodes Manages and Maintains the Same Copy Of Ledger

![](img/5575f2d1bada0bd1c2731bf9be91c7c9_114_0.png)

## FIGURE 3.11 Network topology blockchain environment.

Trust and transparency are straightforward to identify and believe in the blockchain environment [3]. Each node maintains an exact copy of the ledger, which brings trust and transparency among all the nodes in the network. Let us understand the security [5, 6] aspect with the help of an application example of a chain of retailers and distributors network of clothing brands, as shown in Figure 3.12. The whole clothing brand network, which consists of manufacturers, distributors, and retailers, wants to ensure that everything is transparent. A clothing brand is the main initiator of the whole network.

![](img/5575f2d1bada0bd1c2731bf9be91c7c9_114_1.png)

## FIGURE 3.12 Clothing brand – an application of blockchain.

In the case of a centralized use case, the clothing brand would have been a vital player in ensuring data availability and maintenance. In a decentralized environment, all network participants are essential in supply chain management—each node in the network stores a replica of the ledger. The same piece of data as a clothing brand gets redundant at each node in the network. Is there any better transparency than this? Not everybody can see what is happening in the network. Now let us come to the security part of it. Even brands want to tamper with the data, 51% approval is required to change the data. A single node cannot tamper with the data. In Figure 3.12, 12 nodes are there. At least the consent of seven nodes is required to tamper with the data. Again once, to prove the same fact, let us take a centralized environment where a single node works as a Single Point Shared Server. It is easy for hackers to bypass the firewall, so they can easily hack and transfer data. Compare with the blockchain environment. If a hacker wants to transfer the data to a particular block, consent, and changes at all the blocks at different locations must be changed. Nodes are unaware of what other nodes are available in the system, then how can a hacker determine the same?

First and foremost, a hacker needs to find out exactly these different nodes are situated; if not all, but at least 51% of nodes, it should be able to find. Then only tampering would be possible. Multiple blocks allow the fetching of data quickly, preventing the system from being derailed by external hackers [9]. For some reason, let us assume the hacker can tamper with the data at node 1. However, is enough to change the data at all places? Once again, 51% of the sites should have updated data to apply the change at all the locations.

Let us take another drastic situation where hacker finds the location of 51% of nodes. However, one more rule ensures ultimate security in the blockchain environment. Change to be done within the time frame of two continuous additions of blocks, i.e., within Δ time, as depicted in Figure 3.13. Technically, it is an impossible and complex task to achieve. Let us see now
