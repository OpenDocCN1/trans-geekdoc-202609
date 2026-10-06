# Blockchain and Distributed Ledgers: Mathematics, Technology, Economics

Table 11.1 Approaches to blockchain scalability. Source: Zhou et al. (2020).
| Layer | Category | Protocol |
| :--- | :--- | :--- |
| Layer0 | Rationalizing network utilization | bloXRoute, El, Kadcat, Velocity |
| Layer1 | Block storage and TXs handling | Bitcoin Cash, Compact block relay, CUB, Jidar, SegWit, Txm |
| | Transactions sharding | Elastico, Monoxide, OmniLedger, RapidChain, Zilliqa |
| | Changing consensus algorithm | Algorithm, Inclusive, Ouroboros, Snow white |
| | Changing topology to DAG | Bytedall, Conflux, Dagcoin, Hedera Hashgraph, Inclusive, IOTA, PHANTOM, SPECTRE |
| | Permissioning | Corda, Hyperledger Fabric |
| Layer2 | Cross-chain | Cosmos, Polkadot |
| | Off-chain | Arbitrum, Truebit DMC, Lightning Network, Raiden Network, Sprites liquidity.network, Pegged Sidechain, Plasma |
| | Payment channel | |

The Erlay protocol proposes reducing the redundancy by sharing transaction IDs and their sketches; see Naumenko et al. (2019). A sketch is a compact representation of all the transactions accepted by a particular node since the last reconciliation. First, the nodes share IDs, but only with eight peers or less, regardless of their overall connectivity. Second, they request sketches from their peers. A node processes the sketch it receives, identifies new transactions, and requests them from the peers. Such a design enables to materially reduce the amount of inter-node traffic, while consuming a fraction of the conventional method’s bandwidth.

# 11.4.3 Layer1 protocols

Bitcoin Cash, Bitcoin SV, and Litecoin, have implemented changes in the original Bitcoin protocol, allowing a substantial increase in the block size. This increase is very consequential since it results in a proportional increase in the number of transactions recorded in a single block. Normal blocks further decentralization of the protocol since they they impose heavy demands on storage capabilities of the full nodes.

The idea of sharding is straightforward, but implementation is anything but. Sharding is a well-known technology initially designed to optimize large commercial databases. The idea is to divide the data fragments stored at separate servers, reducing the pressure of a centralized server, improving the search performance, and increasing the database’s storage capacity. When applied to a distributed ledger, sharding produces smaller sub-ledgers, or shards, each containing a fraction of the nodes. Transactions are assigned to different shards, which process them in parallel, which dramatically increasing the overall throughput.