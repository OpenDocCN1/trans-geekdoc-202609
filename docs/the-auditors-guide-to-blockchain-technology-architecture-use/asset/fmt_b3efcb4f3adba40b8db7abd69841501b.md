
# Smart Contracts

Smart contracts are software that executes autonomously on a blockchain once it has been deployed. The storage of smart contracts on the blockchain is done openly, as smart contracts can be read and used by anyone on the blockchain. Smart contracts cannot be altered and are permanent on a blockchain. In the blockchain network, smart contract execution is done by ‘workers’ (commonly known as miners or validators) who earn cryptocurrency as a payment for smart contract execution [[53](#ch10.xhtml#r096)].

Smart contracts have characteristics that should be considered when designing a distributed system:

*   **Smart contracts are immutable**: Smart contracts cannot be modified once they have been deployed. As such, if a contract application logic has a flaw, the flaw will exist forever since there are no ways of making updates.
*   **Smart contracts are open**: In blockchain applications, one of the core principles is transparency. In other words, the records stored in the blockchain are accessible to everybody and since the smart contract is a component of the blockchain, the ‘source code’ of the smart contract can be viewed by anybody. Therefore, methods and algorithms that will be kept secret should not be implemented by smart contracts.
*   **Information that relates to smart contracts is always available**: Apart from the code of a smart contract, all blockchain users can view the values that the contract variables hold, the historical data and all the transactions that are related to the contract.

The above-mentioned attributes have implications such as:

1.  Smart contracts cannot be used for storing private data such as private keys and protected records.
2.  Smart contracts cannot be used in performing operations that require secret information, e.g., in the creation of a digital signature.
3.  Smart contracts cannot be used in generating secret information, e.g., in the generation of a secret key [[31](#ch10.xhtml#r074)].

## How Developers Ensure Users Cannot Exploit Bugs or Unintended Functionality

Having in mind that the internal code of smart contracts cannot be changed once deployed, developers are well advised to use defensive programming techniques through testing procedures, measuring the test coverage, setting up continuous integration and performing security audits on the contract which will ensure that the users cannot exploit bugs or unintended functionalities [[53](#ch10.xhtml#r096)].

Smart contract developers should consider a ‘kill switch’, which is a piece of code that will leave the smart contract inoperable permanently. Invoking a ‘kill switch’ should result in all funds associated with the smart contract being transferred to the contract owner. The kill switch should also result in the prevention of users from interacting with the referred contract in the future. It should be pointed out that even if a smart contract is ‘killed’, the code and data of the contract will remain on the blockchain [[31](#ch10.xhtml#r074)].

## Turing Completeness

Turing completeness is a property that defines programming languages used in simulating a Turing machine. Alan Turing developed the idea of the Turing machine in the 1930s. The Ethereum Virtual Machine is a well-known example of a Turing complete smart contract device [[67](#ch10.xhtml#r110)].

To verify if Turing complete languages are necessary or not, the Ethereum blockchain is evaluated for various control flow mechanisms, such as loops and recursion functions. Only 35.3% of the smart contracts use control flow mechanisms. Therefore, the use of non-Turing complete smart contracts is sensible. Note that the Bitcoin platform uses non-Turing complete languages [[44](#ch10.xhtml#r087)].

Turing completeness introduces an unwanted and burdensome attack surface along with it. A real example is the Decentralized Autonomous Organization (DAO) attack in 2016, which was triggered as a result of Turing completeness. This attack robbed 3.6 M ETH (Ether), equivalent to USD 50M. Thus, Turing complete smart contracts could be high-risk implementations [[67](#ch10.xhtml#r110)].

## Untrusted Code

Unexpected risks and failures may occur from calls to smart contracts built using untrusted code. These calls may introduce malicious code into the smart contracts. Interacting with untrusted code is unsafe. It may disrupt the control flow leading to many vulnerabilities.

To minimize the danger, it is recommended to delegate calls to trusted contracts only. When calling an untrusted contract, state changes should be avoided after the call. The use of the `call()` in the code instead of using the `transfer()` and `send()` functions is recommended [[25](#ch10.xhtml#r068)].

See [Chapter 14](#ch22.xhtml#c14) for a discussion of smart contract attacks and best practices in greater detail.

# Conclusions and Recommendations

This chapter discussed the various blockchain components, cryptographic principles and algorithms, differences between public and private and open and closed blockchains, how Merkle trees function in blockchain, blockchain-related access control concepts, the use of hashing algorithms, smart contracts and cryptocurrency wallets. This information-rich chapter is an attempt to familiarize readers with the architectural components of blockchain platforms.

# Core Concepts

*   A blockchain network is created by linking multiple nodes and running software, with transactions being requested through a wallet. This transaction is sent to all processing nodes on the blockchain network with each processing node validating the transaction against predefined rules given by the blockchain network developers. All validated transactions are then stored in a block and secured with a hash. When other processing nodes in the network confirm that the hash is right, the block is added to the blockchain signifying the completion of the transaction and establishing immutability [[20](#ch10.xhtml#r063)] ([Figure 2.10](#ch10.xhtml#f16)).

    ![Figure 2.10 Blockchain transaction lifecycle. ¶ Source: [20](#ch10.xhtml#r063) Created with Visio.](html/images/9781032078243_C002_010.jpg)

    **Figure 2.10** Blockchain transaction lifecycle. ¶ Source: [[20](#ch10.xhtml#r063)] Created with Visio.

*   There are a number of important blockchain-related roles and responsibilities. These include users, processing nodes, blockchain regulators, blockchain developers, blockchain administrators and a certificate authority. These various participants – although quite different in their network roles – exhibit synergy. These interactions are what enable blockchain transactions to be successfully generated throughout the network.

*   Blockchains may be broken down into four main categories: Public, private, open and closed. All users can read the stored data in an open blockchain but only allowed participants can read the data in a closed blockchain.

*   Consensus algorithms refer to the various mechanisms that have been developed over time to ensure agreement in blockchain transaction. This is a pivotal aspect in blockchain as it determines the speed, reliability and further development of the blockchain network. Although there are several consensus mechanisms currently available as consensus algorithms, there is room for further development of new mechanisms.

*   A nonce is a random numerical value that constitutes the heart of the proof of work consensus mechanism. The processing nodes in a blockchain network aim at producing a nonce that meets the required hash value during a PoW process (for example: a hash that starts out with four zeros). Once the PoW process produces a suitable nonce, it can be easily verified by the other participating nodes in order to reach PoW consensus. Once verified by the other nodes, the node that determined the nonce value first will get to create the corresponding block and earn the block reward; typically a cryptocurrency sum.
