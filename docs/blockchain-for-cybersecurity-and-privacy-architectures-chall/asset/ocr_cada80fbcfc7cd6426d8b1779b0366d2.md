Continuous technological advancements can render the current cryptographic tools obsolete and ineffective. Integration of distributed ledgers into the existing infrastructure can also lead to security breaches and threats.

Should be operationally scalable, depending upon requirements.

Legal framework need not provide settlement finality always.

Distributed ledgers pose legal risk if a settlement's arrangement is ambiguous.

Time-jacking attacks, when the attacker posts inaccurate timestamp on a block.

Online wallets are prone to denial-of-service (DDoS) attacks.

>50% attack, when a miner or group of users acquire more than 50% of computing power and self-reverse transactions.

Double spending, when the attacker makes more than one transaction, using a single coin.

Selfish mining, where a group of users can obtain revenue more than their mining power.

# 12.2.2.1.2 Security Threats

As with other payment methods, blockchain payment systems also have security threats and concerns. The security issues are briefed as follows (Vyas & Lunagaria 2014; Lin & Liao 2017):

+   - Attacks on wallet software: Wallets are used by cryptocurrency customers to manage the currencies owned by them. Online wallets are more vulnerable to security attacks than offline wallets. Hence, they need to be encrypted and backed up off-line. The DDoS attacks are potential threats for online wallets.

+   - Time-jacking attacks: The time counter of a node in the network is altered by the attacker, and this deceived node may accept an alternate blockchain. The consequences are double spending and waste of computational resources.

+   - >50% attack: This is one of the major threats to a blockchain when a user or group of users gets hold of more than 50% of computing power. They do this by holding of the 'nonce' value in a block. They can then execute, modify, and self-reverse transactions and prevent the mining of valid blocks.

+   - Double spending: Double-spending is where the attacker makes more than one transaction with the same coin, resulting in invalidation of the 'honest' transaction and validating the 'fraud' transaction. An attacker makes a transaction with a coin and, simultaneously, another transaction with the same coin is done to another address. By varying the timestamp, the second transaction can be made as a real one. Blockchain peers will not accept two transactions with the same input. They will validate only the first one reaching them, and hence, the fraud transaction will be validated and the original one not be confirmed.

+   - Selfish mining: It allows a pool of sufficient size to obtain revenue larger than its mining power. The attacking miners force honest miners to perform wasted computations. The selfish miner will keep their blocks private, will secretly bifurcate the blockchain, and will earn more revenue.