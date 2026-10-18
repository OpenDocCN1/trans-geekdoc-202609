+   - Proof of Stake (PoS): This algorithm requires a miner to acquire a sufficient stake to mine a block. While executing an attack is expensive, the incentive for the attack is also reduced as the attacker needs to own a high stake. There-fore, an attack will have more effect on the attacker. This process provides in-creased security and is power efficient but fails to keep the system completely decentral-ized.
+   - Proof of Burn (PoB): This algorithm requires the miner to burn some wealth to mine a new block. The miners should show proof that they have burned some wealth by sending coins to a verifiably un-spendable address. This process is expensive like PoW but no external resources are used except the miner’s wealth. PoB consumes virtual or digital resources and is power efficient too. PoB works by burning PoW mined cryptocurrencies.

# 5.2 Structure of blockchain

All blockchain structures are generally categorized into three categories:

+   - Public blockchain architecture: In this architecture, any participant can enter and exit the blockchain network as per their will, without any permissions. All the willing participants have access to the data in the network as long as they are in the network. Ex: Bitcoin, Ethereum, etc.
+   - Private blockchain architecture: In this architecture, each participant re-quires permission to enter and exit the blockchain network. The participants who enter the blockchain can be restricted to certain data as well. This system is controlled by the users of a specific organization. Ex: Hyperledger Fabric.
+   - Consortium blockchain structure: In this architecture, the blockchain net-work is built by a set of organizations. This architecture is neither completely public nor completely private. All the permissions are controlled by the preliminary as-signed users. Ex: Quorum, Corda, etc.

The tab.1 gives an outline of the comparison of the three blockchain structures:

Tab. 1: Blockchain structure comparison

| Property | Public Blockchain | Private Blockchain | Consortium Blockchain |
|---|---|---|---|
| Accessibility | Anyone | Single organization | Multiple organizations |
| Who can join? | Anyone | Permissioned and known identities | Permissioned and known identities |
| Consensus mechanism | Pow/Pos | Voting or multi-party consensus algorithm | Voting or multi-party consensus algorithm |