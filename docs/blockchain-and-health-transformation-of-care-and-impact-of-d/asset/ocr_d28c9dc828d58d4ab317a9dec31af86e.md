public keys, and every transaction also has a fee for the miners. Blocks (data or text) form a chain because each piece of data refers to the previous piece of data. This creates a chain (Veuger 2020b) as in Figure 12.

![](bbox=[0.16, 0.165, 0.8, 0.3])

Figure 12. Transaction in Bitcoin.

Everyone can participate in this system and add new transactions (blocks) to the chain. These blocks are stored decentrally, and no one monitors the reliability of the transaction, where the immediate challenge is to design the system in such a way that only valid transactions are added without the person behind the transaction being known and without a central control.

The challenge is therefore to keep Blockchain's ledger up to date, with consensus on its content. This is known as the Byzantine Generals Problem': the problem of a number of generals who jointly coordinated an attack on an enemy.² The problem consists of:

+   - **Completeness**: a message from one general to the others may not arrive because, for example, the messenger is attacked. In terms of Blockchain: a valid transaction does not reach the others and is not included in the ledger.
+   - **Authentication**: an untrustworthy general can represent himself as another general. In terms of Blockchain: C wants to give money from A to B.
+   - **Integrity**: the message from the reliable general can be falsified, for example by the messenger. In terms of Blockchain: A makes a valid transaction but the content thereof is changed.
+   - **Consistency**: an untrustworthy general can send different and conflicting messages to different generals. In terms of Blockchain: A may have 10 euros but gives it to both B and C, also known as double spending.

Blockchain essentially solves the Byzantine Generals Problem because all participants agree on the content of this ledger, a technique that has been around for centuries. Namely by using different cryptographic techniques: