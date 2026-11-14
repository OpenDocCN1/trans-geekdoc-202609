# TABLE 9.1 Comparison of permissionless and permissioned blockchain

| | Permissionless Blockchain | Permissioned Blockchain |
|---|---|---|
| Environment Type | Open | Closed |
| Participation in Consensus | All nodes | Selected nodes |
| Identity | Pseudo-Anonymous | Registered Participants |
| Consensus Type | Lottery based | Voting based |
| Transaction Processing Speed | Slow | Fast |
| Consensus Algorithms | Proof of Work, Proof of Stake, Proof of Burn, Proof of Delegated Stake, etc. | Paxos, Practical Byzantine Fault tolerance, Raft, etc. |

different nodes. Once recorded in a block the transaction can never be changed. So blockchain provides an immutable digital ledger among all the nodes present in the network. It builds trust [7] among all users as all the users have the same set of digital record present among themselves and whatever happens in the network one can see it. Blockchain technology has security, and privacy issues of the users are addressed using public and private key concepts also using a digital signature. Blockchain can mainly be used in two different ways; permissionless and permissioned. Table 9.1 provides a brief comparison of both the technologies. Permissionless design which is generally established on an open environment allows anyone to join the system as well as allowing writing to shared blocks. Permissionless design also gives equal privilege to all the nodes in case of consensus process. A permissioned blockchain design is managed by a known set of entities and is established in a closed environment. Though all the entities are allowed to perform transactions, only a fixed set of predetermined nodes can take part in the consensus process in a permissioned blockchain. Consensus algorithms [4] play an important part in managing an efficient and secure blockchain system.

# 9.9 DISTRIBUTED CONSENSUS ALGORITHMS

The concept of consensus is an engrossing topic in a decentralized or distributed network. Consensus means a procedure to arrive at a common agreement in a decentralized or distributed multi-agent platform. In a conventional distributed system, we apply consensus to ensure reliability which ensures correct execution in the presence of faulty individuals and fault tolerance. In addition to this, a distributed consensus mechanism should satisfy certain properties such as termination, validation, integrity and agreement. An example of consensus is state machine replication, which is a key aspect of any distributed consensus protocol. For example, if we want to run some kind of distributed protocol over a network, every individual entity runs the current protocol and they store the state of the protocol in different state machines. So the entire execution part of the protocol can be represented as a state machine. Now this state machine needs to be replicated to multiple entities so