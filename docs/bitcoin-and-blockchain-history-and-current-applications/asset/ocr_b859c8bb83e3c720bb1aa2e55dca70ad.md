Orderers also maintain a list of channel-building organizations also called as a consortium. This list is kept in orderer system channel. By definition, only the orderer administrator can only change this list and the channel on which it resides.

# 12.3.2.11 Endorsing Policy

Policy on endorsement determines the smallest collection of organizations needed to support a transaction to be legitimate. To endorse, the endorsing peer of an entity needs to run the transaction-related smart contract and sign its result.

When transactions are ordered and broadcasted to the committing peers, they must ensure that each endorsed transaction in the block complies with the endorsing policy defined in the network. If a transaction doesn't satisfy the policy when it is marked as invalid and world state remains unchanged with its values.

# 12.3.2.12 Private Data Collections

In Hyperledger Fabric [1], data can be privatized, i.e., access to particular data can be restricted within the same channel. Fabric calls this as private data collection. Unauthorized entities, as confirmation of the transaction data, will have a hash of private data on the network ledger. It will store this private in a different database called as sideDB [8] as shown in Figure 12.3 which exists in the same peer, if configured.

If a peer is authorized to have a private data collection the private state exists within the peer. This collection is isolated from neighboring peers and only the peer itself has access to it.

# 12.3.3 TRANSACTION FLOW

In this segment, we are going to depict how a transaction is initiated, endorsed, ordered, and committed to the ledger in Hyperledger Fabric network [1].

The transaction flows into five steps.

# Step 1: Transaction Proposal

Transaction life cycle in the Hyperledger Fabric network starts with client applications submitting transaction proposals or, in other words, providing a transaction to endorse peers. A transaction is first invoked by the client application.

![](bbox=[0.22, 0.78, 0.78, 0.9])

FIGURE 12.3 Private data architecture.