
design would require a public-key infrastructure (PKI) to issue and manage public-key certification. Due to the possibility of certificate revocation and expiration, certificate management is a complex issue, and the reliance on PKI creates external dependency and potential single point of failure.

Blockchain can potentially enhance the level of security, dependability, and trust of CPS without resorting to the use of any trusted third party or centralized control. First, fault tolerance for both data and processing can be achieved via the blockchain’s massive redundancy and deterministic execution of smart contracts. The second challenge can be addressed by using smart contract at least partially. Atomicity of computing can be ensured via a smart contract, however, the timeliness of computing cannot be strictly guaranteed. For the third challenge, a CPS application can use blockchain as a trust platform where all transaction records will be made immutable in a decentralized manner, and all smart contracts will be executed atomically with their state reliably logged. Regarding the fourth challenge, a CPS application could adopt the blockchain-way of separating the identity management from secure communication by using a wallet-like component. In Blockchain, all communication is message-based instead of session-based. Therefore, every message is self-contained in that it must carry sufficient information for user authentication (typically via a public key) and it is processed without having to consult with other entities. For systems using the UTXO model, each transaction is associated with a unique pair of keys. Hence, this eliminates the need for checking on the validity of some public-key certificate, which would in turn eliminates the need for a PKI.

### 10.2.2 Application Categories

To find out how the blockchain technology has been accepted and impacted the broader industry, we did a literature search specifically in the context of cyber-physical systems. As mentioned earlier, we believe that in this area blockchain could play a more critical role in making the applications more secure and dependable, and ultimately, more trustworthy.

The literature search was done in early 2020 using the Web of Science core collection. We first used the search term “blockchain cyber physical systems”. The search result contains 76 publications. We again searched using the term “blockchain IoT”, which returned a total of 764 papers. Then, we narrowed the search with a term “cyber physical systems”, which led to 33 papers. After removing irrelevant papers and low quality papers, we selected 40 papers as the basis for the review on blockchain applications in CPS.

![](img/7320b1480d74f1d65f74659cab456782_417_0.png)

The application areas are summarized in Fig. 10.3. Not all works can be easily categorized into a particular industry sector, for example, the work on supply chain [47, 63] and IoT [37, 42, 44, 65] can be used in many industry sectors. Likewise, the work on generic workplace [4] is applicable to most industry sectors. There are also papers having a high level discussion on considering blockchain as one of the enabling technologies for general purpose CPS systems [2, 3, 27, 29, 53, 54, 67, 76]. Comparatively, there are fewer publications that have focused on a specific industry sector.

What we have seen include energy systems [39, 46, 70, 92, 93], smart city [25, 52], automobile [24], healthcare systems [21, 51], manufacturing [3, 21, 43].

The following tables show the key operations that are enabled by blockchain as well as relevant references for each category of applications. Table 10.1 shows the key operations for blockchain-enabled IoT. As we can see, blockchain has been used or proposed to use in a wide variety of aspects of IoT operations, from secure communication, to access control, to the overall architectural design of IoT systems.

Table 10.2 shows the key operations of blockchain-enabled supply chain operations. Only two papers have been found in this category [47, 63]. One focused on general discussion on how to use blockchain to make supply chain operations more efficient with machine-to-machine interaction [63]. The other focused on primarily software management by exploiting the immutability feature of blockchain [47].

Table 10.3 shows the key operations of blockchain-enabled manufacturing [3, 21, 43]. The operations that can benefit from

| Applications | Blockchain-Enabled Operation/Key Points | References |
| --- | --- | --- |
| IoT | Identity and attribute management | [37, 32, 7] |
| | Data-facilitated assessment | [42] |
| | Secure communication for IoT | [55, 56] |
| | Secure edge-to-cloud communication | [35] |
| | Secure publish-subscribe communication | [41] |
| | Proposed a service-oriented architecture | [65] |
| | Enhance business processes | [64] |
| | Access control with smart contract | [63] |
| | Overview of blockchain-enabled IoT applications | [63] |

Table 10.1 Blockchain-enabled IoT-based applications.

| Applications | Blockchain-Enabled Operation/Key Points | References |
| --- | --- | --- |
| Supply Chain | Supply chain software management | [47] |
| | Software patch management | [47] |
| | Software configuration management | [47] |
| | Digital supply chain | [63] |

Table 10.2 Blockchain-enabled supply chain applications.

| Applications | Blockchain-Enabled Operation/Key Points | References |
| --- | --- | --- |
| Manufacturing | Vertical and horizontal system integration | [22] |
| | Design and engineering stages integration | [22] |
| | Secure communication in machine-to-machine interaction | [43] |
| | Securing sensing in production environment | [43] |
| | Data sharing among partners | [43] |
| | End-to-end tracking in manufacturing supply chain | [43] |

Table 10.3 Blockchain-enabled manufacturing applications.

| Applications | Blockchain-Enabled Operation/Key Points | References |
| --- | --- | --- |
| Automobile | Data management | [24] |
| | Automobile supply chain end-to-end transparency | [24] |
| | Smart contract between partners | [24] |
| | Access control with smart contract | [24] |
| | Automobile parts production traceability & data provenance | [24] |
| | Financial management between buyer and seller | [24] |

Table 10.4 Blockchain-enabled automobile production.

integrating with blockchain range from securing communication, enabling data sharing, end-to-end tracking in manufacturing supply chain, to system design and integrity.

We found only a single paper in the automobile sector [24], which is shown in Table 10.4. The paper discussed a full-range of application of the blockchain technology in this sector from data management, to data provenance for parts production tracking, to automobile supply chain end-to-end transparency, to the use of smart contract for access control and partner interaction, and to financial management between buyers and sellers.

There are more interests in integrating blockchain with energy systems [39, 46, 70, 92, 93], including smart grid, traditional power plant operation, and energy trading. The operations identified by these papers are shown in Table 10.5, and they range from sensor

| Applications | Blockchain-Enabled Operation/Key Points | References |
| --- | --- | --- |
| Energy | Sensor data acquisition and logging | [46, 70, 92] |
| | Energy resource management (direct load control) | [92] |
| | Microgrid operation and control | [46] |
| | Electric trading among electric vehicles & charging stations | [46, 93] |
| | Electric energy trading | [46, 39] |
| | Reliable data provenance for power delivery | [39] |
| | Privacy in home area network | [39] |
| | Power generation and distribution monitoring | [58] |
| | Power system control | [58] |

Table 10.5 Blockchain-enabled energy systems.

| Applications | Blockchain-Enabled Operation/Key Points | References |
| --- | --- | --- |
| Smart Health | Smart clothing | [21] |
| | Secure sensing data acquisition and logging | [21] |
| | Data sharing (for occupational therapy) | [51] |
| | Patient status monitoring (with smart contract) | [51] |

Table 10.6 Blockchain-enabled healthcare systems.

data collection, to power generation and distribution monitoring, to data provenance for power delivery, to microgrid operations, to operations in home area networks, to energy trading.

We found two papers on blockchain-enabled healthcare systems [21, 51], and the key operations they identified are shown in Table 10.6. One focused on collection of sensing data regarding a patient’s biological status using smart clothing [21]. The other concerns increasing health IT operation efficiency with blockchain for data sharing and for patient status monitoring [51].

Table 10.7 summarizes the key operations in smart city related applications [25, 52]. Smart city is becoming a more popular topic and it appears that it has encompassed intelligent transportation systems [25] and practically includes everything that could happen
