
![](img/115a7d47166d21dfa1d1dc5986da244b_24_0.png)

**FIGURE 1.1** Bitcoin transaction.

A wallet maintains the balance of unspent transaction outputs. If no such copies are maintained in the wallet, it can always request the network to retrieve the information. Various application programming interfaces (APIs) are available to do this task. Once the required amount of Bitcoin is available in the wallet, it can create the output of the transaction.

### 1.4.3 Creating the Output

A script is created for the transaction output by which the transaction values can be redeemed by providing a solution to the script; that is, whoever provides the signature from the key corresponding to the recipient’s public address. As the destination wallet will have the key with respect to that address only, the intended recipient can provide the signature required and can redeem the coins. At last, for the transaction to happen in a proper way, the wallet application of the sender will charge a small fee. This charging will not be explicit; it is the difference between the inputs and the outputs. This transaction fee will later be collected by the miner to validate and add a block in the network.

To manage the input and output, Bitcoin uses a scripting language which imposes the conditions to be met to redeem the Bitcoins. The most popular script is “Pay-to-PubkeyHash” (P2PKH). It needs only one signature of the owner to approve the payment. In contrast, another script “Pay-to-ScriptHash” uses multisignature addresses for various transactions.

The schematic representation of a Bitcoin transaction is shown in Figure 1.2.

![](img/115a7d47166d21dfa1d1dc5986da244b_25_0.png)

**FIGURE 1.2**  Bitcoin transaction summary.

## 1.5 Timestamp Server

The timestamp server functions by taking hash of a block comprising transactions and distributing them to the public like newspapers or Usenet. The purpose of the timestamp server is to guarantee that a block of transactions actually exists at the time of timestamp. This allows the nodes to verify the order in which the transactions are distributed. Hence, it is possible for the users to have a history of all transactions over the network. Figure 1.3 shows the process of time stamping.

![](img/115a7d47166d21dfa1d1dc5986da244b_26_0.png)

**FIGURE 1.3**  Timestamp server.

## 1.6 Proof of Work

In Bitcoin, multiple copies of blockchain exist in the network, and it is necessary to keep the global view of the blockchain consistent. For example, two different transactions can be created using the same coins to different receivers, which is called “double spending”. And if the two receivers process and get their transactions verified individually based on their local views of blockchain, the blockchain becomes inconsistent. Such problems can be resolved by:

- (i) sharing the verification process of the transaction to guarantee rightness of the transaction;
- (ii) letting everyone know the successfully processed transaction to assure the consistency of blockchain.

Bitcoin uses PoW and a distributed consensus protocol to satisfy the above specifications.

As mentioned, the distribution of the verification process is to ensure the correctness of data by a majority of valid users. Therefore, if the blockchain goes into an unstable state at any time, all users can update their local blockchain copy to the one accepted by most miners. But this election process is subject to Sybil attacks [4]. In Sybil attacks, a malicious user creates many virtual nodes and makes them vote for a wrong transaction, thereby disturbing the election process.

PoW model helps Bitcoin to overcome the Sybil attacks. In this model, a miner has to solve a cryptographic mathematical puzzle to prove their genuineness similar to Hashcash. PoW includes a value named “nonce” which generates a hash value when hashed with SHA-256 which starts with the required number of zero bits. The target sets the needed number of zero bits. The hash value needed must be below the current target value and should have a certain number of leading zero bits to be less than the target. To do this, a high level of computational cost is applied to verification by PoW, and to do PoW, the miner needs a high level of computing resources. It is, therefore, very difficult to fake the computing resources. Thus, the problem of Sybil attacks is resolved.

In general, the transactions are not mined individually. The miners collect the pending transactions to make a block and then mine the block by measuring the block’s hash value as well as varying nonce. The nonce must be varied until the final value is less than or equal to the given target value. The miners share the 256-bit target value. It is not simple to calculate the hash value. SHA-256 is the hash function used in Bitcoin [8]. If the cryptographic hash function does not find the necessary hash value, the only alternative is to try different nonce until a solution is found (a hash value below the target). Consequently, the complexity of the puzzle depends on the target value, i.e., the lower the target value, the lesser the number of solutions, thereby making it more difficult to calculate the hash. Once the correct hash value is determined for a block, the miner immediately broadcasts the block to the network along with the measured hash value and nonce, and then the block is appended to his private blockchain. On receiving a mined block, the other miners compare the hash value with the target value in the received block and verify its correctness. They will also upgrade their blockchain locally by adding the new block. After the block is successfully added to the blockchain, the first miner who solved the puzzle will get a reward. There is no central authority to provide the rewards. In the block generation system, whenever a miner adds a Coinbase transaction or a reward-generating transaction for his Bitcoin address, the rewards are provided.

Other than these rewards, the miner also receives a transaction fee for every successful addition of transaction in block. The transaction fee usually will be the difference of value of all inputs and values of all outputs in a transaction. Studies show that higher transaction fees make transactions with lower transaction fees suffer from the starvation problem, i.e., service is denied for a longer duration. Bitcoin never necessitates a transaction fee. It is the owner of the transaction who sets the fee, which is not a constant value. Nonetheless, as users struggle to get transactions publicized on the blockchain, transaction fees increase to rates that discourage the use of Bitcoin, illustrating a major structural issue facing the blockchain.

## 1.7 Bitcoin Development Environment

Bitcoin is an open-source project, and MIT holds the license for its source code. Bitcoin Core can be downloaded for free. A community of volunteers had created the Bitcoin project. Initially, only Satoshi Nakamoto was there in the project. Later, by 2016, it had around 400 contributors with a handful of developers and several part-time developers. Bitcoin Core can be regarded as the reference implementation of the Bitcoin system by Bitcoin since it is the authoritative reference on how to implement each part of the technology. It is labeled as the Satoshi client. Bitcoin Core acts as a Bitcoin node, and a collection of Bitcoin nodes form a Bitcoin network. Nakamoto initially released the “Bitcoin” software, but to make it different from the network, he later renamed it to “Bitcoin Core”. Bitcoin Core has all features of Bitcoin such as wallet, block validation engine, transaction, and full network node in a P2P Bitcoin network.

### 1.7.1 Bitcoin Core Implementation

Bitcoin Core can be downloaded from http://Bitcoin.org/en/choose-your-wallet and installed by clicking Bitcoin Core button. Once the installation is complete, a new application named “Bitcoin–QT” will be listed in applications. The Bitcoin client can be started by double clicking the icon. As the Bitcoin client starts running, it will download the blockchain, and it will take several days to complete. When “Synchronized” message is displayed, it is understood that the downloading process is successful.

The Bitcoin developers can download the full source code either as a ZIP file or clone it from the authoritative database https://github.com/Bitcoin/Bitcoin. On the other hand, in your system, a local copy of the source code can be created using the git command line.
