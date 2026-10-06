156

Blockchain

+   - Then the chaincodes will be installed on the peer nodes.
- Once the hyperledger network is up and running, then we will start the front end i.e. the web application which the doctors and patients will use to interact with blockchain.
- The web application has three users: administrator, doctors, and patients.
- The administrator can add the new hospitals in the blockchain network or remove them and for each hospital they will add a hospital administrator (Figure 9.14).
- Every hospital will have one administrator who will be managing the or removal of doctors from a particular hospital.
- The patients, after registering in the web application, can upload their medical records that will be stored in the off-chain storage i.e. cloud in our case (Figure 9.15).
- The medical records can be uploaded in pdf or jpeg and stored format.
- The patients can gain access or revoke access from a particular doctor for any of their specific medical records (Figure 9.16).
- The doctors can view the patients' records for which they have been given access to (Figure 9.17).
- The access to any of the patient's vitals data can also be given to the doctor and revoked (Figure 9.18).

# 9.10 Conclusion

We proposed an IoT-based EHR management system that solves a lot of problems, which the current electronic health record system suffers from regarding security and accessibility. In this chapter, we saw how blockchain technology can be used to overcome those problems. We also saw problems that can be solved by remotely sensing patient's vitals using IoT sensors and how that data can be stored in the cloud and can be accessed by blockchain transactions only. In the first section, a comprehensive explanation of the fundamentals needed to comprehend how blockchain technology works was provided. Then a brief explanation of different types of blockchains was provided and it found out that permissioned blockchain was relevant for our system. We also chose a hyperledger fabric permissioned blockchain network to implement our system. We then gave a description of different components and actors involved in the fabric network and the transaction flow in fabric.

In the next section, we talked about the challenges in current EHR and current health monitoring systems and motivation for this system. A detailed overview about our system was provided. We then talked about the architecture of our system and the workings of our system. The next section provided the pseudocode of the algorithms used in system. Finally, in the last section, to tie everything together, a detailed description and its implementation details were provided. Security and controlling access to the medical records are the most prominent challenges in the existing electronic health record system. So, this chapter presents a system that can transform the healthcare sector and can be used to solve a lot of the mentioned problems present in the healthcare sector. The whole system is built around hyperledger fabric, which is a permissioned blockchain and the proposed system is completely patient-centric. [1,3-20]