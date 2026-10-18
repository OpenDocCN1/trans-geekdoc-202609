
## Table 9.1 Blockchain evolution phases, characteristics and examples

| Year | Phase | Short Description | Characteristics | Example |
|---|---|---|---|---|
| 2009 | Blockchain 1.0 | Blockchain genesis | Blockchain is monolithic with application, consensus, and network layers tightly coupled. Its main focus is to support transactions related to digital currency. | - Bitcoin |
| 2015 | Blockchain 2.0 | Smart contracts birth | The application layer is separated from the other two layers. This increases programmability and opens new avenues for blockchain applications. | - Ethereum |
| 2017 | Blockchain 3.0 | The dApps era | New innovative decentralized solutions and use cases make their appearance. | - Ethereum based dApps<br>- Augur<br>- MakerDAO<br>- Opensea<br>- Sovrin network |
| 2019 | Blockchain 4.0 | Scalability and interoperability | - Tokenization and incentive mechanisms<br>- Decentralized identity<br>- Decentralized governance<br>- Decentralized Autonomous Organizations (DAOs)<br>- Cross chain communication<br>- Layer 2 solutions on top of Layer 1 blockchains<br>- Standardized protocols<br>- Decentralized oracles<br>- Interoperability standards<br>- Consensus mechanism optimizations<br>- Off chain processing | - Cosmos<br>- Chainlink<br>- Polkadot |

| Year | Phase | Short Description | Characteristics | Example |
|---|---|---|---|---|
| 2019 | Blockchain 5.0 | Web 3.0 revolution | - Decentralization of data ownership<br>- Decentralized Exchanges (DEXs)<br>- Decentralized Finance (DeFi)<br>- Lending protocols<br>- NFTs rise<br>- Game Finance (GameFi)<br>- Play-to-Earn (P2E)<br>- Decentralized Metaverse | - Digital assets<br>- NFT collections<br>- Uniswap, Sushiswap<br>- Decentraland<br>- Virtual real estate |
| 2020 | Blockchain 6.0 | The rise of CBDCs | - Blockchain technology is adopted by many Central banks<br>- More than 50% of all Central banks have investigated and experimented with CBDCs<br>- CBDC interoperability is considered a challenge<br>- Serving the unbanked is a key target, especially for less developed countries<br>- Integration with the traditional financial system | - Bahamas Sand Dollar (October 2020)<br>- Nigerian eNaira (October 2021)<br>- Many CBDC projects in the pilot phase since 2020 |

blockchain will consume a big portion of the world’s total energy production. This issue is fast becoming one of the most critical challenges faced by this network (Hasib Anwar, 2018).

Cost and Efficiency: The swift and dependable execution of peer-to-peer transactions via blockchain protocols is accompanied by a considerable cumulative cost, which is more substantial for certain types of blockchains compared to others. This inefficiency occurs because, in an effort to be the first to find a solution, each node executes the same functions as any other node on its own copy of the data. For example, in the Bitcoin network, which uses a PoW CA, the overall operating costs associated with the validation and exchange of public ledger transactions are projected to be as high as $600 million per year and rising. It should also be taken into account that this amount does not include the capital costs associated with the purchase of specialist mining equipment (Deloitte, 2019).

Privacy and Security issues linked to blockchain technology have been rigorously debated. According to Otto (2018) and other experts, blockchain technology is not compatible with privacy laws such as the European Union’s General Data Protection Regulation (GDPR). Although digital currencies like Bitcoin offer pseudonymity, future blockchain implementations that allow smart transactions and contracts could be directly linked to verified identities. This raises privacy and data protection concerns regarding the data that is stored on public ledgers. Participants who transfer personal data to the blockchain are more likely to be classified as GDPR controllers, given they define the processing information, while blockchain nodes that gather personal data are more likely to be identified as processors as they facilitate the operation of the blockchain protocol.

Regulation: According to Egorova and Kozhevina (2020) regulation is a key challenge to the adoption of blockchain technology. In cases where (a) regulations are unclear, (b) they are too strict, or (c) there is an absence of blockchain regulations, there is a high risk of a negative impact on blockchain adoption. On the other hand, smart blockchain regulations may be a driver of mass adoption. Clear regulatory frameworks can facilitate the integration of blockchain technology into existing systems where regulatory sandbox programs can support innovation and increase adoption.

Sourcing: Another important factor in the adoption of blockchain technology is sourcing (Cunha et al., 2021). Employees with blockchain skills are required to support various areas of blockchain systems including designing, developing, deploying, managing, securing, and others. To achieve this, there is a need for education and training programs to develop a skilled workforce capable of supporting the growing demand for blockchain-based solutions.

Public Acceptance: We are still in the early days of blockchain adoption, especially as only a small percentage of the global population uses blockchain applications or cryptocurrencies. Specifically, it is estimated that only 3 percent to 5 percent of adults hold cryptocurrency wallets today. From a different point of view, this may also mean there is huge potential for the blockchain industry as most of the population is still ignoring its existence or prefers not to get involved with it at this time. Blockchain education and smarter regulation are expected to increase these low rates in the coming years (Themistocleous et al., 2020).

## 9.3 REVIEW OF CONSENSUS ALGORITHMS

Achieving consensus in distributed systems is at the heart of this technology, including blockchain. Since by nature such systems do not rely on a central authority for the validation process of transactions, the consensus mechanism plays a key role towards that goal. Such a system would confirm the legitimacy of each transaction by reaching an agreement between all the network participants. Consensus mechanisms existed long before the advent of blockchain. Starting from the “Byzantine Generals Problem”, this is a term derived from the definition of a situation in which two or more parties involved need to agree on a single strategy to avoid total failure, but where some of the parties involved are unethical and disseminate false information or are otherwise unreliable. In 1980, several system architectures were developed forming a distributed system, where Byzantine Fault Tolerance (BFT) consensus mechanisms were adopted. Such mechanisms include Draper’s FTMP, Honeywell’s MMFCS and SRI’s SIFT (Driscoll et al., 2003; Goldberg, 1981; Hopkins et al., 1978).

Before examining the CA, we summarize some key parameters used by them:

- **Throughput:** The rate at which a network can process transactions. Throughput directly impacts its ability to cater to a high volume of users.

- **Scalability:** The capacity of a CA to handle an increasing number of participants. It also ensures the network’s growth without incurring significant performance bottlenecks.

- **Security:** It safeguards the network from malicious attacks and preserves the immutability of the blockchain.

- **Finality:** It assures that blockchain transactions are immutable.

- **Energy efficiency:** It minimizes the environmental impact and ensures the long-term viability of the system.
