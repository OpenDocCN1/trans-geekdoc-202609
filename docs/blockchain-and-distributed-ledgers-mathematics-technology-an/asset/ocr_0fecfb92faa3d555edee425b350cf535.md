# Chapter 11 Current Research Topics | 365

# Transparent Layer, t-Addresses

![](bbox=[0.153, 0.091, 0.846, 0.375])

**Figure 11.8** Zcash has a shield-in privacy layer, called the ZK security layer, allowing participants to transact anonymously. Own graphics.

the inputs is equal to the sum of the outputs. This framework guarantees that transactions stay anonymous. Upon receiving the encrypted transaction, the receiver decrypts its content with her secret key and generates a unique one-time serial number for the newly acquired coins, which is used for preventing double-spending attacks. This number becomes public once the coin is spent. This technique is very similar to the one proposed by Chaum, see Section 4.5.7.

# ## 11.4 Scalability trilemma

# ### 11.4.1 Background

The Ethereum Wiki defines the scalability trilemma as follows: “This sounds like there’s some kind of scalability trilemma at play. This is trilemma and we can break through it? The trilemma claims that blockchain systems can only have at most two of the following three properties: decentralization (defined as the system being able to run in a scenario where each participant has only access to O(c) resources, i.e., a regular laptop or small VPS), scalability (defined as being able to process O(n) > O(c) transactions), security (defined as being secure against attackers with up to O(n) resources).”² The trilemma is presented graphically in Figure 11.9,³

First, we analyze the definitions to lay terms. Being decentralized is the raison d’être for the entire crypto concept. Correctly implemented, decentralized protocol

> ²https://github.com/ethereum/wiki/wiki/Sharding-FAQ.

> ³The decentralized + severe dilemma claims that the foundational protocols, such as Bitcoin and Ethereum, can achieve decentralization and security. However, this claim is difficult to accept at face value. Indeed, as was