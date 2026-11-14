
the working of blockchain and its prominent use-cases. This will be followed by analyzing the traditional systems in healthcare and then we will look at an overview of how blockchain technology can reform the healthcare industry.

## Technical Aspects of Blockchain

In its essence, Blockchain is a distributed public ledger. In other words, it is a decentralized database. There is no central authority in charge of its functioning and maintenance. This is the reason it enables peer-to-peer transactions, eliminating the need for a middleman. As the name suggests, a blockchain is a linear arrangement of blocks, which are its data units. These blocks can store data ranging from transaction records to medical records and even media. This linear arrangement is like an append-only data structure. New blocks can only be added to one of the ends of this chain. Every block has a hash value that uniquely identifies it. Further, the block also contains the hash value of the block previous (otherwise known as the parent block), which forms a link. The very first block of a blockchain, which has no parent block, is known as the genesis block.

Since there is no entity to verify which blocks are to be added to the ledger, blockchain makes use of various consensus algorithms to validate new blocks. All participating users agree to abide by a pre-defined consensus algorithm to decide on the concurrent state of the ledger and allow the blockchain to facilitate “trustless” transactions within the network. Every new block needs to be verified by the consensus algorithm before being introduced into the blockchain. The time it takes to verify and append a new block is known as the Block time of the network. It is about 10 minutes for the Bitcoin blockchain and about 20 seconds for the Ethereum blockchain [3]. Proof of Work (PoW) is a widely used and robust consensus algorithm that is used in the Bitcoin blockchain. It uses cryptographic hash functions, like SHA 256 to enforce security and integrity. A cryptographic hash function uniquely maps input data to a corresponding hash value. Also, it is a non-reversible function, so it is practically not possible to compute the input data from a given hash value. PoW protocol requires the users to put in some computational work to obtain a hash value for a block that satisfies some predefined condition. This condition is usually a number known as a nonce, which sets the “difficulty” for computing the hash. For example, the nonce can define the number of zeros for which the hash value must begin. Due to the “Avalanche Effect”, even a small change in the input data completely alters the corresponding hash value. Hence, the users who want to add a block have no other option but to brute-force till they find a combination that satisfies the given hash condition. Once a combination is found, other users in the network can simply run this combination with the cryptographic hash function and confirm whether it satisfies the condition or not. This process of adding blocks to the blockchain is known as mining and the users who put in the computational effort to add the blocks are known as miners (see Fig. 1).

![](img/acd73a27093a44d669c4d9968aa1626b_77_0.png)

Fig. (1). Sequential working of Blockchain.

Some other consensus algorithms are Proof of Stake, Proof of Burn, and Practical Byzantine Fault Tolerance. While these algorithms differ in the way they are implemented, their functions remain the same; to validate new blocks and to make sure that only one version of the database exists in the entire network [4].

## Applications of Blockchain

As of 2020, blockchain has been researched and implemented in numerous fields, proving the versatility of this technology. Following are some examples.

## Voting

Blockchain has the potential to revolutionise voting. A blockchain-based voting framework can offer security, privacy, reliability, and non-tamperability to higher standards than the traditional voting methods. The immutability of blockchain ensures that once a vote is placed, it cannot be tampered with. Tampering of votes remains a grave issue with traditional voting methods. In 2020, Malawi’s constitutional court ordered re-election after investigations revealed that tallying forms had been tampered with in the general election of 2019 [5].

Blockchain allows voters to anonymously cast votes after some authentication. Further, it can maintain a real-time count of the votes cast. This saves the time spent in the collection and calculation of votes. This is exemplified by the 2019 fisheries council advisory board election in which the South Australian government contracted a blockchain-based startup Horizon State to host blockchain-enabled voting. The month-long election’s result was immediately published once the voting concluded [6].

## Identity Management

We often associate ourselves with different institutions or organizations that can be both public and private. To authenticate ourselves as a member of an institution or a valid benefactor of a scheme, we are given some sort of identity proof by the authorities. Moreover, to enrol ourselves in some new institutions, we may be required to present a set of previously owned identity proofs. Maintaining a separate identity proof for different purposes is a tedious task for consumers. Further, managing a centralized identity management system is effort and resource-consuming for the organization as well. The aspect of decentralization in blockchain technology can help alleviate these limitations.

A distributed ledger-based framework for identity management can help in securely maintaining personal identification information and also allowing this information to be seamlessly accessible whenever and wherever required. uPort is an example of such a framework that uses the Ethereum blockchain for identity management. It is an open-source project which aims to provide users to own and maintain digital identity and assets. Further, it facilitates secure disclosure of information to other users or organizations when required [7]. Another example of blockchain-based identity management is the Illinois Blockchain Initiative which aims to register the digital identity of citizens right at birth. Only the individual or their guardian will have permission to access the cryptographically sealed identity attributes [8].

## Real Estate Records Management

Ownership of real estate is often a matter of dispute. This dispute can be between people, government, and people, or even between governments. In India, for example, land records are sometimes maintained by multiple authorities which may have conflicting information regarding the same land. Thus, these disputes are not easily resolved. Land registry is also a tedious process that requires the involvement of many stakeholders and middlemen. Blockchain technology, with the power of immutability and smart contracts, can help in tracking ownership records and ease the registration process.

In 2017, the government of Andhra Pradesh in India collaborated with Chromaway, a Swedish company, to set up a blockchain-based land registry system with the aim to reduce errors and administrative burdens [9]. Similarly, in 2019, South Burlington in the USA initiated a blockchain-based land title registry with the help of Propy, a real estate transaction management platform [10].

## Traditional Technology in Healthcare

The Healthcare industry currently follows an institute-centric approach to health record collection resulting in hospitals and practitioners being solely responsible for the storage, sharing, updating, and collection of patient records. Let us look at how patient records are stored by hospitals.

## Electronic Health Records

Earlier, most practises used Electronic Medical Records (EMR) before the implementation of Electronic Health Records (EHR). Despite sounding similar, EMRs and EHRs are vastly different. EMRs are essentially the digital form of a patient’s chart from only a particular practice, i.e. different hospitals will have different EMRs for the same patient disregarding patient history. However, with the advent of medical tourism, immigration and the growing popularity of second opinions, real-time data sharing became the need of the hour making EHRs an indispensable tool to promote interoperability of medical records. EHR is now the most common form of digitally storing medical records which were specially built to share data with other healthcare providers and organizations.

Even though switching from paper to digital records aids secure and efficient data management, certain caveats need to be followed.
