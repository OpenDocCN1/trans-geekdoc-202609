
# 3 Distributed ledgers and internet of things

![](img/0a07f1fa1a7ff1beaaa3170e7e172821_133_0.png)

Fig. 3.4: OAuth authorization flow.

contracts as we know them today. It uses new types of transactions to get, delegate, or revoke access to users. Scripting language to express fine-grained and contextual access policies is enveloped inside these transactions. An access token is required to obtain access to a protected resource. A transaction does not deliver the access token until the requester fulfils all access control already described with the model and included in the transaction. As a proof of concept of this idea, two access control models (identity and permitted access control models) have been used in the implementation.

As OAuth is dependent on a trusted third-party authentication provider, an authentication server could block applications thus deny the services provided by the application. DAuth [56] provides an OAuth-like authentication service based on the Ethereum blockchain. A decentralized approach provides trust architecture, and enhances transparency and user control. In DAuth, resource owners (users) are registered with their blockchain addresses in the authentication smart contract. For authorization, the backend application requests the user’s blockchain address from the smart contract and, at the same time, asks the user to sign an authentication request message with the same blockchain account credentials. It then compares the signatures of the user and the smart contract. If they match, the application provides resources to the user.

VaultPoint [57] is a new blockchain-based self-sovereign identity management model that complies with the popular and mature standard of OAuth 2.0. It follows the authorization code grant type of OAuth, which comprises the client authorization, user authentication, and issuance of access tokens. The proposed model could make Web or mobile development easy and reduce users' learning of new authentication and authorization processes, because they are already familiar with OAuth. Using blockchain, the proposed model provides decentralization and integrity of the user and client information. The system is based on the Ethereum blockchain. Three types of smart contracts are used – identification, notification, and client management. The proposed model not only solves the information centralization and the privacy issue of the existing federated ID models governed by major companies, but also provides users with secure accessibility to sovereignty over their identity.

# 3.4 Monetization

Distributed ledger technology can successfully keep trusted records of monetary transactions. If this distributed ledger technology is integrated with IoT, it enables development of new business models. IoT ecosystems are extremely heterogeneous in their applications, technologies and involved stakeholders. A decentralized ecosystem business model, for example, in a smart city, can prioritize the overall benefits of the entire community and the greater ecosystem objectives, of maximizing fragmented values as the profit of the involved individual participants [58].

The IoT business market is multi-faceted. Different entities in the ecosystem can serve multiple sides of the market and play various roles in the business model. Multi-faceted roles of the participants not only affect the business model, they directly improve authentication and authorization in the system, supported by the decentralized approaches. Refer Section 3.3. In an illustrative example in Section 3.6, we demonstrate, to some extent, with a multi-faceted environment. For example, each autonomous machine can act as a service provider or a service consumer.

Several vendors are involved in IoT ecosystem provisioning, including software and hardware vendors, communication and information service providers, and solution providers. They need compensation for their investments in IoT infrastructures, as well as for service provisioning. Monetization of data plays a key role in the IoT ecosystem, data ownership usually accompanied by rich contextual information, which can be monetized. However, this requires efficient and granular control over data. Two business models are prominent in data monetization. First, where the data owner offers their data in exchange for services provided by a third-party provider, and second, where the owner pays to keep his data protected while using the same services.

# 3 Distributed ledgers and internet of things

Monetary and non-monetary aspects of the distributed ledger technology can be combined in the same IoT solution. However, this opens new issues related to the DL network architectures and their interoperability for diverse application requirements. Networks with seemingly similar technological backgrounds may differ greatly in practical implementation, governance, and performance. In decentralized monetization of IoT, one enforces a public, permissionless network for user interfaces. In the other, a permitted consortium network meets the machine interface requirements and reduces the transaction costs.

# 3.5 Integration schemes of internet of things and the distributed ledger

Embedded IoT devices are often characterized by low power consumption for prolonged battery autonomy and are prone to stringent production cost containment because of their mass scale. This limits the computation and storage capabilities of IoT devices and their cryptographic capabilities. For energy efficiency in IoT, WAN (e.g., LoRaWAN, NB-IoT) or PAN (e.g., Bluetooth), wireless communication technologies are optimized for low power operation. IoT devices are, however, not used as full nodes, because the computation and communication overheads do not justify the potential benefits or because full blockchain is simply impossible to be implemented in a constrained device [47].

The processing power of a constrained device limits the use of advanced encryption protocols and limits the blockchain functions that a constrained device can execute. Limited storage makes it impossible to keep the entire chain data or even all block headers in an IoT device.

The communication traffic of a blockchain network node consists of continuous traffic for synchronization with the blockchain network and a sporadic traffic due to transaction submission and event notification. The continuous traffic results from the DL network operation and is not affected by the DApp design and implementation. The only way to alleviate continuous traffic from the IoT device is to withdraw blockchain synchronization protocols and allocate them to a capable gateway. The sporadic traffic is application dependent and can be, at least to some extent, limited by appropriate de.

The communication traffic of a blockchain network node consists of continuous traffic for synchronization with the blockchain network and a sporadic traffic due to transaction submission and event notification. The continuous traffic results from the DL network operation and is not affected by the DApp design and implementation. The only way to alleviate continuous traffic from the IoT device is to withdraw blockchain synchronization protocols and allocate them to a capable gateway. The sporadic traffic is application dependent and can be, at least to some extent, limited by appropriate de. (Wait, the OCR text has a repetition here, I will follow the logical flow).

The sporadic traffic is application dependent and can be, at least to some extent, limited by appropriate de.

IoT devices, for example, unmanned devices without user interfaces, inhibit flexible and secure management of blockchain credentials. This impacts device enrolment and authentication procedures.

# 3.5 Integration schemes of internet of things and the distributed ledger — 115

Absolute decentralization in IoT is, therefore, problematic. We may adjust blockchain network architectures and protocols and device to cope with needed network performance and latency.

### 3.5.1 Distributed ledger networks for internet of things

Distributed ledger networks are discussed in detail in Section 2.3. In IoT, we try to attain performance, scalability, network costs, and privacy. The requirement by IoT devices on a DL network need be different from that of the DeFi application. Such divergent application aspects need to be combined in the same decentralized, both the public and consortium networks (Section 2.3.3) can be applied and cross-chained. In public networks, other consensus algorithms from PoW can be used as PoS or PoA (Section 3.2.1) to reduce transaction costs and improve performance. In private or consortium networks for IoT, a simplified version of the PoW consensus can be found. However, this reduces the decentralization and the inherent trust. Some of the distributed ledger technologies try to combine the financial and IoT performance (and privacy) aspects in one network (e.g., IOTA).

### 3.5.2 Internet of things device architectures for DApps

Table 3.2 summarizes the levels of involvement in the blockchain protocol execution of various entities, that is, network nodes and IoT devices. IoT devices usually act as issuers or requesters. The full or light nodes are not IoT-devices but dedicated entities that provide blockchain capabilities. We can split blockchain functions (e.g., chain synchronization, event filtering, transaction creation, validation, or key-store management) between the IoT devices, device gateways, and full blockchain network nodes. Then, we adapt the off-chain logic to IoT device, accordingly [25].

An IoT device that is a transaction issuer is capable of building and signing a valid blockchain transaction. The issuer has a valid blockchain identity. It needs access to the key-store to properly sign the issued transaction. Access to the key store requires reliable authentication in the device and can impose hardware security risks. After a transaction is built, it is submitted to the blockchain network via API in one of the network nodes.
