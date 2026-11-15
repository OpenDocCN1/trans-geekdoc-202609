Ethereum is a secure decentralised ledger that is optimized for transparency, hence it is difficult to share secrets on the platform (Ethereum, 2020). The main components of Ethereum are Ethereum Virtual Machine (EVM), miner, block, transaction, consensus algorithm, account, smart contract, mining, Ether, and gas (Modi, 2018). These are illustrated in Figure. 2. The notion of private transactions and public transactions are introduced in Quorum (Quorum, 2020) which extends the transaction model of Ethereum to include an optional privateFor parameter and a new IsPrivate method to deal with such transactions.

# Figure 2. Components of Ethereum

![](bbox=[0.22, 0.295, 0.8, 0.48])

On the other hand, Hyperledger Fabric introduces private data collections, which allow a defined subset of organizations on a channel the ability to endorse, commit, or query the private data (Hyperledger2, 2020). The private data is sent peer-to-peer via gossip protocol to only the organisations authorised to see it. The ordering service is not involved here and the orderer does not see the private data. The hash of the private data is endorsed, ordered, and written to the ledgers of every peer on the channel as in Figure. 3 (Hyperledger2, 2020).

# Figure 3. Private Data Store in Hyperledger Fabric

![](bbox=[0.22, 0.685, 0.8, 0.91])