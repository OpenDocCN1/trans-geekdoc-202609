
## 11.4.1 APPLICATIONS OF BLOCKCHAIN

Since its inception, the financial industry is the major beneficiary of blockchain technology; the most popular application is cryptocurrency. Looking at its potential, other industries are also exploring opportunities. We are discussing herewith financial services, government uses, health care, industrial applications, and Internet of Things (IoT) only.

### 1. Financial services [18,19]
Blockchain is effective in taking care of the financial services like commercial financing, trade finance, cross-border transactions, and digital payments. It can play important role in providing sustainable economic growth. To provide end-to-end visibility of financial resources, blockchain is proven technology.

Organizations can trace and maintain their commercial financing with suppliers and its credit details effectively. It will help in reducing number of disputes and time to resolve disputes. Businesses need to interact with various legal entities and fulfill legal requirements. Blockchain will help businesses in the area to maintain contracts and keep updating the same with various business entities. It will simplify the business processes.

MNCs need access to multiple currencies along with facility to maintain transactions in the local currencies to run businesses. Such transactions and its reconciliations will be taken care effectively with the help of blockchain technology. It will provide visibility of transactions and balances across multiple locations.

Banking institutions are using blockchain as a disruptive technology to resolve the traditional banking problems such as nonrepudiation, transparency, traceability in a cost-effective way. R3 [18], like blockchain application, is used in the banks to settle cryptocurrency payments, general banking applications, loan management, and financial auditing. Crowdfunding [20] is another business functions that can be thought of through blockchain technology. Various blockchain applications such as Prediction Marketplace systems, BitShares 2.0, Plasma, and Global Payments Steering Groups are already in use to deal with banking services.

### 2. Government Uses [18]
Government provides services to the citizens and enterprises. Different stakeholders such as beneficiaries, bureaucrats, policy makers, and community organizations need frequent interactions and exchange of information. Government needs to maintain records of these transactions as proof of ownership and proof of existence. Blockchain could provide better solution to the existing procedures. Blockchain will enhance accountability and safety of the records. It will enhance operations performance by automating governance. Services like citizen identification certificates, maintaining the records of the public assets, tracking its uses, record keeping and maintaining legal documents related to the public and private entities, various permissions issuing to the stakeholders, tax payments can be taken care by blockchain applications in a better way. Blockchain could help better in integration of physical assets and its integration with digital contents. This will
help in reducing bureaucracy and improving the operational efficiency of the government services. Online voting could be possible along with the integration of government services as blockchain records are immutable, traceable, decentralized public ledgers along with great transparency.

### 3. Healthcare [3]
Healthcare is another area where blockchain would be effective because of its features such as immutability, distributed public ledger, transparency, availability of required information in a secure way by maintaining privacy. Blockchain will solve the problem of stakeholder’s integration in healthcare supply chain management effectively. Healthcare functions such as maintaining patient healthcare records, clinical trial, public health scheme records, drug counterfeiting, automating health insurance mechanism, and accounting would be taken care by blockchain technology in a better way. While performing these operations, privacy and security are of most concern, which blockchain will take care of?

### 4. Industrial applications [18]
Business or industry tracking of movement of goods under process or processed goods is very important in order to attain the business objectives. Similarly, tracking the various business services and its optimization is very important to satisfy stakeholders. Business operations such as purchase management, customer relationship management, supply chain management, production and operations management need to be taken care. Visibility of the production process and its associated services could be well taken care with the help of blockchain technology. Blockchain technology features make these operations effective and efficient. This will provide various opportunities in the area discussed above and support business to flourish.

### 5. IoT applications [18]
This is one of the most challenging but yet growing field in which smart devices interact with each other using the Internet. These devices generate huge data. The data that is generated by these devices in the last two to three years is almost equal to the data that is already the world is having. Major problem of this field is security of data generated by different smart devices within distributed nature of wireless networks. As we have discussed that blockchain is distributed public ledger, it would best take care of this huge data and its security. Blockchain will also help in payment settlement mechanisms among these smart devices throughout the world in cost-effective and more secure way.

These are the potential areas where the opportunities of blockchain can be explored. There are certain challenges of the blockchain technology itself along with area-specific challenges which we need to address.

## REFERENCES
- 1. Satoshi Nakamoto, “Bitcoin: A Peer-to-Peer Electronic Cash System,” December 17, 2019 18.22, https://www.bitcoin.org.
- 2. Arati Baliqa, “Understanding Blockchain Consensus Models,” Persistent Systems Ltd, (2017):3–14

- 12.4.1 Demo of the Hyperledger Fabric Network ........................................ 206
- 12.4.2 Prerequisites ........................................................................ 208
- 12.4.2.1 Docker ............................................................................. 208
- 12.4.3 Docker-Compose Services Configuration ........................................ 209
- 12.4.3.1 Orderer ............................................................................. 211
- 12.4.4 Crypto-config.yaml configuration .................................................. 213
- 12.4.4.1 Configtx.yaml Configuration .................................................. 215
- 12.4.4.2 Organizations ...................................................................... 216
- 12.4.4.3 Capabilities ......................................................................... 216
- 12.4.4.4 Channel Defaults .................................................................. 216
- 12.4.4.5 Application Defaults ............................................................... 217
- 12.4.4.6 Orderer Defaults .................................................................. 217
- 12.4.4.7 Profiles ............................................................................... 218
- 12.4.4.8 Channel Profile .................................................................... 218
- 12.4.5 Commands ................................................................................. 218
- 12.4.6 Chaincode .................................................................................. 222
- 12.4.6.1 Stub, Getstate, Putstate, getQueryResult, getHistoryForKey .......... 224
- 12.4.7 REST API ................................................................................... 226
- 12.4.7.1 Fabric SDK ............................................................................ 226
- 12.4.7.2 User Interaction API using the Fabric SDK (NodeJS) ..................... 227
- 12.4.8 Hyperledger Explorer .................................................................... 234
- References .......................................................................................... 235

## 12.1 INTRODUCTION

### 12.1.1 PERMISSIONED BLOCKCHAIN
It is possible to architect, access, and manage a blockchain [1] in multiple ways. Some blockchains [1] need exceptional permissions for reading, transacting, writing, and accessing information about them. Such blockchains inherent configuration controls the interactions of the participant and defines their roles. Such blockchains are called permissioned blockchains.

A permissioned blockchain facilitates auxiliary security by providing an access control layer to the blockchain network, which permits only well-defined identities to transact with the distributed ledger in the network, without making data public. Permissioned blockchains permit different levels of permissions to be designated to its users; therefore, access can be restricted, sufficing confidentiality. A participant may join the network without any permission but may need authorization for transacting within the network. Hence such blockchains are favored by individuals who within the blockchain need to define security, identity, and role. Authorized blockchains are common among companies and businesses at the industry level, for which security, identity, and role management are relevant. A few advantages of a permissioned blockchain are listed below:
