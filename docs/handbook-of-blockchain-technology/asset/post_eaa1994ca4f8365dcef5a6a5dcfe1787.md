
![](img/ab11be88faa3a9baf1bf1607f21e9805_359_0.png)

*Figure 19.1* A negotiation scenario between two NPs for resource provision and QoS guarantee

characterized by self-manageability and self-orchestration in order to rapidly adapt to changes and applications’ demands. Researchers are currently investigating the implementation of the ZSM framework in networks beyond 5G, although they point out various security issues that should be addressed. Nevertheless, blockchain technology can be the antidote to these security threats.

## 19.2.1 Centralized Vs Decentralized Blockchain-enabled Approaches

In both inter- and intra-administrative domain resource negotiation and allocation, two main options exist: centralized and decentralized (Xevgenis et al., 2020). Traditional centralized approaches have been thoroughly studied and used in many use cases, while decentralized solutions are becoming extremely popular in the technological arena. Centralized approaches (Agarwal et al., 2019; Samdanis et al., 2016; Taleb et al., 2019) have the advantage that they can achieve high performance due to the availability of information regarding the status of the whole network/domain. However, this comes with certain drawbacks: the centralized nature of the brokering mechanism automatically labels it as a Single Point of Failure (SPoF). If this centralized entity is out of service, then the operation of the whole system is disrupted. In addition, communication among the entities participating in the resource brokering should be secured in order to avoid data alteration (which would cause service unavailability).

On the other hand, by adopting a decentralized solution, such as blockchain, the different resource providers would be members of the DLT network hosting one (or more) nodes, which obviates the SPoF attack. Every node of the network keeps a copy of the ledger and participates in the consensus process for validating the information registered/stored in the form of transactions. The consensus mechanism used in blockchain discourages any node from performing malicious actions and validating false transactions (Christodoulou et al., 2020). In summary, the design and development of a blockchain-based solution for network management attracts the interest of NPs as it:

- Assures transaction security. The resource management process is implemented in the form of a transaction.
- Harnesses the benefits of blockchain technology, which introduces characteristics such as data integrity and immutability, as well as increased traceability. Therefore, the non-repudiation problem is solved as the participants are able to search the transactions written in the ledger, if necessary.
- Implements resource management tasks in the form of SCs, which are executed automatically when needed. This guarantees the security of management tasks and improves the dynamicity of resource management processes.

Table 19.1 summarizes the main benefits of each of the two approaches described above.

| Attributes | Centralized Resource Allocation Approaches Features | Decentralized Blockchain-based Resource Allocation Approaches Features |
|---|---|---|
| Performance | High performance | Low performance |
| SPoF | Yes | No |
| Data security | Low data security – No consensus process | High data security – Decentralized consensus |
| Data immutability | No | Yes |
| Scalability | Scalability is supported | Scalability may be an issue |
| Code vulnerability – Code immutability | Use of traditional code which may present vulnerabilities to malicious attacks | Use of SCs which are immutable pieces of code (SLA implementation) |

## 19.2.2 Pros and Cons of Blockchain Technology

Although blockchain could prove to be a powerful tool to overcome and even eliminate security issues, we should keep in mind that this technology is not a panacea. Hence, the consequences of using this technology should be considered when designing a solution. Therefore, we highlight the main advantages and disadvantages of this promising technology, which may revolutionize the way NGNs are managed and, at the same time, substantially increase the security level. The main advantages of this technology are summarized as follows:

- The presence of a trusted third party is not required: The active participants of the network, which host at least one node, have full control of the network’s operation and growth, as they participate in the consensus process to create and validate new blocks (Patrikakis et al., 2023; Xevgenis, 2023).
- The SPoF problem is solved: The distributed nature of blockchain automatically eliminates the SPoF problem. In cases when a node is unavailable for several reasons (maintenance, attack, etc.), the operation of the network is undisturbed (Patrikakis et al., 2023; Xevgenis, 2023).
- Assurance of data integrity and immutability: The use of cryptography when the transactions are stored and validated in a block, and the strong cryptographic links used for the chaining of blocks, leverages the security of the information. Once the information is stored in the ledger, it cannot be erased or altered (Patrikakis et al., 2023; Xevgenis, 2023).
- Increased transparency: The information is stored in the ledger of the blockchain in the form of a transaction and is available to the participants. It should be mentioned that transactions contain the information and the blockchain network addresses of the parties that implement this transaction. There is no information on the network regarding the correspondence of a physical identity to a network address (Patrikakis et al., 2023; Xevgenis, 2023).
- Credibility: The rules of a blockchain network cannot be altered by one entity. Changes to the rules of the network are proposed by the participants. If the majority of participants vote in favor of a change, then the change is applied in the network. As the number of participants grows, so does the credibility of the system (Patrikakis et al., 2023; Xevgenis, 2023).
- **Traceability:** The increased transparency of data, the integrity, and immutability of the information automatically increases the traceability of a transaction written in the ledger (Patrikakis et al., 2023; Xevgenis, 2023).
- **Trust:** The characteristics of data integrity and immutability, data transparency and traceability, as well as the existence of the consensus mechanism, increase the user’s feeling of trust towards the blockchain network (Patrikakis et al., 2023; Xevgenis, 2023).

The main disadvantages of blockchain technology are as follows:

- **Scalability:** Information stored in the ledger cannot be deleted, which means that the chain is growing as more and more transactions are validated. Also, the blockchain network grows as new nodes enter, which should mean a copy of the ledger should be synced with other participants. Therefore, the scalability of the system is a major issue for this technology (Cunha et al., 2021; Patrikakis et al., 2023; Xevgenis, 2023).
- **Security:** The private keys of the user are used for the creation of a blockchain address. This means that if the keys of the user are lost or stolen, the content of his/her account is lost (Patrikakis et al., 2023; Xevgenis, 2023).
- **Speed of transactions:** The time it takes for a transaction to be validated plays a crucial role when we examine the adoption of blockchain technology for a time-critical use case. Therefore, the selection of the proper DLT mechanism for a time-sensitive application is a very important task. Already, many DLT systems offer high speed transactions to satisfy demanding scenarios (Patrikakis et al., 2023; Xevgenis, 2023).

In the following sections, several published works are discussed that focus on the use of blockchain technology in NGNs. More specifically, we divide these works into three discrete categories in order to examine: the use of blockchain in resource management; the use of blockchain in NS; and the use of blockchain technology for secure ZSM-enabled network management. The goal of this survey is to present how this hyped technology can be used in NGNs to efficiently tackle the challenges of NGNs. The plethora of published works highlights the growing interest of academia regarding the use of DLTs in NGNs.

## 19.3 BLOCKCHAIN FOR RESOURCE MANAGEMENT IN NGN

This section of the chapter presents research works that focus on the adoption of blockchain technology for resource management in NGNs. The resource management process includes the management of network services implemented in the form of VNFs over virtualized infrastructure (i.e., resources in the form of VMs or containers) located at the core or at the edge of the network (i.e., edge computing infrastructure), as well as the management of spectrum used for the communication of several network services. The studies presented below aim to take advantage of blockchain’s main characteristics to ensure the high performance of the network infrastructure, while at the same time highlighting crucial decision points regarding the design of a blockchain-based solution for resource management.

Herbaut and Negru (2017) present a model for collaborative blockchain-based video delivery. This work studies how the combination of a SC stored in a blockchain and network service chain can be used to support collaboration schemes. The main contribution of this study
