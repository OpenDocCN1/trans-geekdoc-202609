+   • Public-private key encryption: this is an encryption that requires a public key and private key, which together form a pair and are each other's counterpart. What is unique about this is that the decryption is only possible with the use of both keys.
+   • Cryptographic hash functions: converting a (large) piece of text into a fixed-length text. This is applied as a guarantee of the integrity of the data.
+   • Hashcashing: the reverse process of cryptographic hashing. This is a labour-intensive process, also called the proof of work, where there is a lot of calculation work for a computer.

# Examples of Infrastructures

Various Blockchain systems are being developed in the world, and they work in different ways - publicly or privately. Differences in the infrastructures are also determined, among other things, by the way in which consensus has been reached to arrive at that infrastructure. There are currently three different structures that are widely used: Hyperledger Fabric, Ethereum and Corda. We explain them briefly.

# Hyperledger Fabric

Hyperledger Fabric has a refined consensus model that is not only dependent on proof-based mining. After all, a check has already been done for the transaction data and the authorizations therein. Nodes – which validate the reliability and integrity of transactions – have a different role and tasks within Hyperledger Fabric to reach consensus than for Ethereum.

Hyperledger Fabric is very suitable for streamlining the supply chain. This infrastructure focuses on the chain management of a sector. Information is only shared with stakeholders who are not visible to all (involved) parties in the entire chain, so it is a private system (see Chapter 1.4). An example of this are material certificates, the processing of the material and the final assembly of these steel elements. This application is described in Jansen's research (2018).

Medicalchain is one of the first healthcare organizations to use Blockchain within the Hyperledger community. Medicalchain is focused on ensuring that clients have access to their medical records.

# Ethereum

Within Ethereum, all users must reach consensus on all transactions within the network, the order of transactions being essential for consistency within this network. As a result, duplications and fraud can be prevented. Consensus is reached on the basis of mining, a proof of work mechanism, whereby common agreement is reached in the ledger and all users give permission for all transaction data in this Blockchain. With