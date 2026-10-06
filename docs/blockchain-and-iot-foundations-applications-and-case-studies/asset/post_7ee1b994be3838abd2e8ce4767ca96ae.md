
# 16

# Blockchain and IoT

![](img/7237166d8c6f79ea99cc6e305e5ec1f5_28_0.png)

FIGURE 1.11 Privacy preserving terminology.

Profile indistinguishability refers to the inability of adversaries to reconstruct a user's profile (set of addresses or transactions of Bitcoin coins) in a public ledger (Figure.11).

# Techniques to Enhance the Privacy and Anonymity of Bitcoin

- i. **Coinbase**: Transactions require multi-signatures. Anonymity level varies.
- ii. **Coin shuffle**: It is used for coordinating Coinbase transactions via crypto-graphic protocols and lower anonymity levels.
- iii. **Xim**: Multiround partnering mixing at a higher mixing rate.
- iv. **Coin Shuffle and DeMix**: Optimal mixing is done to improve the anonymity of cryptocurrency and DDoS may occur. It does not use a third party and less risky, but it is less resistant to DoS attacks.
- v. **Value Shuffle**: Coin Shuffle-based to achieve unlinkability and better privacy.
- vi. **Dandelion**: Policy to avoid the deinonymization of Bitcoin.
- vii. **Secure Coin**: It helps to understand the advantages of centralized and decentralized-mixing, and also suspected coin theft.
- viii. **CoinParty**.
- ix. **Mix Coin**: Mixing is done by a third party. Partial theft resistance and unlinkability.
- nx. **Blind Coin**: Blind signatures are used for anonymity and provide partial theft protection.
- xi. **Tumble Bit**: Payments conducted via untrusted intermediaries and require double back-to-back transactions.

# Architecture, Security, and Privacy for Blockchain

# Security

Security means providing the access control, confidentiality, integrity, authentication, availability, and non-repudiation of services. Miners whose computing power is below 25% of the network's total power are incentivized. Therefore, they are lured to use small blocks and extend the longest and heaviest chains. The honest users follow the heaviest chain while selfish users may follow any. To increase their revenue, miners prefer to follow the longest blockchain fork. Bitcoins are more flexible in network optimal conditions, staying zero attacks in zero latency. Secure multiparty computation, attribute-based mechanisms, and non-interactive bitcoins are more flexible in zero-knowledge proof. Blockchain provides very good authentication for access control with the feat of hashing [47]. Some of the security issues are as follows:

- **Wallet security**: Wallets need to be protected from the attacks to get the private key.
- **Censorship resistance**: To limit the power of the lead miner to a single epoch.
- **Resilience to mining power variation**: They are adjustable to different mining power variations.
- **Forks**: Making of other blockchains, which wastes the efforts of honest nodes.
- **Double-spending**: Nodes try to transfer the same Bitcoin to more than one node.

# Classification of Attacks

Attacks compromise the security of the system. Attacks are classified into several different categories depending on where they pose the threats [4, 20]: identity based (replay, impersonation, Sybil), manipulation (Eclipse, transaction malleability, time jamming, quantum, reputation), vulnerability in service (race, DDoS, double-spending, finney, vector76, collision; malware), application vulnerability (use case design flow, coding vector) [8].

> A. Bitcoin proof of work attacks based on consensus protocol:

- i. **Selfish mining attack**: Cheating to create rewards.
- ii. **DAO attack**: It is exploited by re-entering the contaminated smart contracts.
- iii. **BGP hijacking attack**: Intercepts the miners and reroutes the cryptocurrency so can be stolen.
- iv. **Eclipse attack**: It is used to separate the victim from the rest of the network.
- v. **Balance attack**: It disrupts the communication of low-power miners.
- vi. **Double-spending or race attack**: The seller or merchant is targeted, and the same Bitcoins are sent in rapid succession. They are countered by putting observers in between them.
- vii. **Finney attack**: Sellers and merchants are affected. A faulty miner sends a pre-mined block for double-spending. It can be countered by multiple confirmations.
- viii. **Brute force attack**: To secretly mine a blockchain and it is controlled by using the observers.
- ix. **Vector 76 or one confirmation attack**: It is a fusion of double-spending fin fin attacks and again it can be avoided by using an observer.
- x. **More than 50% hash power or gold finger attack**: It manages adversaries with to more than 50% hash rate and it can also be controlled by inserting-observers.
- xi. **Block discarding or selfish mining**: It misuses the fork feature to unfairly gain rewards. It can be controlled by the zero block technique and time-stamp base mechanisms.
- xii. **Block withholding**: It involves only PpoW. It can be avoided by involving only known and trusted miners.
- xiii. **Fork and withholding attack**: It corrects the bad effects of block withholding-selfish mining. It is a node fence, therefore it is more dangerous.

B. Misbehavior targeting Bitcoins as follows:

- i. **Bribery attack**: Some nodes brute to get advantages for mining, and they affect the seller and merchant. It can be countered by increasing the reward of honest miners.
- ii. **Refund attack**: It is a refund method that is exploited by adversaries for payments, and it can be managed by publicly verifiable evidence.
- iii. **Punitive and feather attackers**: A miner blacklists transactions of other miners. It affects the users and are difficult to control.
- iv. **Transaction malleability**: An attacker speeds the ID of a transaction.
- v. **Time jacking**: An attacker speeds up the miner's clock. It can be prevented by restricting acceptance time ranges.
- vi. **DDoS**: An attack in groups to exhaust the network resources, and it can be countered by authorization protocols.
- vii. **Sybil**: Multiple identities are used by the attacker. It can be countered by mutual mixing protocols.
- viii. **Eclipse or not split**: The attacker monopolizes network connections. Here attackers try to isolate the target from the network. It can be controlled by disabling the connections.
- ix. **Tampering**: A delay is caused in transactions. It is managed by improving the block management.
- x. **Routing attacks**: Some nodes are skipped from the network. It is controlled by increasing the diversity connections.
- xi. **Deanonymization**: Wallets are linked with IP addresses. It affects users only. It can be countered by mixing the Coin and Join Shuffle services.

# Solutions to Bitcoin Attacks

These are some solutions to prevent the attacks:

# Architecture, Security, and Privacy for Blockchain

- i. **Double-spending**: Confirmations are received from observers. For detecting the attacks, non-equivocation contracts are employed to lock the payer.
- ii. **Forking and pooling**: This is backward compatible means miner gets many forks of the same length, and will forward them to all peers. Other techniques use timestamps to check the recency.
- iii. **Securing Wallets**: A wallet contains the private and public keys for each account, which is encrypted by AES, CBC, SHA, etc. Another wallet called a cold wallet is kept unconnected to the network. Therefore, the bank cannot access this wallet.
- iv. **Securing Bitcoin networks**: It helps secure networks from DDoS attacks, refund attacks, and transmission malleability.
- v. **Defense against anonymity, peer-to-peer network**: Certificateless authentication, convergence encryption, counterresistance to attacks, and blockchain-based distributed key architecture are proposed to be employed.

# Risks to Blockchains

Various dangers or threats to Bitcoins are considered here [3] (Table 1.5). They are vulnerable to 51% attacks. It results in many attacks as opposite transactions, reverse ordering, private mining and confirmation of ordinary transactions. Private key security, referred to as identification, is dealt with by third party. Some criminal activities can be managed like ransomware, underground marketplace, money laundering. Transactions are traceable and their order of execution need to be recorded in a defense storage. Transaction privacy is not secured by smart contracts risking information leakage. In under-priced operations, the attacker launches attacks that consume a lot of resources. Marketplace risk is due to the versions inside the foreign exchange quotes.

# SUSTAINABILITY AND POTENTIAL FAILURES

Foreign money is safe from the authorities' regulations for business and purchases. However, there are some gray areas concerning restrictions using Bitcoin because of its decentralization coverage and technical failures. Some countries have regulated Bitcoin by recognizing or not longer backing it. Many federal governments have a monopoly on issuing currencies.