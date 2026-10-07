
# Blockchain, AI, and Data Protection in Healthcare

![](img/22da15453f020b9665d0b01ac32670f9_143_0.png)

**Figure 6.1** Overview of roles and process flows (diagram created by Meng Kang).

incorporates a Hyperledger cloud agent. The individual uses a mobile app with an agent. Agents can connect with other agents for messaging, credential issuing, and proof presentation.

To prevent the misuse of status permissions, permissions have a limited duration of validity. Never have a token that is valid indefinitely. This gives the, as controller of their own data, temporal control over active permission tokens as authorization capabilities. The signed URL is a query string authentication that has been used by most cloud storage providers as part of cloud storage access control mechanisms, which represents a concept of providing temporary access to specific resources [25]. All cloud service providers have an implementation of this technique, which is referred to as Signed URL in Google Cloud Storage [26], SAS in Microsoft

## Blockchain and Artificial Intelligence-Based Solution

132

![](img/22da15453f020b9665d0b01ac32670f9_144_0.png)

**FIGURE 6.2** Data issuing and storage architecture (diagram created by Meng Kang).

Azure, and presigned URL in Amazon Web Services (AWS) [27] for purposes of granting temporary access. This solution uses the AWS presigned URL. This URL is embedded as an attribute of the storage credential.
Figure 6.3 shows the architecture of licensing and consumption. Similar to the previous part, the distributor and consumer have their web app with Hyperledger cloud agent. The Individual uses a mobile app with an agent.

![](img/22da15453f020b9665d0b01ac32670f9_144_1.png)

**FIGURE 6.3** Licensing architecture (diagram created by Meng Kang).

# Blockchain, AI, and Data Protection in Healthcare

## 6.2.2.4 Computational Processing of Data

The FHE adopted in this solution is a kind of cryptography scheme which allows operations on encrypted data without decryption. Currently, the Xeon-Kim-Song (CKKS) FHE scheme [28] is the most effective method of performing approximate homomorphic computations over real and complex numbers. By going exact computations, the CKKS scheme achieves significant improvements in the ciphertext/plaintext ratio and algorithm speed. Therefore, this scheme is adopted in our solution as an encryption method for preserving the privacy of personal data. To prevent consumers from sharing homomorphically encrypted data, the design suggests that some level of protection and monitoring by the data manager as a service provider is required. These architectural enhancements require further research and involve the concept of a ‘secure enclave’. Due to the effort and complexity of developing such an environment, this feature remains future work for this solution.

Snippets of code and screen shots from an implementation of the SSI data marketplace can be found in the Appendix.

## 6.2.3 Case Study: Ocean Protocol Data Marketplace

### 6.2.3.1 Introduction

Ocean Protocol (OP) is an Ethereum-based decentralized protocol which follows a systematic approach for unlocking data for AI analysis with the verification of eligibility, proofs of payments, and acceptance of terms and service level agreements [29, 30]. The overall goal of OP is to allow data providers to monetize their data in a privacy-preserving manner and consumers to obtain value from accessing and processing the data.

The data within OP marketplace cannot be accessed directly if the compute-to-data approach is used. Data tokens that use the Ethereum ERC20 token standard are utilized to provide access to the data [30]. The data stays on individual data providers’ primitives and consumers can only perform computations on the data after accessing the data using a data token [30]. The OP decentralized database maintains record of every transaction.

The data can be transferred to a third party in exchange for the OP tokens [29, 30]. Any organization with access to a data token has compute access to the data. In other words, each data token provides a license to access the data [29, 30].

### 6.2.3.2 Preliminaries

As a foundation to understanding the solution design, we present some preliminary concepts and technical primitives based on V2.0-3.0 of OP as follows:

- Data NFT, a nonfungible ERC721 token representing copyright of a data service.
- Data Token, in the context of OP, an ERC20 token for gaining compute access to the data.
- Ocean Token, the token-based currency used in the OP marketplace.

# Blockchain and Artificial Intelligence-Based Solution

- Metadata, details used for asset discovery in the marketplace comprised of data asset, name, creation date, etc. Each asset has a DID specific to it and a DID document for each metadata field. Fields and metadata can vary from one marketplace to the other.
- DID Document (DDO), a JSON document with metadata fields comprising of ID and signatures derived from the DIDs.
- Aquarius, a store of asset metadata. It is used for storing DID DDO.
- Ocean DB manages the published data tokens in the OP marketplace.
- Operator Engine, a backend service responsible for providing necessary infrastructure for compute services and for executing the compute services in the Kubernetes (at the data provider's end).
- Automated Market Markers, used for the automatic price discovery in the marketplace. Example: Balancer, in which the token sale is directly proportional to the price of data tokens.
- Gas, fee or pricing value which is required for the execution of transactions and contracts on Ethereum.
- KB Cluster, a platform at the data provider's end responsible for managing the compute service on data stored in containers.
- Compute-to-Data, a mechanism by which data consumers perform computations on the data on premises of the data provider.
- Compute Algorithm, the algorithm used in the compute-to-data service.
- EVM store, a secret store that hides the location of the data on the data provider's premises.

### 6.2.3.3 Roles

- Data Provider, in the context of OP, data providers are the organizations or group of individuals who are willing to sell their data in exchange for Ocean Token.
- Brizo (also known as Provider), serves as a data access control proxy of the data provider. It is the only component that can directly access the data location. It performs checks on chain for buyer permissions and payments; encrypts the data URL and metadata during publication; decrypts the URL when the dataset is downloaded or a compute job is started; provides access to data assets by streaming data; and computes services (to C2D environment).
- Operator Service, service responsible for performing computations on the data based on the confirmation provided from the data provider's proxy Brizo (Provider).
- Data Consumer, data consumer who is authorized to obtain access to the data for performing in exchange for Ocean token.
- Keeper, a node which is basically a set of smart contracts that maintains a registry of asset ownership and makes sure that all the nodes are running correctly within the system.

# Blockchain, AI, and Data Protection in Healthcare

## 6.2.3.4 System Architecture

The OP marketplace has a decentralized backend. However, there can be multiple frontiers. The backend Architecture is presented below in Figure 6.4.

To interact in the marketplace, a data provider uploads their URL to a storage location using AWS, Google Drive, or a decentralized data store like Filecoin [29, 30]. In V2.0 of OP, the URL of the data is stored in a secret store – a cluster of EVMs [29], where EVM stores a fragment of a data location URL – but this component has been deprecated in a more recent version of the marketplace and the Brizo (Provider) now encrypts the URL and stores it on chain. The Brizo (Provider) also manages encryption when it receives a request for access to the data. To make the data available on the marketplace, the data provider 'publishes' the data using the Ocean NFT Factory, which creates a new NFT. In an earlier version, only ERC20 tokens were used. However, since datasets are typically shared more than once among many people, OP now makes a kinda NFT to define the ownership rights, with each NFT having one or more data tokens to separately define and access rights.

The Keeper node is used for running keeper contracts (a set of smart contracts) [29]. It makes sure that all the nodes are running correctly within the system. It is responsible for registering the data and maintains a registry of data ownership [29]. It makes use of the EVM and solidity technology and registers the metadata for the published data on chain using DIDs [29].

Data is not published on the OP marketplace; rather, it is the metadata and data tokens that are published [29, 30]. Metadata consists of fields such as the URL of the published data token, data token price, dataset name, description for the data, and so on on [29]. DIDs for the data are hashed onto the metadata and are registered on-chain using Keeper contracts [29].

![](img/22da15453f020b9665d0b01ac32670f9_147_0.png)

** 6.4** Data sharing and storage architecture (diagram created by Deepansha Chhabra).
