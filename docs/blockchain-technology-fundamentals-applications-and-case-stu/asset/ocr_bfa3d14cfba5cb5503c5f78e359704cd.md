# Major Protocols of Blockchain

![](bbox=[0.118, 0.096, 0.881, 0.206])

FIGURE 8.7 Bitcoin transaction [9,10].

**Double-spending problem:** This occurs when the same cryptocurrency is used more than once. It can also be defined as in any bitcoin transaction where the same input is used for multiple transactions that was used previously and got broadcast on the decentralized network [10].

**Unspent transaction output (UTXO):** It is defined as an output of the transaction that is not used or spent in the next transaction. This UTXO is used mostly in all the cryptocurrencies [9,10].

**Spent transaction output (STXO):** It is define as an output of the transaction that is used or spent in the next transaction [9,10].

In any bitcoin transaction, it can have maximum of two outputs and multiple inputs

**Output:** The item is sent to the other participant or the balance that is returned to the sender.

**Input:** The multi-inputs can be utilized to join smaller amounts of coins transferred.

**Sybil attack:** This is a type of attack common in a peer-to-peer network to strengthen the power in the reputation system. The purpose of this attack is to achieve the power in the network to do illegal transactions in the network. A single participant builds numerous identities/accounts to the banned network, but for the other participants, the deylked accounts/identities seem to be unique accounts/identities.

All transactions and ownerships are described clearly in the distributed ledger used in the bitcoin network. All participants of the decentralized peer-to-peer network have a copy of the bitcoin ledger [12]. When any participant wishes to do a transaction to send coin to another participant, the transaction should be informed publicly, and the decentralized peer-to-peer network will take care of the transaction with proper verification and correctness. In the network, the participant can try to change the transaction with two different participants, which is already discussed earlier and called double spending problem. The same participant can run multiple instances of the transaction to verify the initial transaction, which leads to Sybil attack. The problems discussed are solved using proof of work in the bitcoin network.

The hash is generated and announced publicly by the time stamp server confirms the existence of the data inside the block during the time of hashing. The time stamp server also verifies the time stamp of the current and the previous blocks;