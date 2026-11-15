
## A Blockchain-based Privacy-Preserving Recommendation Mechanism

Liangjie Lin
College of Computer Science and Technology
Harbin Institute of Technology (Shenzhen), China
sherlocklij@163.com

Yuchen Tian
College of Computer Science and Technology
Harbin Institute of Technology (Shenzhen), China
19s051060@stu.hit.edu.cn

Yang Liu
College of Computer Science and Technology
Harbin Institute of Technology (Shenzhen), China
Cyberspace Security Research Center
Peng Cheng Laboratory
liu.yang@hit.edu.cn

### Abstract

Recommendation system is widely used to predict users’ interests and provide targeted products for them, which effectively facilitates users in the era of big data where information overload problem is prevalent. Unfortunately, massive data closely related to users’ privacy is in high demand to produce more accurate predictions. In this case, the collection and transmission of such data is communication costly; to process and analyze such data is of high possibility to compromise users’ privacy. In this paper, we propose a privacy-preserving recommendation mechanism based on blockchain, which well addresses these problems. Leveraging the inherent advantages of blockchain, we establish a completely distributed model mitigating the risk of privacy disclosure caused by central data storage. Moreover, we combine Inter-Planetary File System with blockchain to greatly improve the communication efficiency. We also introduce local sensitive hashing and local differential privacy into proposed mechanism to reduce the computation load and provide a strong privacy guarantee. The experimental results demonstrate that the proposed mechanism shows better performance on privacy preservation while maintaining desirable recommendation accuracy when compared with the baseline.

### Keywords

big data; blockchain; privacy; recommendation; local sensitive hashing; local differential privacy

## I. INTRODUCTION

Recommendation system is proposed as a promising technology to address the information overload in the era of big data. However, massive users’ data need to be collected to improve the quality of recommendations, which brings a number of privacy issues. Efforts from legal aspects have been made to preserve users’ privacy. For example, the European parliament unanimously passed the General Data Protection Regulation (GDPR) [1], which came into effect in May 2018. After that, the California government of the United States also established the California Consumer Privacy Act (CCPA) [2], which took effect in January 2020, to ensure the privacy rights and interests of consumers. Recommendation system, having heavy demand for users’ data, is of vital significance to preserve users’ privacy in the society where privacy is widely concerned.

At present, many approaches to achieve privacy preservation are based on centralized framework under the distributed environment [3, 8]. To this end, users’ data still needs to be collected and stored in the central server. In this work, we propose a completely distributed recommendation mechanism leveraging the inherent decentralized features of blockchain. In this framework, users’ raw data are preserved locally to well reduce the risk of privacy disclosure. In addition, we apply local differential privacy technology to further minimize this disclosure.

More specifically, we followed the basic framework in [4] to implement the minimum hash algorithm based on Jaccard similarity and involve CRC32 verification algorithm for data clustering, making offline computation more efficient and secure. Moreover, we use local differential privacy on the users’ sides by adding a small perturbation to the data via the random response mechanism [5], which can further enhance the system’s ability to preserve users’ privacy. To the best of knowledge, this paper is the first to combine blockchain technology, recommendation algorithm, and differential privacy for the purpose of privacy preservation. Considering that the recommendation accuracy will be degraded due to the parameters in the clustering process and the perturbation process, we conduct experiments to demonstrate how to strike a balance. Possible privacy attacks based on the proposed system are analyzed and discussed in this paper.

Related Work. Fery et al. [6] first proposed blockchain-based recommendation framework to address privacy issues. In that framework, secure multi-party computation is leveraged for encrypting and preserving the privacy information of customers in an e-commerce system for shopping [7]. However, the analysis of efficiency as well as the accuracy of that framework were not provided. Furthermore, all the computation is processed in the blockchain, making it is impractical for the real-world deployment due to the high computational overhead. Umekwudo et al. [8] applied the blockchain to recommendation system in mobile environment, but data is still processed in the blockchain. In addition, the introduced third-party organization may expose the users under the risk of privacy disclosure. Since then, Omar et al. [9] constructed a client-driven recommendation architecture using blockchain, but they didn’t analyze the efficiency and performance of this architecture. Then, Fran Casino et al. [4] implemented the first highly efficient and scalable recommendation system based on blockchain. They combined the blockchain with the Inter-Planetary File System (IPFS) and super-bit locality sensitive. Furthermore, they proposed three recommendation strategies, effectively preserving users’ privacy and improving the computation efficiency as well as recommendation accuracy. However, in that system, only static values are used to fill the highly sparse data, which is inadequate to yield a model with high recommendation accuracy. And they only used cosine similarity for clustering the data. Besides, differential privacy was not involved in these three recommendation strategies.

## II. BACKGROUND

### Blockchain Technology

In 2008, to maintain transaction orders and avoid the double payment problem of bitcoin, Nakamoto introduced the blockchain structure. The distributed features can be utilized in many areas to provide a strong level of network security and privacy preservation. Moreover, it can provide anonymous and transparent services without the participation of third parties or other verification organizations [10].

### Inter-Planetary File System

The IPFS is a distributed file system in the form of Peer-to-Peer. It is also a hypermedia transmission protocol which is based on content addressing and able to avoid centralized failure due to the point-to-point architecture. The files are stored within the system as IPFS objects. We can enhance the availability of blockchain and IPFS by enabling off-chain storage and anonymous file sharing [11].

### Local Sensitive Hashing

The Local Sensitive Hashing (LSH) [12] is used to map the datasets via their similarity. In specific, the similar data tend to be mapped into the same bucket, while for the dissimilar data, the different buckets. Various forms of LSH can be implemented according to different similarity calculation methods. In this paper, we use binary Min-Hash algorithm based on Jaccard similarity. The details of the algorithm can be found in Section 3.2. In this case, the similarity calculation formula for dataset A and B is defined as follows:

\(J(A, B) = \frac{|A \cap B|}{|A \cup B|}\) (1)

### Local Differential Privacy

At present, differential privacy is commonly used in the centralized environment where data is collected into a central server. In this paper, we apply differential privacy directly at the users’ sides, precluding the malicious third-parties from obtaining the raw data with sensitive information and greatly enhancing the privacy preservation ability. In addition, the random response mechanism disables attackers to infer correct sensitive information from users. In this paper, we choose a local differential privacy algorithm based on Private Count Mean Sketch (PCMS [13]), the details of which can be found in section 3.3.

## III. OUR MECHANISM

In this section, we will describe the proposed mechanism based on blockchain in detail. More specifically, the mechanism consists of three main procedures. At first, LSH clustering and local differential privacy are performed locally to each user, the obfuscated data is sent to IPFS for storage. After that, each user will get a unique hash value returned by IPFS, through which, the user can have access to the data again. Then, the outputs in the last process along with other information, such as clustering results (i.e., bucket number), the hash value, the pseudonym and the current timestamp, are uploaded to the blockchain. Each user is responsible for recording those data. Therefore, users can pick up the similar hash values from the transaction data stored in blockchain. Finally, users obtain the obfuscated data for TOP-N recommendations from the IPFS via selected hash values. The illustration of the proposed mechanism is shown in Fig. 1. More details are presented in the following subsection.

### A. Mechanism Overview

![](img/ba6405dd3b4100239a8087f4ac628bd3_1_0.png)

Fig. 1. The overview of proposed mechanism.

In the blockchain, genesis block contains the LSH function required for clustering, the dimension of the data and the hash function set for PCMS calculation. Each user is required to upload a pseudonym and a timestamp to distinguish whether it is the latest data because rating of the data is dynamic. In addition, the information is allowed to be uploaded only once at a certain time interval, which is decided by the application developer.

In traditional decentralized recommendation systems, the whole cost is dominated by the data transmission between users and the server, the cost of transaction process and transaction verification in blockchain is trivial in this case. In the proposed mechanism, we have much smaller-sized data (e.g., the hash values, the timestamp, and the pseudonym) to be transmitted between blockchain and users. Moreover, the LSH clustering and differential privacy process is executed in parallel among different users. Consequently, our mechanism shows high efficiency in various aspects. Furthermore, the inherent features (such as stability, robustness, and scalability) of blockchain [4] within our mechanism are not well supported by the traditional decentralized or centralized recommendation systems.

### B. Min-Hash Based LSH

In this algorithm, each user should generate a sparse matrix where recorded item is marked as 1, otherwise 0. Then, random row permutation is performed on this sparse matrix. For each result, the number of rows with value 1 appearing for the first time in each column is recorded as a part of the signature matrix. After that, the signature matrix is divided into several bands and each band is transformed into a unique value. The corresponding bucket number is obtained by CRC32 algorithm and mod
