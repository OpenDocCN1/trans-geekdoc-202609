Yan, J., Meng, Y., Lu, L., & Li, L. (2017). Industrial big data in an industry 4.0 environment: Challenges, schemes, and applications for predictive maintenance. IEEE Access : Practical Innovations, Open Solutions, 5, 23484–23491. doi:10.1109/ACCESS.2017.2765544

Zeng, S. W. (1997). Discussion on maintenance strategy, policy and corresponding maintenance systems in manufacturing. Reliability Engineering & System Safety, 55(2), 151–162. doi:10.1016/S0951-8320(96)00004-X

Zhang, Y., Kasahara, S., Shen, Y., Jiang, X., & Wan, J. (2018). Smart contract-based access control for the internet of things. IEEE Internet of Things Journal, 1–1. doi:10.1109/JIOT.2018.2847705

Zimmermann, L., Scholz, A., Tahoori, M. B., Aghassi-Hagmann, J., & Sikora, A. (2019). Design and evaluation of a printed analog-based differential physical unclonable function. IEEE Transactions on Very Large-Scale Integration (VLSI). Systems, 27(11), 2498–2510.

# KEY TERMS AND DEFINITIONS

Chaincode: Smart Contracts are called Chaincode in Hyperledger Fabric. These are small computer programs that are executed in a distributed manner and represent a digitalised version of previously paper-based contracts. In Hyperledger Fabric, smart contracts can be programmed in Go, Java or Node. js and thus provide ease of use for the programmer. The process of executing the smart contracts is called a transaction.

Channel: A Hyperledger Fabric Channel provides private and confidential communication and represents a blockchain. Transactions are executed on a channel which are stored in the channel’s ledger. Channels are used to hide certain information from specific Organizations.

ESR: This Epson T3-401S SCARA robot - a versatile entry-level robot solution for production lines.

Hyperledger Fabric: Hyperledger Fabric is a permissioned blockchain infrastructure, originally contributed by IBM and Digital Asset, providing a modular architecture with a delineation of roles between the nodes in the infrastructure, execution of Smart Contracts (called “chaincode” in Fabric) and configurable consensus and membership services.

Membership Service Provider: The Membership Service Provider (MSP) issues and maintains the identities of all nodes in the Hyperledger Fabric system. Issuing and maintaining the identities is handled via standard PKI methods based on digital signatures. Nodes take up to one of three roles: Client (executing the smart contract), Peers (maintaining a copy of the blockchain and validation of the transaction), and Orderer (establishing the order of all transactions).

Orderer: This is a node type in Hyperledger Fabric. A group of Orderers form the ordering service, responsible for establishing the correct order of all transactions. In the process of ordering consensus (agreement) of the transactions is achieved. Hyperledger Fabric features three consensus implementations: Solo (for development purposes), Kafka (a crash fault tolerant consensus implementation), and Raft (a crash fault tolerant consensus algorithm).

Organization: Hyperledger Fabric uses Organizations to structure the stakeholders inside the network. Every user is part of an Organization which determines his access rights. Each Organization forms a trust domain, such that a node with the Organization trusts all node within the Organization but no node of another Organization. Each Organization issues the identities for its own members.