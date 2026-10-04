
# Blockchain for Internet of Vehicles Security

185 based on its score. The reputation algorithm consists of a reward mechanism, and the score of the vehicle is increased or decreased depending on the vehicle behavior.

Shrestha et al. (2019) proposed a blockchain-based scheme to secure critical event messages distribution in VANET. They used a public blockchain to secure trustworthy vehicles and messages exchanged in a particular geographical location (local., blockchain for each). First, the vehicle sends an initiation message containing its public key to the RSU. The latter sends an identity to the vehicle, which sends back the session identity. The RSU authenticates the vehicle and publishes the location certificate signed by its private key. Then, the legitimate RSU creates a genesis block (i.e., first block of blockchain), and all vehicles download it. New blocks are mined by vehicles that have high trust level and computing power. Each vehicle independently checks the message and stores it in its message pool if it is trustworthy. Then, the event message is broadcasted within the network. The miner creates a new block for trustworthy event message using the PoW algorithm. Each vehicle updates the public blockchain by adding the new block. To reduce delay of block generation and propagation, the authors presented a new architecture using edge cloud computing.

To secure announcement messages in the IoV, the authors in Zhang et al. (2019) proposed a blockchain-based scheme. They used private and auxiliary blockchain for each region (country). The vehicle uses an asymmetric key pair and sends its public key with its identity to the traffic management authority. The latter sends its public key in the private blockchain. Moreover, the vehicle generates a pool of short-term asymmetric keys, blinds the public key by using blind signature scheme, and signs the blinded short-term public keys. These are sent to the issuer that verifies the signature and generates a session identity to trace the real identity of the vehicle. The public key and session identity are stored in the auxiliary blockchain. Each vehicle signs the announcement message by its short-term private keys based on multisignature, and and then, it broadcasts the signed message within the network. If the signed message is trustworthy, it will be stored in the auxiliary blockchain of the region and the vehicle will be rewarded with Vcoin. Otherwise, the vehicle will be traced to pay a penalty using Vcoin, and its public key will be blacklisted. The proposed scheme achieves message authenticity, vehicle privacy, and reliable message distribution.

In Kang et al. (2019), the authors used blockchain to provide secure data sharing in the IoV. They proposed an enhanced Delegated Proof of Stake (DPoS) scheme with secure miner selection and verification to address collision attacks in the IoV. The miners are selected using reputation-based voting. They participate in block verification by using contract to prevent internal collisions. The proposed scheme improves the detection rate of malicious miners and decreases miners' collisions. Table 14 blockchain-based solutions.

## 8.4.8 CLASSICAL SOLUTIONS VS. BLOCKCHAIN-BASED SOLUTIONS

In this subsection, we classify and address the cost and limitations of the classical and blockchain-based solutions that have been proposed to secure the IoV. This classification, according to types of attack, security requirements, and mechanisms used, is illustrated in Table 8.4.

Table 8.3

# TABLE 8.3 Classification of Blockchain-Based Solutions

| References | Communication Types | Blockchain Content | Blockchain Type | Consensus Algorithm | Participant | Applications |
|---|---|---|---|---|---|---|
| Hossain, Hassan, and Zawood (2017) | V2X | Story of occurred events | Public | — | LEA and investigator | Investigation |
| van der Heijden, et al. (2017) | V2X | Messages, revocations | Private | — | Cluster of vehicles and RSUS | Cross-border vehicular networks |
| Baoygin, et al. (2018) | V2X | Nodes' messages | Public | PoW | — | Routing |
| Sharma and Park (2018) | V2X | IoT services requests | Public | Memory-hardened | Controller nodes, specific vehicles | Free application |
| Singh and Shiho (2018) | V2X | Local blockchain: messages, messagebox; Main blockchain: IVTP, transactions | — | PoW | Vehicles | Intersection deadlock |
| Arora and Sumit Kumar (2018) | V2X | Authentication information | Private | — | RA | Free application |
| Zhagain, et al. (2018) | V2X | Certificate | Private | PoW | CA, vehicles | Free application |
| — | V2I | Revoked keys | Private | PoW | — | Motivating vehicles to forward announcement |
| Li, et al. (2018) | V2X | Vehicles' announcement, vehicles' coins | Public | PRFT | RSUs, official public vehicles | (Continued) |

186 Blockchain for Cybersecurity and Privacy

# TABLE 8.3 (Continued)
Classification of Blockchain-Based Solutions

| References | Communication Types | Blockchain Content | Blockchain Type | Consensus Algorithm | Participant | Applications |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Ktaani, Abbasi, and Guera (2018) | V2V, V2R | Validated messages | Public | PoE | RSUs | Calculating vehicles' reputation |
| Sharma (2019) | V2X | Local Global | - | PoE | Vehicles | Free application |
| Zhang and Chen (2019) | V2X, V2V, V2R, R2R | Messages | Public | PBFT | RSUs | Safety warning |
| Sheshtha, et al. (2019) | V2V, V2I | Public | Node trustworthiness, trustworthiness | PoE | Full vehicles with high speed and high computing power | Critical events (e.g., traffic jam, accident) |
| Zhang, et al. (2019) | V2X, V2V, V2I | - | Parent BC: identities, public keys, Auxiliary BC: session identities, public keys, signed message identities (local) | PBFT | RSUs | Announcement icy road, flooding |
| Kang, et al. (2019) | V2V, V2I | Public | Data-sharing records, reputation opinions | DPoS | Reputation-based voting (RSU's) | Intelligent transportation system |

# Blockchain for Cybersecurity and Privacy
(Continued)

# Classical vs. Blockchain-Based Security Solutions

| References | Blockchain-Based | Attack Model | Security Requirement | Mechanism Used | Cost | Limitations |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Liu, et al. (2016) | No | MIM attack | Confidentiality | Access policy | High computation, low storage | Lack of privacy and vehicles authentication |
| Hossainain, and Zaowar (2017) | No | Eavesdropping | Integrity | Eavesdropping and verification | Low communication, high latency | Lack of latency |
| van der Heides, et al. (2017) | Yes | Malware injection | Availability | Misbehavior detection algorithms | Optimized with clusters and local blockchain | Stability of clusters to provide consensus |
| Bogyoski, et al. (2018) | Yes | Sybil attack | Authentication | Deleting outdated information by hashing the whole chain to deal with | Medium bandwidth, optimized latency | DoS and Sybil attack possibility |
| Sharma and Park (2018) | Yes | Message tampering | Integrity | Digital signature to ensure | Optimized bandwidth usage | Lack of privacy |
| Li, et al. (2018) | Yes | MIM attack | Confidentiality | Consensus algorithm, Hash chain, | High computation time and storage capacity |
| Kchaui, Abassi, and Guemaira (2018) | Yes | DoS attack | Integrity, Non-repudiation | Unlocking script | High latency | High latency |

TABLE 8.4

* With*

211
# Blockchain for Internet of Vehicles Security

| References | Blockchain-Based | Attack Model | Security Requirement | Mechanism Used | Cost | Limitations |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Singh and Shiho (2018) | Yes | Blackhole | Trust | IVTP | Low latency | Trustworthiness of vehicles just by mining blocks and earning IVTP |
| | | Bogus attack | Privacy | | | Test in one case of communication deadlock |
| | | Illusion attack | Authentication | Branching algorithm | | |
| | | Tracking attack | Availability | | | |
| Jeneda and Anita (2018) | No | Sybil attack | Authentication | | | |
| Wan and Zhang (2018) | | MM attack | Availability | Lagrange interpolation method | Low latency | Insecure private key distribution |
| | | Eavesdropping | Confidentiality | Algebraic and IBS signatures | Low computation, medium storage | Lack of privacy |
| Limbasya and Das (2018) | No | Tracking attack | Integrity | | Practicing private keys for different vehicles | Low latency, medium computation, medium storage | |
| | | Sybil attack | Confidentiality | Including the time stamp in the computation of different vehicles | | Encryption and decryption | Confidentiality of the group key |
| Arav and Sumit (2018) | Yes | Tracking attack | Privacy | | Pre-identification (PIDs) | | Multiple group key |
| | | Sybil attack | Authentication | | Identification public ledger (B) | | Reputation update |
| Zhaojun et al. (2018) | Yes | Sybil attack | Privacy | | Public keys as identity | High latency of certificate |
| | | Blackhole attack | Authentication | | Reputation management algorithm | Certificates certificate |
