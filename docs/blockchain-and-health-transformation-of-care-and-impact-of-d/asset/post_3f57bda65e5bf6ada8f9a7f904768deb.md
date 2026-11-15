
have no direct control thereafter. Secondly, there is no particular protocol between the different systems for sharing sensitive data. In order to refute the two issues, the Blockchain Lab of Arizona State University conducted a study and presented a MedFabric4Me. This is a system for HIE based on Blockchain. In this rather technical case about MedFabric4Me, we delve deeper into this system.

## Healthcare Information Exchange (HIE)

Healthcare Information Exchange (HIE) is the electronic transfer according to national standards of healthcare related data between medical facilities, public authorities and health information organisations - companies that supervise and regulate the exchange of these data.

The purpose of HIE is to promote proper and safe access and retrieve health information from a patient in order to improve the cost, quality, safety and speed of patient care. Although HIE usually refers to the act of exchanging information between two or more organisations or healthcare providers, it may also refer to an organisation responsible for facilitating the exchange.

## CASE 3: HEALTH INFORMATION EXCHANGE AT MEDFABRIC4ME

MedFabric4Me is a patient-focused system where patients own and share their healthcare data based on necessity. Arizona State University with its Blockchain Lab is a knowledge partner of the Blockchain professorship and also conducts specific research into Blockchain and healthcare. This case MedFabric4Me is an example of how Blockchain can be used effectively in healthcare.

First, an analysis was performed of the requirements for a patient-oriented system that ensures fraud-proof sharing of the data among the participant. This system contains a mechanical system that ensures that data cannot be manipulated. A distributed Proxy encryption system has been used to securely encrypt data during storage and data sharing. In addition, the combination of on-chain storage and on-chain access management has been applied for authenticity and privacy.

### On-Chain and Off-Chain

MedFabric4Me is a two-part solution platform consisting of on-chain and off-chain components. The on-chain solution is implemented on the secure network of Hyperledger Fabric while the off-chain solution uses an Interplanetary File System to store data securely. An Ethereum-based Nucypher – a Proxy re-encryption network – provides cryptographic access control to actors for encrypted data sharing.

To demonstrate usability and scalability, a prototype solution from MedFabric4Me has been implemented and evaluated as the performance benchmark of the system against an already implemented HIE. The results show that decentralised technology such as Blockchain can help to reduce some of the problems HIE faces today, such as patient transparency, slow emergency response and better access control. The research (Vishnoi 2020) therefore concludes that MedFabric4Me benefits in terms of operation and performance.

### Properties of MedFabric4Me

The experiment has demonstrated the potential in an interoperable network of a private and public blockchain. If we compare this application with the HIE, intervals of scalability and performance, we see the following:

### Privacy

As previously indicated, data from healthcare and the electronic patient file are protected by laws and regulations. Therefore, each system must comply with the Health Insurance Portability and Accountability Act (HIPAA) privacy guidelines. HIPAA is the 1996 US healthcare legislation. MedFabric4Me meets all minimum requirements.

A patient can delete their account at any time on MedFabric4Me. So when you leave the network, MedFabric4Me immediately deletes all information for the participant. Although the exchange of information must be recorded as a transaction history, MedFabric4Me as a general ledger is unchangeable.

A patient manages data sharing in MedFabric4Me and can therefore unsubscribe from file sharing at any time. A patient therefore determines their own policy for sharing data. In addition, a patient may request the supplier to change incorrect health information. Although the patient cannot change his electronic patient record himself, any discrepancy can be changed by a next doctor.

### Partial Sharing of Data

De-identification is required when the patient's data are shared for study purposes. To comply with the same, MedFabric4Me may partially share data, hide personal information, or may not be required to share data for structured data only. For unstructured data, it has not (yet) been implemented in the system, but can still take place at a later stage.

### Scalability

For scalability of Hyperledger Fabric, we will need to compare it to the state of the art of the Arizona company Health Current. Health Current completes an average of 23.4 million HLF transactions, 1.2 million CCD transactions and 10.4 million warnings per month.

### IPFS versus Cloud

Cloud services offer about 20MB per second of upload and download speed, while Interplanetary File System (IPFS) provides a constant upload time of 0.4 seconds for encrypted files. For unencrypted files, the speed decreases even more (Taylor 2020). This shows that IPFS performs better for most uploads than cloud services with unencrypted file sizes. In the case of downloading, IPFS offers a speed of about 7 MB per second and is lower than the download speed of cloud services. This can be improved by creating a private cloud service and duplicating data across multiple peers. The researchers (Vishnoi 2020: 80) therefore conclude that IPFS may not be the best database for applications, but that it works to store files with a hash and when access control via Hyperledger Fabric is regulated.

### Nucypher

PRE is the most popular coding algorithm (Aminubaba et al. 2014) in the cloud and has a speed of about 55 MB per second for encryption, compared to Nucypher with 115 MB per second. PRE therefore offers better performance in terms of encryption time than existing cloud services.

### Comparisons of Use between MedFabric4Me and HIE

Finally, we look at six scenarios in which HIE offers benefits to healthcare providers and participants and compare them with the implementation of MedFabric4Me.

### ADT Messages

When patients are admitted, discharged or transferred to an emergency situation, the patient's caregivers receive a warning with the basic information (date of admissions, place of admissions, reason for admission, etc.) and can thus reach the patient and take care of follow-ups. This warning is an ADT message, where ADT stands for Admission, Discharge and Transfer.

However, MedFabric4Me does not (yet) have an implementation for emergency visits, although the most important functionality of the ADT messages are implemented in an unchangeable ledger. When a patient visits the emergency room and files are updated, MedFabric4Me records the transaction of data unchangeably. Providers will then not receive ADT messages at the exact time of status change. But when patients visit providers, those providers get a general history of the updated files with the patient's visit to the emergency room for what reason.

### Improvements in Pandemic Warnings

A pandemic is an epidemic of diseases that spreads across a large region. Very well-known examples of this are SARS and COVID-19. In general, test laboratories provide rapid results during a pandemic. HIE will have to adapt and create an infrastructure to adapt to a pandemic that initially slows down the response. Even once the infrastructure is there, HIE is vulnerable because warnings must always be in real time and generally on a certain scale. During COVID-19, for example, Health Current initially provided the alerts and data without the Secure File Transfer Protocol.

MedFabric4Me does not have to adapt to a pandemic every time. Although it does not provide emergency alerts, no new functionality or complete infrastructure needs to be created to support pandemic reporting. An institute or test laboratory that conducts mass tests can provide safe results for the specific patient and those data can be exchanged further.

### Management of Medical Devices

HIE has a very specific functionality, namely to share medical records with providers' suppliers and with the participants. The medical industry is enormous, and there are several other industries involved. One of these are manufacturers of medical devices that supply medical devices to suppliers, research institutes and healthcare institutions. Manufacturers pass on the use of a device to providers or institutes. Currently, medical suppliers have a limited view of the use of the device, which results in careless service.

MedFabric4Me's policy on the partial sharing of data can help device manufacturers to have a good view of the use of the device with vendors and to trust the data. The manufacturer can determine which medical devices are required. For the rest, manufacturers can gain insight into the inventory of a particular location, which helps them make a well-considered decision as to whether they should move it within the providers at the location or call for a new machine.

With these experiments and comparisons, the researchers conclude that MedFabric4Me is a viable decentralized alternative to the current centralized alternative. Some outlined benefits of MedFabric4Me are:

- MedFabric4Me has the capacity to perform better in the field of transit.
- Decentralisation ensures that there is no single point of failure.
- MedFabric4Me reduces the overhead costs of cloud computing, expensive encryption and helps to divide costs between insurers, healthcare providers and patients.
