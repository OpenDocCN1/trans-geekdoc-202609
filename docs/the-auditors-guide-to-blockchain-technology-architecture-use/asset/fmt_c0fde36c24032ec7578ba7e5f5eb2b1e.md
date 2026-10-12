
## Hardware Wallets

*Hardware wallets* are physical devices for storing private keys and data such as the account balance. A primary example of a hardware wallet is KeepKey, illustrated in [Figure 2.7](#ch10.xhtml#f13).

![Figure 2.7Example of a hardware wallet. ¶ Source: [46].](html/images/9781032078243_C002_007.jpg)

[Figure 2.7](#ch10.xhtml#f13b)Example of a hardware wallet. ¶ Source: [[46](#ch10.xhtml#r089)].

Hardware wallets, generally, are the most secure. As such, the owner’s cooperation will be required to unlock it, in case of confiscation. However, in the case of losing the PIN or the device, the recovery capability can be used. If the investigator understands the recovery steps, the coins may be accessed without the need to recover the PIN.

### Cold Wallet or Cold Storage

Cold storage refers to any key that is kept offline. It could be on a USB key, a paper note or a hardware wallet. Although there may be a key that is stored offline and there would be a need for it to be imported into a wallet to transfer funds out, the offline wallet will still be able to receive coins from the sender. This is because the coin was never received but it only references the address on the blockchain. As such, an address and its private key or a backup stored on a piece of paper in the safe can still get richer while being completely offline.

Setting up a paper wallet is very easy. The private key can be written and stored on a piece of paper and kept somewhere safe like a bank safety deposit box. Public/private key address pairs can also be generated without being online. The paper wallet is very secure because the key pair can be generated, and the private key would never have to appear in a wallet or on a computer until any funds received need to be moved to the public key address.

A useful tool for generating a public/private key pair is a free application called *WalletGenerator*, a universal paper wallet generator for cryptocurrencies [[34](#ch10.xhtml#r077)] ([Figures 2.8](#ch10.xhtml#f14) and [2.9](#ch10.xhtml#f15)).

![Figure 2.8Example of a wallet generator. ¶ Source: [78].](html/images/9781032078243_C002_008.jpg)

[Figure 2.8](#ch10.xhtml#f14b)Example of a wallet generator. ¶ Source: [[78](#ch10.xhtml#r121)].

![Figure 2.9A generated public/private key pair ready to print in a paper wallet. ¶ Source: [78].](html/images/9781032078243_C002_009.jpg)

[Figure 2.9](#ch10.xhtml#f15b)A generated public/private key pair ready to print in a paper wallet. ¶ Source: [[78](#ch10.xhtml#r121)].

### How Are Keys Stored in a Wallet?

Wallets store keys in several ways. These methods describe the ways public keys are created from a single or many private keys. Understanding how keys are created is important because it can help in tracking wallets used by individuals or organizations with complex transaction needs. These methods are divided into three primary categories:

*   **Nondeterministic**: Also known as Type-0 or *just bunch of keys* (JBOK). Nondeterministic keys are stored in a simple list of public/private key pairs. This method means that there are a lot of keys that need to be managed. It also means that a lot of data need to be backed up or kept safe.

*   **Deterministic**: Also known as Type-1 or seeded wallets. In deterministic wallets, all the private keys are obtained from a single seed that is based on a random number. This method is considerably better because the seed only needs to be stored and backed up to be able to recover all the private keys generated. This makes managing the wallet much easier.

*   **Hierarchical deterministic**: Also known as HD wallets. This is the most up-to-date wallet protocol that is in use and was implemented in the Bitcoin core in 2016. As with the deterministic wallets, all the private keys are obtained from a single seed, but the keys in an HD wallet can generate their own private and public keys in a hierarchical structure. Also, the seed can be backed up, and the backed-up seed can be used to recover the entire structure of the tree. The seed is often represented by a series of 12 to 24 words [[34](#ch10.xhtml#r077)].

## Inter-Planetary File Systems

An Inter-Planetary File System (IPFS) is a protocol that allows media to be stored on a distributed file system [[40](#ch10.xhtml#r083)]. It generates a unique fingerprint (Hash) when a file is added and removes duplicate files across the network [[17](#ch10.xhtml#r060)].

IPFS is a decentralized file system whose functionality core is created by applying the distributed hash tables (DHT) and Merkle-directed acrylic graph (DAG) data structures [[40](#ch10.xhtml#r083)].

IPFS is essentially a decentralized peer-to-peer sharing application, because there are no superior nodes in the system and unlike a typical decentralized file system that would save a file until it is deleted by a user, IPFS saves only files that are being used and ensures that they remain immutable [[62](#ch10.xhtml#r105)]. Therefore, less used files are automatically deleted from the network. This attribute of the IPFS is a major reason why it is seemingly impossible to have a successful distributed denial of service attack on the network [[56](#ch10.xhtml#r099)].

The sub-protocols of IPFS are as follows:

*   **Identities** ensure that processing nodes’ identities are generated and verified as genuine.
*   **Networks** ensure that there is seamless connectivity to other networks and optionally check the integrity of messages sent in the network.
*   **Routing** ensures the exact delivery of information in the network to the intended recipient.
*   **Exchange** ensures data distribution is seamless. *BitSwap* is used to serve as a medium for nodes to gain the blocks they need.
*   **Objects** are used to represent data structures and communication hierarchy in a network.
*   **Files** ensure that there is a clear hierarchical structure in file systems.
*   **Naming** ensures the use of the self-certifying mutable name system [[17](#ch10.xhtml#r060)].

IPFS has a name service called *Inter-planetary Name System* (IPNS). IPNS allows IPFS files to be identified by names that are easy to identify and understand by users. This is helpful for users to easily identify a file to be downloaded after an update has occurred.

An advanced feature of IPFS is that it supports file versioning using data structures like GIT, a type of software used for identifying and tracking any changes in files and also to enhance coordinated work during software development among multiple people. IPFS also makes use of directories and files using the mountable file system known as File System in User Space (FUSE) [[62](#ch10.xhtml#r105)].

There are four types of IPFS files as follows:

*   **Blob** is a representation of a major part of a stored file in the IPFS.
*   **List** is a representation of a complete file of a combination of blobs and other lists designed to compress data in the network.
*   **Tree** is a representation of a directory. It holds a combination of blobs, lists, trees and commit.
*   **Commit** is a snapshot of the history of any file on the network.

Since every file in the network is identified by its hash, the hash of a category is required to download any file. For example, to download a snapshot of a file, the hash of the IPFS Commit is required [[40](#ch10.xhtml#r083)].

## Smart Contracts

Nick Szabo postulated smart contracts in the late 1990s in an article entitled *Formalizing and Protecting Partnerships on Public Networks*. A smart contract is a secure and decentralized program that runs on top of the blockchain. It represents an agreement that is executable and enforceable automatically when certain conditions are met. A smart contract is a decentralized framework. The blockchain mechanism’s major privacy benefits made blockchain a standard decentralized model for smart contracts [[14](#ch10.xhtml#r057)].

### Smart Contract Lifetimes
