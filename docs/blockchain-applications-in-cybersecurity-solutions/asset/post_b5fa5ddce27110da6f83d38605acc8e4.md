
the corresponding smart contract to generate an access token. A contract will keep the token stored in persistent memory on the contract's server rather than transmitting it to the client. Tokens are stored in the internal contract storage, and then clients request the key to decrypt them from the key server, which is a blockchain node that maintains a copy of the Blockchain ledger. The key server verifies a client's access token on the blockchain and transmits the key using DTLS channels after checking the smart contract storage on the Blockchain. The client then downloads the encrypted resource from the proxy server and decrypts it.

Researchers in the study [15] used smart contracts to solve the scaling problem associated with IoT authentication. Typically, an individual owns one or more IoT devices, and each device requires its own set of credentials. Therefore, it is necessary for the user to authenticate to every device individually from this point onward. As a consequence, this method causes an authentication overhead and is difficult to scale. Smart contracts are used primarily for authenticating users and providing them with a token that allows them access to the IoT devices which they own. Users authenticate to the smart contract using their Ethereum wallet address, which allows the smart contract to verify the user's identity. A contract is subsequently negotiated if the user is allowed to access the resources, and the key is then communicated to the end user and to the IoT device. The user will then sign the received token using his private key, send it to the IoT device that will take the token and confirm its integrity by comparing it with the instance received earlier from the contract and then grant access. The Ethereum blockchain has been used to implement and test this approach. A general approach for blockchain-based access control for IoT has been shown in (Fig. 1).

![](img/1b14bb2748aa86be47fb2952ff28da51_138_0.png)

## CONSENT FOR PUBLICATION

Not applicable.

## CONFLICT OF INTEREST

The author declares no conflict of interest, financial or otherwise.

## ACKNOWLEDGEMENT

Declared none.

## REFERENCES

- [1] S. Rouhani, and R. Deters, "Security, performance, and applications of smart contracts: A systematic survey", *IEEE Access*, vol. 7, pp. 50759–50779, 2019. [http://dx.doi.org/10.1109/ACCESS.2019.2911031]
- [2] Vincent C. Hu, David Ferraiolo, Rick Kuhn, Arthur R. Friedman, Alan J. Lang, Margaret M. Cogdell, Adam Schnitzer, Kenneth Sandlin, Robert Miller, and Karen Scarfone, "Guide to attribute based access control (abac) definition and considerations (draft)", *NIST special publication*, vol. 800, no. 162, pp. 1–54, 2013.
- [3] R.C. Merkle, "A digital signature based on a conventional encryption function", In: *Conference on the theory and application of cryptographic techniques* Springer: Berlin, Heidelberg, 1987, pp. 369–378.
- [4] C. Dwork, and M. Naor, "Pricing via processing or combating junk mail", In: Annual international cryptology conference Springer: Berlin, Heidelberg, 1992, pp. 139–147.
- [5] NIST, US, Descriptions of SHA-256, SHA-384 and SHA-512,
- [6] Preneel, Bart, Antoon Bosselaers, and Hans Dobbertin. "The cryptographic hash function RIPEMD-160." (1997): 9–14.
- [7] D. Johnson, A. Menezes, and S. Vanstone, "The elliptic curve digital signature algorithm (ECDSA)", *Int. J. Inf. Secur.*, vol. 1, no. 1, pp. 36–63, 2001. [http://dx.doi.org/10.1007/s102070100002]
- [8] M. Pilkington, Blockchain technology: Principles and applications. *Research handbook on digital transformations* Edward Elgar Publishing, 2016. [http://dx.doi.org/10.4337/9781784717766.00019]
- [9] S. Huckle, R. Bhattacharya, M. White, and N. Beloff, "Internet of things, blockchain and shared economy applications", *Procedia Comput. Sci.*, vol. 98, pp. 461–466, 2016. [http://dx.doi.org/10.1016/j.procs.2016.09.074]
- [10] M. Michael, and M. Smith, "Sharing ledgers for sharing economies: An exploration of mutual distributed ledgers (aka blockchain technology)", *Journal of financial perspectives*, vol. 3, no. 3, 2015.
- [11] D.D.F. Maesa, P. Mori, and L. Ricci, Blockchain based access control. *IFIP international conference on distributed applications and interoperable systems* Springer: Cham, 2017, pp. 206–220.
- [12] O. Novo, "Blockchain meets IoT: An architecture for scalable access management in IoT", *IEEE Internet Things J.*, vol. 5, no. 2, pp. 1184–1195, 2018. [http://dx.doi.org/10.1109/JIOT.2018.2812239]
- [13] A. Outchakoucht, H. Es-Samaali, and J. Philippe, "Dynamic access control policy based on blockchain and machine learning for the internet of things", *Int. J. Adv. Comput. Sci. Appl.*, vol. 8, no. 7, pp. 417–424, 2017. [http://dx.doi.org/10.14569/IJACSA.2017.080757]
- [14] O. Alphand, M. Amoretti, T. Claeys, S. Dall'Asta, A. Duda, G. Ferrari, F. Rousseau, B. Tourancheau, L. Veltri, and F. Zanichelli, "IoTChain: A blockchain security architecture for the internet of things", 2018 IEEE wireless communications and networking conference (WCNC), 2018 pp. 1-6
- [15] A.Z. Ourad, B. Belgacem, and K. Salah, "Using blockchain for IOT access control and authentication management", In: International Conference on Internet of Things Springer: Cham, 2018, pp. 150-164. [http://dx.doi.org/10.1007/978-3-319-94370-1_11]

## INTRODUCTION

The Blockchain is a series of blocks, each of which holds valuable data that is not supervised by a central authority. It is unchangeable and cryptographically secure. Linked Lists and Pointers are two significant data structures used in a blockchain. The Blockchain is redefining ways of handling trustworthy transactions. The internet is incredibly vulnerable, and Blockchain [1] has been released as a result of this. Blockchain defines the confidence liability lines as one challenge for AI and IoT. The majority of IoT devices communicate with one another on public networks, and it is superfluous to discuss how vulnerable public networks are. Blockchain [2] overcomes this challenge by allowing users to create linear and long-lasting indexed records. They can also make the business process go more smoothly by offering a payment mechanism and a communication channel. Any kind of hacking and tampering with the data, like captivating control of devices and records, is excruciating by the way blocks are stored and guarded in an unambiguous database in the Blockchain outline. Every IoT device is a point of vulnerability, and the hazards are still higher as even AI is intricate in making choices for users. Hence, Blockchain can provide a safe, scalable, and certifiable platform with superlative security implementations [3].

## BLOCKCHAIN AND SMART CONTRACTS

### Implementation Techniques for Blockchains

To develop a realistic and effective blockchain application environment, a number of fundamental concerns must be addressed [4]. The four levels of a unique blockchain ecosystem are smart contracts, Blockchain, services, and user interfaces. Enterprise network models, participants, ecosystem design, admission policies, nodes, polling systems, incentive mechanisms, smart contracts, and clients are all examples of blockchain implementation strategies. Furthermore, to solve the problematic issues of blockchain applications, data collecting and data processing methods are required.

The majority of current projects are struggling with the blockchain network concept [5]. Blockchain technologies are still changing, and no widely acknowledged technological pattern exists. Due to their inefficiency and high-performance costs, specific Bitcoin-based projects have not been recognised. Self-designed hybrid networks or alternative network architectures are being used in an increasing number of applications.

A typical blockchain ecosystem includes a blockchain infrastructure, participants' information systems with programming edges to the Blockchain, and a set of smart contracts for operation. All data and communications are stored in a
