consensus algorithm. This PoW is executed by miners who not only ensure the fidelity of past transactions on the blockchain’s ledger but also detect and avoid double spending.

# 8.3.14 51% ATTACK

In a blockchain network, a 51% attack is a probable attack that can happen when an organization governs the mining power or so-called hash rate with a majority ratio. A bitcoin network is made secure by making all miners give consent on a shared ledger, i.e. blockchain. Every node in bitcoin ensures that these are working on a valid transaction at any point of time by looking at each other. Miners would have the potential to determine which transaction to give consent to given that the majority of miners are handled by a single entity. Hence this will give power to the miner to block other transactions and allow their own coins to be spent multiple times. This is also known as double spending as shown in Figure 8.7 [16, 17] (ref: https:// learncryptography.com/ cryptocurrency/ 51- attack).

With this attack an attacker can perform the activities mentioned below:

+   - They can reverse his transactions that have already happened.
+   - They can block transactions from gaining any confirmations.
+   - They can block other miners to mine any other valid blocks.

However, an attacker cannot perform the activities below:

+   - They cannot reverse the transactions of others.
+   - Block transactions to be sent at all.
+   - Modify the number of coins generated per block.
+   - Generate coins out of nowhere.
+   - Send coins that were never owned by them.
+   - These attacks are valid till the attacker is in control (i.e., owns 51%). The transactions which had been turned down can be added just after the attacker loses their majority [18].

![](bbox=[0.11, 0.7, 0.88, 0.88])

# FIGURE 8.7 51% Attack Simplified.