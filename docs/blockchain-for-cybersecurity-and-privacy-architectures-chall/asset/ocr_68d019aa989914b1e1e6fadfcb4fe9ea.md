# A Taxonomy of Blockchain Threats and Vulnerabilities

# 1.4.2 CONSENSUS MECHANISMS VULNERABILITIES

# 1.4.2.1 51% Vulnerability

Establishing mutual trust in BT is based on the shared consensus mechanism. However, the attackers might control the whole blockchain network by exploiting the 51% vulnerability, which is built in the mechanism. For example, if a single user or a group of users have more than 50% of the total hashing power in the blockchain networks, which are based on the PoW mechanism, then the user or the group of users can exploit the 51% vulnerability. Therefore, gathering the mining power under a few mining pools might lead to this. Recently, Clash.io dominated 54% of all BTC network powering for a day [19]. In addition, the blockchain networks, which are based on the PoS mechanism, also have the 51% vulnerability. The vulnerability can be exploited when a single miner has more than 50% of the coins in the network; a 51% vulnerability leads to a 51% attack, which allows the attacker to do the following [31]:

+   - Injecting deceptive transactions
- Manipulating the blockchain network
- Outstripping all other users in the blockchain network
- Performing a double-spending fund
- Stealing other users' assets

# 1.4.2.2 Alternative History Attack

In this attack, the attacker sends a payment transaction to the target while he or she mines another blockchain fork, which includes a deceptive double-spending action. After the confirmation, a product or service will be received by the attacker from the target. If the attacker succeeds in finding more blocks than the genuine chain, or he propagates his her malicious fork and recovers the coins; otherwise, or she must extend his or her malicious fork to reach the fork of the honest miners. If the attacker cannot catch up with other nodes, the attack will fail [32].

# 1.4.2.3 Finney Attack

In this attack, one transaction is pre-mined in a block, and a duplicated version of this transaction is sent to a user by the attacker. After the transaction is accepted and the receiver delivers the product, the attacker propagates the block, which contains the initial transaction. Thus, the transaction, which is sent to the user, will be invalid, and the attacker will succeed in producing a double-spend transaction [33].

# 1.4.2.4 Race Attack

This attack is easy to launch in blockchain networks, which are based on the PoW mechanism; this is mainly because an attacker can exploit the time between the creation transaction and the confirmation transaction to carry out the attack. Before mining the confirmation transaction, the attacker has obtained the creation transaction results, which leads to double spending [34].