# The API-service architecture in Hyperledger

![](bbox=[0.125, 0.18, 0.875, 0.42])

Figure 14.1 V2.0.0 architecture of Hyperledger (from Hyperledger white paper)

different possible choices of the consensus algorithm, like the SOLO and Kafka (https://github.com/hyperledger/fabric/tree/master/orderer/consensus/solo and https://github.com/hyperledger/fabric/tree/master/orderer/consensus/kafka) algorithms, or the Simplified Byzantine Fault Tolerance, in order to bet-
ter take into account the relationships among network participants.

The Hyperledger Fabric White Paper specifies the main features of Fabric
(see Figure 14.1 for the architecture). These are:

+   - **Scalability:** The possibility of adding dynamically new nodes into the
+   network. The execution of chaincode is kept separate, and it is possible to
+   add nodes for distributing the traffic flow.
+   - **Transactions:** Are deterministic, executed in a defined and constant time
+   independent from the executing entity.
+   - **Identity:** Hyperledger Fabric provides a PKI (public key infrastructure)
+   used for the controlling resources accesses. The PKI module can be inte-
+   grated with preexisting solutions such as LDAP or AOUTH2.
+   - **Audit:** The possibility of performing auditing is included in Fabric, with
+   managing events and a log allowing for a variety of checks based on the
+   current network configuration.
+   - **Advanced queries:** Fabric allows users to query the current blockchain
+   status, with queries defined and loaded into the blockchain during deploy
+   of the business network. They can be invoked using APIs by users. Data