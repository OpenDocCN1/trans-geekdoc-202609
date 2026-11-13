
![](img/f7b65e1b6017d6bb4f421d92025cbdc6_154_0.png)

**FIGURE 6.2** Working of the blockchain technology.

This transaction is published on the blockchain network, where the miners confirm it. Blockchain’s high-performance nodes are known as miners [14]. Using a consensus mechanism also known as proof of work, miners make the transaction unmodifiable and irrevocable. The generation of a legitimate block is a contest between the miners, and the winner is paid [15]. Figure 6.2 describes the working of the blockchain technology. Only when a transaction has been validated by every miner on the network is a block containing that transaction considered to be genuine and added to the longest blockchain, if more than 50% of the miners confirm the transaction [16].

## 6.2.2 Literature Survey

This section describes several initiatives attempted to protect health records, as well as the difficulties and potential explanations.

*Towards using blockchain technology for e-health data access management.* Writers highlight advantages of Blockchain and specific issues related to it for protected deployment of the health record. It offers an ascendable explanation in order to achieve the greatest presentation. They have also put out a design to address the problems with health application, in which hospitals and doctors are viewed as nodes associated to the e-health blockchain via smart contracts, and a separate database is also kept off-chain [17].

Through the data gateway, patients can communicate with blockchain and medical sensors. This study also demonstrates how completely functional systems can be developed to revolutionize future applications with usage of appropriate tools, prototypes, protocols, and blockchain technology.

*Decentralized e-health architecture for enhancing healthcare analytics.* In the chapter titled “Decentralized e-Health Architecture for Enhancing Healthcare Analytics,” the writers discuss the difficulty connected to the analysis and safety of medical data. Additionally, they have made an attempt to deliver an explanation that elevates the bar for medical care. Based on the Exonum framework, which consists of nodes associated by peer-to-peer connections—and all nodes are validated by utilizing a public key—they have built a blockchain solution for state scale in healthcare [18]. They’ve also suggested that blockchain would be used to manage enormous volumes of healthcare data and sustain patient privacy.

Is blockchain technology a potential solution to security and interoperability problems affecting EMR in developing nations? The implementation of blockchain in EMR ensures uninterrupted readiness and access to real-time data, according to the chapter “Is This Solution to EMR Interoperability and Safety Challenges in Developing Countries?” Blockchain enables patients to fully access their data and have control over how it is united. Further, blockchain relies on cryptographic methods to communicate in a network without prior mutual belief. The privacy of patients is protected when their information is shared among stakeholders due to information encryption [18].

Introducing blockchain for healthcare. Authors of this chapter focused on various blockchain topologies, present blockchain problems, and provide prospective blockchain results. Even while blockchain is used to generate smart contracts between healthcare providers [19] and to grant access to specific data or patient records, it is impossible to determine who is accessing information and whether the person is authorized to do so or not. The Sybil attack is another security vulnerability that can be fixed by demanding that every miner node take part in the solution of a mathematical puzzle before attackers add a new block to blockchain [19]. Because of these issues, the author has suggested that researchers construct a new blockchain architecture that does not rely on an existing cryptographic method.

## 6.3 Medical Data Supervision on Blockchain

The current healthcare structure keeps track of patient health information digitally. Currently, healthcare organizations save patient data, diagnostic results, and doctor’s prescriptions in a consolidated manner. Patients don’t have control over their data, and updating documented data is a time-consuming and difficult process; thus, there is a potential that it will be leaked or used for other purposes because it is a centralized system. We are putting out the notion of converting a centralized system to a decentralized system consuming blockchain technology in an effort to address these issues. In order to integrate blockchain in healthcare, it is first necessary to comprehend the extent of the data as well as where and how it is being produced [20].

At each stage of medical therapy, such as a discussion, diagnosis, and surgery, healthcare organizations produce sensitive and important medical data. The medical information includes prescriptions written by doctors, MRI scans, X-rays, angiography, ultrasound reports, endoscopy, radiography, as well as a few other types of sensitive health information, including cancer, HIV, or psychological problems. Figure 6.3 shows medical data supervision on blockchain [20].

- Hospitals maintain patient's records using blockchain
- Each patient's records are stored in blocks using their public keys
- Healthcare organizations submit their queries via APIs to access patients
- Patients permit healthcare organizations to access their medical data by sharing their unique IDs

**FIGURE 6.3** Medical data supervision on blockchain.

To advance the quality of data before placing it on the blockchain, some value must be added. Medical records for patients should be precise, clear, and organized, since unstructured data causes errors and delays in the delivery of care. Digital health records can be stored across numerous nodes within a blockchain network, removing concerns connected to data centralization [20].

Patients’ medical records may be saved on the blockchain network using their public keys, and transactions containing patients’ medical records may be preserved using both the patients’ individual IDs and public keys. Only when unique IDs match may healthcare institutions access a patient’s non-identifiable data using smart contracts. Patients can, if necessary, share their public key with healthcare organizations, but data would never be identifiable without their private key.

Smart contracts are required to make sure users will share or recover the data. Smart contracts are self-executing contracts between two parties in which terms are directly written in code without the assistance of a third party. It is a procedure that supports, upholds, and authenticates contract negotiations and execution digitally [20].

The suggested notion is built as a contract with the name healthcare that has two nodes, each of which can be assumed to represent a hospital administrator or a lab administrator. A structure that includes the patient’s address, test name, hospital name, unique ID, date, price, and signature count is formed and given the name “record.”

### 6.3.1 Invoking the Transaction

We utilized a function Object() that is run automatically when a DApp is deployed and is public in nature. Only hospital administrators should start transactions on the blockchain network, as it is only he who chooses the lab admin and gives him a specific address [20].

### 6.3.2 Creation of New Records

To add new data to an existing record, we’ve built a function called “new record” that works by giving values to the corresponding arguments. Records is an array that stores the current patient records.

### 6.3.3 Record Validation

To be utilized for record validation, a function called “sign record” was created. If the new record is in the array of records that already exist, the hospital administrator will sign the transaction; otherwise, if the record already exists, the signature count value will be 1. In this function, the presence or absence of the new record in the existing record array is determined using the signature count. The transaction will not be signed. When the signature count equals 2, a record that has been signed is released [20].

## 6.4 Why Is Blockchain Technology Needed in the Healthcare Industry?

According to CNBC, human error is the third foremost cause of death in the United States.

- The safety of patient health records.
- Lack of transparency in the drug supply chain.
- The dispersion of healthcare-related data, such as patient medical histories or the qualifications of medical staff.

According to the 2020 Breach Barometer research, nearly 41 million patient records were exposed. The World Health Organization estimates that one in ten medical gadgets sold in developing countries is defective [20].

These are a few of the typical difficulties. The current situation makes it impossible to share and obtain health data on time.

The potential for blockchain technology to address these healthcare trials is great. The way patients and professionals handle and use health data will be significantly improved and transformed. Each healthcare company is attempting to integrate technologies that would simplify their procedures in the wake of the digital revolution in the healthcare sector.

However, because this sector deals with sensitive medical information, professionals must make sure that any technology they employ does not jeopardize the security of patient data. Blockchain technology is useful in this situation. There are several ways that blockchain technology might help the healthcare sector [20].

## 6.5 Top 10 Blockchain Use Cases in the Healthcare Area

Blockchain technology has a lot of potential to help close gaps in the current healthcare sector. Ten frequently utilized blockchain applications in healthcare are listed next.
