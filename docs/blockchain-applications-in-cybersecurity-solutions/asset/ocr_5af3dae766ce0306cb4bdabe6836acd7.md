without completely confirming the authenticity of blocks. The three detecting methods are as follows:

+   - **Listening period:** In this method, each received transaction is associated with a listening period, during which the Vendor monitors all receiving transactions. Only if the Vendor observes no attempt at double-spending throughout the listening period, will he deliver the product or provide the service.
+   - **Inserting observer nodes:** In this case, the Vendor inserts observer nodes into the network. The main task of the observer node is to transmit all transactions received to Vendor. This enables the Vendor or its observers to notice a double-spending attempt within seconds. To detect this attack, the Vendor must deploy a large number of observer nodes capable of connecting numerous nodes. The Vendor will incur costs as a result of implementing this countermeasure.
+   - **Sending out Warning or Alert Messages:** To counteract double-spending on rapid Bitcoin transfers, an efficient defense strategy has been developed. Peers on the Bitcoin network send out alarm messages when they receive two additional transactions with similar inputs but distinct outputs.

# Countermeasures against Vector76

Vector76 attack is an attack in which attackers aim to fraudulently withdraw or steal the coins from the target using an invalid transaction. Using the mechanism that does not accept transactions with a single confirmation, the user node in the network should avoid having inbound connections, which prevents the attacker from injecting false information into the network; outgoing node connections should be monitored as well, and only well-known nodes should be permitted to join, and notifying the merchant about the ongoing double-spend could be preventive actions.

# Countermeasures against Alternative History Attacks

In the case of repeated confirmations, an alternate-history attack is still conceivable, but it necessitates a high hash rate and the danger of largely lost electricity to the attacking miner. Incoming connections are not permitted; implementation of explicit outbound connections to well-known nodes, placing observer nodes in the network, and notifying the merchant about the ongoing double-spend are all feasible safeguards [11].

# Countermeasures for 51% Or Majority Attacks

Several countermeasures are recommended to mitigate 51 percent of attacks or the Majority of attacks. Miller et al. [18] recommended adjustments to Bitcoin's PoW puzzle in order to minimise coalitions of mining pools for majority attacks. In