
## 9.3 SYSTEM COMPONENTS AND ARCHITECTURE

With the advent of many healthcare providers and wearable devices, a huge amount of PHD is generated. However, it is not used for active disease diagnosis or prevention. Since EMR is data by healthcare providers, it is accessible only to that healthcare who created and maintained it. Moreover, health data is highly privacy-sensitive, and storing in public cloud systems increases the risks of malicious attacks and data stealing.

If a patient decides to switch from one healthcare provider to another, then all the patient-related data may not be disclosed to the second healthcare provider immediately. In such a situation, necessity arises to get the health data of the patient by taking all the tests once. This results in increased expenses and delays in following up the treatment of patient. To enable data sharing between two health institutions, there is a need for secure infrastructure. Another important problem that should be focused on, is if the patient needs treatment in a foreign country, there is no universal access to patient records. This data can delay the treatment to the patient, which may have severe consequences. Microsoft HealthVault is a third-party vendor that helps patients to store their PHD and give access to others the data. Since the data is stored in third-party data centers, it is susceptible to attacks from hackers, who wants to steal the data. Another problem is the authenticity of data. The doctors can be cautious of the data provided by the patient. There are no methods to validate if PHD is tampered with or. Patients can modify data and submit to healthcare providers.

This study aims at providing a solution to these problems by shifting the architecture of the healthcare domain to decentralized distributed architecture. The PHD is stored on a distributed network owned by the patient. The members of the network can be different healthcare providers, insurance agents, etc. The patient is the owner of the data and the network. The doctors and insurance agents can access the data with patient’s approval. Thereby, the healthcare is no longer restricted to only centralized healthcare provider. The introduction of blockchain technology in this scenario brings security, transparency, and authenticity to the data stored by the patients. The transactions in the network can vary fast with the consensus concept in blockchain, and everyone in the network will be aware of what is happening in the network. Information/data is the greatest asset, and by securely sharing it, a fast hassle-free and transparent system that is patient-friendly can be developed.

### 9.3.1 LACK OF PHD INTEGRATION IN HIE

At present, no steps have been taken by either healthcare providers or national governments to include PHD for healthcare. There are devices available in the market to measure cholesterol, blood pressure, glucose level, etc. These can be monitored by patients themselves. However, the medical personnel do not consider this data for treatment or diagnosis. So, even if a patient notes a fluctuation in his blood pressure with his/her personal device, a physician will only take into account the blood pressure readings from certified labs. One of the reasons for the physicians not considering the data from healthcare applications is the lack of standardization. No communication protocols or systems are deployed to collect this data securely and transfer to healthcare providers. There is a need to standardize all the healthcare devices in hardware, communication protocols, system design, etc. [12]. Even though research is going on this area, practical implementation of these studies has not been deployed.

The inclusion of PHD in HIE can save a lot of time for patients as well as physicians and speed up the entire process.

### 9.3.2 MINIMAL DATA SHARING ACROSS HIE

As per survey conducted with the help of US Department of Health and Human Services [23], it has been observed that even the number of organizations that are willing to support HIE has increasing with time, there are very few health providers that support active and robust information exchange. One of the reasons is the lack of government funding available to healthcare providers to set up an infrastructure for HIE. Second reason is that no organization or patient wants to pay for data exchange. There should be a very secure way for transfer of data, and no one is ready to incur the expense. Another reason is low adoption rate of EMR. There are many hospitals in the USA that have not digitized their patient record storage systems. They still write reports in papers and store in file cabinets. In such a situation, EMR cannot be adopted.

### 9.3.3 LACK OF PROPER TECHNICAL SECURITY MEASURES

As mentioned in the earlier sections, the lack of secure and robust infrastructure to store the health reports is a major blow to integrate HIE into mainstream healthcare services.

#### 9.3.3.1 Objectives

#### 9.3.3.1.1 Data Security

The use of blockchain to store data ensures the security of data. When a private blockchain network is created, there are certain criteria that should be satisfied for a member to join the network. The members can be doctors, nurses, and other medical personnel of the patient. Necessary proof should be presented to validate the same. All members in the network will be known to the patient and versa [24].

#### 9.3.3.1.2 Immutability

Blockchain is an append-only system. Once a record is added to the blockchain, it can never be removed or deleted. So, no one can tamper with the health records or compromise its private nature. All transactions on the blockchain are recorded and timestamped [25].

#### 9.3.3.1.3 Transparency

All members in a blockchain network can view all the records. Before adding or editing a record, all the members in the network should agree on the same. Only after that, a new record can be added. Since all transactions have with the consent of all members in the network, transparency is ensured. No one can change anything without the knowledge of others [26].

#### 9.3.3.1.4 Ease of Access

Every member of the network keeps an exact copy of the blockchain on their personal computer. If patients want to monitor their health, they can view it on a personal computer. Physicians can also view the records uploaded by another physician [27].

#### 9.3.3.1.5 Interoperability

An implementation of a secure HIE will enable different healthcare providers to exchange data among themselves. This can help in quick diagnosis and treatment of diseases. Such a system can also enable physicians discussing among themselves effective treatment plans for their patients. Thus, HIE can help to achieve interoperability and better communication between different healthcare providers [28].

### 9.3.2 Architecture

The proposed architecture can be divided into three subsystems: user-friendly frontend–BlockHealth application, Tendermint, and backend storage systems.

As shown in Figure 9.1, our focus is on developing a decentralized distributed application that can ensure the origin and authenticity of records stored in the blockchain. The decentralized distributed stack architecture ensures that even if one node is lost, and never, no node can make changes in data without the consensus of other nodes. All the transactions are transparent to all users in the private blockchain network. Since BigchainDB is BFT at a time, one-third of the nodes in the network can fail, and still, the system will be running without any issues.

The first layer in Figure 9.1. BlockHealth web application, provides a user-friendly interface to upload the health documents and store them in the IPFS and then in blockchain. Tendermint acts as an interface to broadcast transactions to all nodes in the private network. It is Tendermint that initiates the consensus process that determines whether a transaction is valid. If the transaction is valid, it will be added to the network; else, it is not.

![](img/816c34830872ca25a809f80557c76d27_230_0.png)

FIGURE 9.1 Decentralized stack architecture.
