# 9.3.3.1.4 Ease of Access

Every member of the network keeps an exact copy of the blockchain on their personal computer. If patients want to monitor their health, they can view it on a personal computer or a mobile device. Physicians can also view the records uploaded by another physician [27].

# 9.3.3.1.5 Interoperability

An implementation of a secure HIE will enable different healthcare providers to exchange data among themselves. This can help in quick diagnosis and treatment of diseases. Such a system can also enable physicians discussing among themselves effective treatment plans for their patients. Thus, HIE can help to achieve interoperability and better communication between different healthcare providers [28].

# 9.3.2 Architecture

The proposed architecture can be divided into three subsystems: user-friendly frontend–BlockHealth application, Tendermint, and backend storage systems.
As shown in Figure 9.1, our focus is on developing a decentralized distributed application that can ensure the origin and authenticity of health records stored in the blockchain. The decentralized distributed stack architecture ensures that even if one node is lost, and never, no node can make changes in data without the consensus of other nodes. All the transactions are transparent to all users in the private blockchain network. Since BigchainDB is BFT at a time, one-third of the nodes in the network can fail, and still, the system will be running without any issues.

The first layer in Figure 9.1. BlockHealth web application, provides a user-friendly interface to upload the health documents and store them in the IPFS and then in blockchain. Tendermint acts as an interface to broadcast transactions to all nodes in the private network. It is Tendermint that initiates the consensus process that determines whether a transaction is valid. If the transaction is valid, it will be added to the network; else, it is not.

![](bbox=[0.218, 0.668, 0.781, 0.883])

FIGURE 9.1 Decentralized stack architecture.