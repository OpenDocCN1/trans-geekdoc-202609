# Architecture, Security, and Privacy for Blockchain

# Security

Security means providing the access control, confidentiality, integrity, authentication, availability, and non-repudiation of services. Miners whose computing power is below 25% of the network's total power are incentivized. Therefore, they are lured to use small blocks and extend the longest and heaviest chains. The honest users follow the heaviest chain while selfish users may follow any. To increase their revenue, miners prefer to follow the longest blockchain fork. Bitcoins are more flexible in network optimal conditions, staying zero attacks in zero latency. Secure multiparty computation, attribute-based mechanisms, and non-interactive bitcoins are more flexible in zero-knowledge proof. Blockchain provides very good authentication for access control with the feat of hashing [47]. Some of the security issues are as follows:

+   - **Wallet security**: Wallets need to be protected from the attacks to get the private key.
- **Censorship resistance**: To limit the power of the lead miner to a single epoch.
- **Resilience to mining power variation**: They are adjustable to different mining power variations.
- **Forks**: Making of other blockchains, which wastes the efforts of honest nodes.
- **Double-spending**: Nodes try to transfer the same Bitcoin to more than one node.

# Classification of Attacks

Attacks compromise the security of the system. Attacks are classified into several different categories depending on where they pose the threats [4, 20]: identity based (replay, impersonation, Sybil), manipulation (Eclipse, transaction malleability, time jamming, quantum, reputation), vulnerability in service (race, DDoS, double-spending, finney, vector76, collision; malware), application vulnerability (use case design flow, coding vector) [8].

> A. Bitcoin proof of work attacks based on consensus protocol:

+   i. **Selfish mining attack**: Cheating to create rewards.
ii. **DAO attack**: It is exploited by re-entering the contaminated smart contracts.
iii. **BGP hijacking attack**: Intercepts the miners and reroutes the cryptocurrency so can be stolen.
iv. **Eclipse attack**: It is used to separate the victim from the rest of the network.
vv. **Balance attack**: It disrupts the communication of low-power miners.
vi. **Double-spending or race attack**: The seller or merchant is targeted, and the same Bitcoins are sent in rapid succession. They are countered by putting observers in between them.