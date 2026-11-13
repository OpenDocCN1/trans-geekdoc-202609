
across all blocks [17]. Every time a secure block is generated, a new hash is generated, and miners are paid with Bitcoins and transaction fees for each transaction they successfully confirm.

- 3. Spending twice. Double spending refers to sending a Bitcoin transaction to two separate receivers simultaneously. At all costs, you should avoid this.

- 4. Proof-of-work (PoW). Proof-of-work is a requirement that expensive computations be done to permit transactions. PoW was created to support the trustless consensus. A PoW is a block that has been hashed.

- 5. Hashcash. A PoW is an example, such as Hashcash. The PoW function of hash is used by Bitcoin. Hashcash is a PoW method that generates data that is challenging to produce computationally but simple to verify by others. For each block, miners are required to generate a hash and a “nonce number” to generate a hash with the necessary number of leading zero bits to satisfy the difficulty requirement.

- 6. Nodes. The network’s nodes are dispersed computers that each hold a copy of the whole blockchain. Copies of the blockchain and access to it are disseminated as new users join the blockchain network. All the nodes in the various networks can replicate, synchronize, and share the data. There is no single node or network that has control over the data.

- 7. Address. The network’s nodes are dispersed computers that each hold a copy of the whole blockchain. Copies of the blockchain and access to it are disseminated as new users join the blockchain network. All the nodes in the various networks can replicate, synchronize, and share the data. There is no single node or network that has control over the data.

- 8. Smart contract. An unchangeable, digital contract known as a smart contract is one that is kept on the blockchain. It specifies some logical requirements that must be met to carry out tasks, like depositing money or data [18][19]. Criteria for transferring funds to a third-party delivery team, for instance: consider a situation where a sender wants to use a third party to deliver products to a recipient, but only when the delivery is successful. Then, a smart contract might look like this: On the day when the products are loaded, the sender makes the shipment payment. Until the recipient acknowledges to the sender that the products have been received, the smart contract will withhold payment to the delivery crew.

## 8.7 Cloud Forensics Challenges

### 8.7.1 Technical

- 1. Accessing logs. The standard method of computer investigation for locating a cybercrime entails locating the log data of each action performed on the devices and then evaluating them to discover the evidence [20]. The fact that the archives reside on a distant, unidentified server makes this application of cloud computing architecture special. With cloud computing, fetching logs becomes challenging.

- 2. Gathering reliable data. The process is intended to ensure that the information contains reliable data that may be used as proof in court. As several users share the same physical location, it is very challenging to guarantee the confidentiality of data in the cloud.

- 3. Another significant issue with cloud forensics is the existence of huge quantities of information that need to be analyzed to find evidence. The traditional forensics approaches are incompatible with such enormous quantities of data. During the investigating processes, the provider of cloud services must comply.

### 8.7.2 Procedural

- 1. Recreating the crime scene. In some cases, the investigation process calls for re-enacting the entire criminal enterprise to find the evidence. All the actions taken at the crime scene are repeated and simulated during this process [21][22]. Cloud computing makes this more challenging because clouds are maintained as virtual machines that may be deleted after a crime to remove all traces of it and make room for recreation.

- 2. Multinational laws. The investigations are carried out in accordance with the laws of the nations where the crimes are committed. Since cloud data centers are located all over the world, many rules must be complied with when conducting investigations in the case of cloud forensics.

- 3. Presentation of the evidence in court. The case inquiry calls for the presentation of the evidence in court. It's possible that the jury members are unfamiliar with the complicated cloud computing models [23]. So presenting the evidence becomes a difficult task in cloud forensics.

- 4. Crime scene reconstruction. To investigate harmful activities, investigators often need to recreate the crime scene. Using traditional digital forensics, the investigator can quickly determine how many devices were involved in the crime or who committed it [24][25]. Reconstructing the crime scene and determining the extent of the damage is nearly impossible due to the extremely dynamic nature of the real-time, autonomous interaction in the cloud environment between multiple nodes.

- 5. Evidence segregation. In the cloud, virtualization allows for the isolation of various instances running on a single physical machine. Even though their data instances are stored on the same system, different users behave as though they are running on distinct hosts. Because of this, it is extremely challenging for CSPs and law enforcement agencies to tell them apart during investigations without endangering the anonymity of other entities who use the technology [26].

- 6. Lack of user statistics anonymity. Most cloud service providers adhere to user-friendly standards and request minimal data from clients [27]. Due to the limited information provided by the sparse user data, it is challenging for the detective to identify the guilty party.

- 7. Data origin. Unlike investigations involving traditional digital forensics, cloud-based data may originate from thousands of different user locations, making it challenging to identify who or what created and/or altered the data item there. The data's source is thus less clear.

- 8. Data privacy and a lack of accountability. In cloud services are issues that are normally handled by IaaS providers, like Cloud Servers, AWS, Microsoft Azure, iCloud, and numerous others [28]. However, a few services use common keys for disk encryption and archiving.

- 9. Less control. As opposed to digital forensics, where the investigator has more control over the access level to cloud devices, cloud forensics depends on the various service models.

### 8.7.3 Custody Forensic

### 8.7.3.1 Security, Efficiency, and Scalability Costs

The expense associated with the security management and efficacy in the chain of custody for evidence in the case is one of the main obstacles to the implementation of a blockchain network. The design enables provenance and transparency by continuously growing the distributed ledger as transactions are completed and case data from all parties are added. This enables everyone engaged, regardless of who oversaw the acts, to examine relevant case-related material at the same time [29]. Each participant’s fear of sharing their operating records with the other peer group members is removed by Hyperledger.

### 8.7.3.2 A Lack of Uniformity

Multimedia forensics research systems employ a wide range of case investigation approaches, which add to the inconsistent chain of custody for media evidence. Digital forensics’ process layer, which includes gathering evidence and preserving it, is less trustworthy. This has inescapable negative effects and offers inconsistently poor quality. Design enforces a consistent approach and raises the standard of the final product by standardizing the forensics processes. The process flow of digital forensic is shown in Figure 8.3.

### 8.7.3.3 Issue with Record Transparency

One of the main problems is providing data accessibility (chain of custody) in a scattered setting. We have designed Sawtooth’s fully decentralized ledger verification and transaction method, as well as its consensus verification policy (PoET), to provide a solid architecture for privacy protection and security, since Sawtooth is unable to give a predetermined data transparency policy. This can also assist us in developing an architecture for forensic chain-of-custody investigations that upholds the openness and traceability of data and evidence [30][31]. We provide systems with effective document monitoring and proof administration at every layer of the smart contract by utilizing the hyper-blockchain modular platform. In comparison to the conventional technique, its comprehensive design offers superior chain security management, a better activity record case, and better outcomes.

![](img/f7b65e1b6017d6bb4f421d92025cbdc6_198_0.png)

FIGURE 8.3
Digital forensic process flow.
