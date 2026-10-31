
was divided into three parts: data producer, Blockchain platform layer, and data consumer layer. Using IoT devices, patient records are stored. It uses a private and public key in the lightweight attribute-based authentication mechanism to verify devices' authenticity and encrypt PHR data. The blockchain platform layer has provisions to store data, patient id, block hash, and encrypted data that anyone can search and verify. Access control, key management, and filtering are done in this layer. Data consumers such as physicians, researchers, and insurance agents can request data upon data retrieval request authentication. While data filtering and decryption occur before data delivery, as depicted in Fig. (3) [17].

![](img/12e321fe66dd89993b17a8d73b64bd0c_276_0.png)

Fig. (3). Data acquisition, management, provision, and verification via SEAL.

Banotra et al., in their research work, proposed layered architecture to use IoT, Cloud Computing, and Blockchain-based system to store and share PHR/MHR [18]. Their proposed model contains the following layers:

- 1. Physical Layer (Patient)
- 2. Device Layer (Mobiles, Wearables, Medical Devices)
- 3. Communication Layer (HTTPS/TCP-IP, API, GATEWAY (Lora, ZigBee, Profibus))
- 4. Cloud Interface (Cloud Hub with MQTT/COAP support)
- 5. Platform Components (Low Level - Real-time data processing and Storage Engine, Blockchain Engine, Middle Level – API Management Layer, Government Healthcare Data System and HMS/HIS, Top-Level – Mobile/Web Application)

## 6. Stakeholder Layer (Governments, Regulators, Hospitals, Doctors, and Patients)

PATIENTORY1 (Atlanta, Georgia) and MEDICALCHAIN2 (London, England) are two well-implemented Blockchain-based HDMS/HIS real-world products.

The processes of collecting, processing, storing, retrieving, and completing/filtering data sharing among various stakeholders of healthcare ecosystems were similar, as discussed in earlier case studies, while using an API-based data access model is a new addition. They also included multiple regulators and governments in their proposed model as stakeholders.

## How Does Blockchain Address Security, Consensus, and Data Manipulation Issues?

Each wallet (client application) is secured using a private key and the passcode known to the wallet user. Guessing a private key using a brute-force attack is not feasible because of many key pools. In the case of a custodial wallet provider, the private key is managed by the wallet provider themselves, but then also no one can use their wallet without a passcode. However, in most cases, the attackers were found stealing individual private keys and passcode to steal information from the Blockchain client application.

Transactions in Blockchain are highly secure because the communication channel is encrypted using public and private key cryptography. A participant in Blockchain is called a node, and each node digitally signs the transaction using its private key. After signing, the Block is broadcasted to various peers for confirmation, and based on consensus; the generated Block is verified and added to the distributed ledger. The fact is that no authentic party can sign these transactions without an approved private key verified using a public key, and any manipulation in a block during propagation would result in failure during the decryption process. Hence communication between nodes in a peer-to-peer network is highly secure [19].

After receiving the broadcasted block participant node verifies the transaction and regenerates the block hash values using hash functions like SHA-256, Keccak256, SHA3, SHAKE256, etc., and matches with hash values stored in the Block. If the value is matched, then it is a valid block; else, the Block is discarded, and if a majority of the nodes (generally 51% nodes) in the Blockchain network confirm the correctness of the Block, then this Block is added to the Blockchain. This block verification process and the consensus is called the mining process, and the scheme is called Proof of Work (PoW). In the PoW, hash verification is done more times, and computing is resource-consuming [20]. Various Blockchain platform uses different Consensus Algorithms (CA) [20] like Proof of Stake (PoS), Proof of Importance (PoI), Byzantine Fault Tolerance (BFT), and Proof of Elapsed Time (PoET) [13].

In Blockchain, each block stores the hash value of its Block and the previous block hash. Any changes to any block generate a different hash result. The Blockchain network can easily track these manipulated blocks, and manipulated blocks get discarded. To change any block, one has to change the current block hash and all hash values of all forward blocks. An attacker could change the block value of any single node, but to reflect changes, the attacker has to change the Blockchain of more than 51% of nodes, which is almost impossible to do without being caught. As Blockchain is distributed, each node maintains a separate copy of Blockchain. It is also tough to do so because it requires a massive amount of computing resources, and the cost of doing so would be huge.

## How Does Blockchain Address Privacy Issues?

The Blockchain supports anonymity and eliminates the need for a trusted third party, but anonymous transactions could be troublesome if this technology is used for wrongdoing. This is the biggest concern of various law enforcement authorities, but there are ways to address it without compromising anonymity using Blockchain technology. Without revealing the private key, a wallet application only exposes the wallet address, not the private key or any personal identity of the wallet holder, to protect the privacy of wallet owners. The wallet application providers can facilitate the Know Your Customer (KYC) process and issue digital identities in the form of wallet addresses without compromising owners' privacy. The digital identity can only be revealed to law enforcement agencies when needed to avoid misuse of Blockchain Technology.

## Preventing PHR, EMR Manipulation, and Sharing Records Securely using Blockchain

In Blockchain-based PHR/EMR systems transaction process, reliability and security are maintained at the following level:

- 1. Submission of transaction or origination of data-source from trusted and authentic users. A private key is issued to the user to sign messages digitally. Nodes verify the digital signature of the messages against the public key to ensure a trusted party initiates the transaction.
- 2. Inter-Node communication is done through remote procedure calls in peer-to-peer distributed Blockchain networks. The communication channel is protected using a secure socket layer to ensure end-to-end encryption.
- 3. Each block is timestamped and stores current and previous block hash values in the distributed Blockchain. Any changes to any block would result in a different block hash value that can be tracked. To modify one Block, one has to change all the blocks that come after the changed blocks and make the same changes in the Blockchain of all participating nodes on Blockchain networks. It is almost impossible to do so in secret without reaching a consensus, and the cost of doing so would be very costly as it requires enormous computing resources.

## ISSUES, CHALLENGES, AND RECOMMENDATIONS

The researchers proposed a systemic approach using Blockchain to collect, store, retrieve, and share PHR and MHR data. However, there are various issues and challenges, as listed below:

- 1. Real-time data collection is not possible in many cases due to networks, faulty devices, and power issues.
- 2. If security keys are compromised by the patient or custodial key service provider or key repositories, the attackers could alter the Blockchain data and change data blocks of PHR/MHR in the ledger.
- 3. To decrypt encrypted PHR/MHR records, the patient has to share their private key, which can be stolen if the health professional uses a compromised system.
- 4. The Pharmaceutical companies would also need the patient's private key to decrypt the patient's data, so they could also create a local store of private keys and PHR/MHR records and misuse it.
- 5. There is no need to share the complete PHR/MHR with all stakeholders.
- 6. Blockchain offers better transparency, trust, tamper-proofing, consensus, and security, but it has another set of challenges and issues [21] which can be addressed by adopting the recommended best practices of Shrivas et al. [13].
- 7. Due to the invention of Quantum Computing, the entire Blockchain can be compromised, as Quantum computers are much faster than any known supercomputers of the current time. Most Blockchains and other systems, along with HDMS/HIS, use RSA-based private-public keys that come under pre-quantum cryptography and can easily be broken with the help of Quantum Computers [22, 23].

The patient should have complete ownership of the private key, and there could be smart contracts to share selected, not all, data among healthcare providers and pharmaceutical companies. The Patients should have the option to securely
