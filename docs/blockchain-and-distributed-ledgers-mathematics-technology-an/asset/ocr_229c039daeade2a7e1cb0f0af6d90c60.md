# Blockchain and Distributed Ledgers: Mathematics, Technology, Economics

traditional, regulated financial institutions. They are nonetheless facilitated by the pseudo-anonymity inherent in cryptocurrencies, the peer-to-peerness of transactions, and the relative-immaturity of regulations, proper risk frameworks and controls in this industry.

# 9.7 Key isolation and transaction approval

# 9.7.1 Security integrands

Overall, the security of a wallet heavily depends on two factors:

+   (1) the protection of its keys;
(2) the protection of its transaction signature process.

Even when the keys are well protected, the process under which the system may be authorized to use the secret key to sign a transaction can become the weak point of a system. An HSM, for instance, provides strong guarantees over the confidentiality of keys; however, HSMs often expose an interface to which external service connects to ask for a signature. Even assuming that the key is well protected in the HSM, the interface becomes an attack vector: the attacker may attempt to access this interface and ask the HSM to sign an arbitrary transaction. Therefore, such an interface must be well guarded, and must enforce good controls and process to alleviate the risk of a single point of failure.

# 9.7.2 Hot and cold storage

We define two broad classes of wallets often called hot wallets and cold wallets.

+   (1) Hot wallet: A hot wallet is a wallet whose secret keys are manipulated on a device that is, or may be, connected to a network (generally the Internet). Hot wallets are typically implemented for applications where access to the funds must be fast, and inexpensive. Because the keys are exposed to attackers, the attack surface is large and such wallets are generally used when high availability or automation is required.

+   (2) Cold wallet: A wallet is a wallet whose secret keys are under no circumstance stored or managed on a device that may be connected to a network. The keys are physically isolated, they are immune against remote attacks and may be attacked with physical access to the infrastructure. Cold wallets are typically implemented for applications where security is critical (e.g., when assets under management have significant value) and where the access time and cost to the funds is a serious concern.

Naturally, specific implementations of hot wallets may embed robust protocols mitigating the large attack surface. Equivalently, inconsiderate implementations of cold wallets may reveal critical weaknesses trumping their apparent resilience. A solid wallet implementation should model specific thread scenarios to maximize security under specific availability requirements of the wallet use case.