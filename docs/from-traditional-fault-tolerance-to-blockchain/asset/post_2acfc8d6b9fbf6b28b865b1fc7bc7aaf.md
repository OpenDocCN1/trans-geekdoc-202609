
## EXAMPLE 6.1

In this example, we study the role of the promise-not-to-accept-older-proposal requirement on the safety property for consensus. If the system has already chosen a value before a competing proposer proposes, the safety property for consensus would hold even without the promise-not-to-accept-older-proposal requirement, as shown in Figure 6.3. For the system to choose a value, the majority of acceptors must accept a proposal (proposal P(n, v) in Figure 6.3). When another proposer (proposer 2) wants to send a proposal (proposal P(n + 1) in Figure 6.3), it must collect information from the majority of acceptors regarding if they have accepted any proposal. Therefore, in this case, at least one acceptor that has accepted the proposal P(n, v) would pass on the fact that it has accepted proposal P(n, v). Therefore, proposer 2 must use v as the value for the new proposal P(n + 1). However, the promise-not-to-accept-older-proposal requirement is essential to ensure only a single value is chosen if the system has two or more competing proposers to start with.

![](img/7320b1480d74f1d65f74659cab456782_241_0.png)

Figure 6.3 If the system has already chosen a value, the safety property for consensus would hold even without the promise-not-to-accept-older-proposal requirement.

As shown in Figure 6.4, before proposer 1 completes the accept phase for proposal P(n), proposer 2 may have completed the prepare phase. Despite the fact that acceptor 1 has accepted P(n, v) before it receives the prepare request P(n + 1), its response might not reach proposer 2 soon enough before proposer 2 concludes that no value has been chosen in the past and proposes a new value v' in its proposal P(n + 1). Without the promise-not-to-accept-older-proposal requirement, acceptor 2 and acceptor 3 would still accept P(n, v) after they have responded to proposer 2's accept request for P(n + 1). This would lead the system to choose v. Subsequently, the acceptors would accept the accept request for P(n + 1) because it is a newer proposal. Unfortunately, at this point, the system has chosen two different values, violating the safety property for consensus.

![](img/7320b1480d74f1d65f74659cab456782_242_0.png)

Figure 6.4 If two competing proposers propose concurrently, the system might end up choosing two different values without the promise-not-to-accept-older-proposal requirement.

With the promise-not-to-accept-older-proposal requirement in place, acceptor 2 and acceptor 3 would have rejected the accept requests for P(n) that arrive later than the prepare request for P(n + 1), which would prevent value v being chosen by the system. If the accept phase for P(n + 1, v') can be completed before a newer proposal is issued, the system would choose v'.

![](img/7320b1480d74f1d65f74659cab456782_242_1.png)

Figure 6.5 With the promise-not-to-accept-older-proposal requirement in place, even if two competing proposers propose concurrently, only a single value may be chosen by the system.

## 6.3 Multi-Paxos

An immediate application of the Paxos algorithm is to enable state machine replication where a set of server replicas provide services for the clients by executing the requests sent by the clients and returning the corresponding replies to the clients. In this context, a client partially assumes the role of a proposer, and all the server replicas are acceptors. At the highest level, the value to be agreed on by the server replicas (i.e., acceptors) is the total ordering of the requests sent by the clients. The total ordering determination is accomplished by running a sequence of instances of the Paxos algorithm. Each instance is assigned a sequence number, representing the total ordering of the request that is chosen. For each instance, the value to be chosen is the particular request that should be assigned to this instance.

The reason why a client only partially assumes the role of a proposer is because it is only capable of proposing a value (which is the request it sends), but without the corresponding proposal number. One of the server replicas must assume essentially the other half of the proposer role. This special replica is referred to as the coordinator [14], the leader [10], or simply the primary [16, 17]. We could argue that the primary is essentially the proposer as it is described in the Paxos algorithm [10] and it is the primary that selects the value, which is supplied by the clients. Furthermore, the primary propagates the chosen value to the remaining replicas (often referred to as backups) so that they can learn the value as well. Obviously, the primary is the first to know that a value is chosen for each instance of the Paxos algorithm, and usually the first to send the reply to the client. The backups can suppress their replies unless they have suspected the primary because the client needs only a single reply for each of its requests.

Normally, one of the server replicas is designated as the primary at the beginning of the system deployment. Only when the primary becomes faulty, which is rare, or being suspected of being faulty by other replicas, another replica will be elected as the new primary. As long as there is a sole primary in the system, it is guaranteed that no replica would report having accepted any proposal to the primary, which would enable the primary to select any value (i.e., any request). Therefore, the first phase (i.e., the prepare phase) can be omitted during normal operation (i.e., when there is only a single primary in the system). The full Paxos algorithm is needed to elect a new primary and it is needed to run only once right after a new primary is elected. In essence, this run would execute the first phase of all instances of the Paxos as long as the current primary is operating.

The above scheme of applying the Paxos algorithm for state machine replication is first proposed in [10] and the term “Multi-Paxos” was first introduced in [5]. The Multi-Paxos during normal operation is illustrated in Figure 6.6. Note that the primary can execute the request as soon as it receives the P2b messages from a quorum of replicas. As shown in Figure 6.6, the primary does so prior to the receiving of the P2b message from replica 2.

![](img/7320b1480d74f1d65f74659cab456782_244_0.png)

Figure 6.6 Normal operation of Multi-Paxos in a client-server system with 3 server replicas and a single client.

### 6.3.1 Checkpointing and Garbage Collection

The Paxos algorithm is open-ended in that it never terminates – a proposer is allowed to initiate a new proposal even if every acceptor has accepted a proposal. As such, an acceptor must remember the latest proposal that it has accepted and the latest proposal number it has acknowledged. Because the Multi-Paxos is derived from Paxos, all server replicas must remember such information for every instance of the Paxos algorithm that it has participated in, even after it has long executed the request chosen by this instance. This would require infinite amount of memory space, which is obviously not desirable for practical systems.

The problem can be eliminated by performing periodic checkpointing at each replica [16, 17]. A replica takes a checkpoint after the n-th request has been executed, where n is the checkpointing period in terms of the number of requests executed. When f + 1 or more replicas have taken a checkpoint at the same logic point, the checkpoint becomes stable. When a checkpoint has become stable, a replica can subsequently garbage collect all logged information and messages pertinent to the last n messages (including the clients' requests).

A slow replica might lag behind and need either to find out which request is chosen for an instance, or need a copy of the request itself. Such information might no longer be available for a Paxos instance older than the most recent stable checkpoint, in which case, the replica should contact the primary for a state transfer. Upon a state transfer request, the primary would send a copy of its latest checkpoint to the slow replica. The slow replica then roll-forwards its state by restoring its state using the checkpoint received.

### 6.3.2 Leader Election and View Change

Earlier in this section, we mentioned that upon the primary failure, a new leader would be elected (using the Paxos algorithm itself), and the new primary would need to execute a full two-phase Paxos algorithm to establish whether or not a request has been or might be chosen for each incomplete instance of the Paxos algorithm. In fact, the two steps can be combined to eliminate the extra message delays, as first shown in a Byzantine fault tolerance algorithm [4] and later was adapted for the non-Byzantine environment [16, 17], as shown in Figure 6.7. Such an algorithm is referred to as a view change algorithm [4].

![](img/7320b1480d74f1d65f74659cab456782_245_0.png)

Figure 6.7 View change algorithm for Multi-Paxos.

The view change algorithm assumes that each replica is assigned a unique integer identifier, starting from 0. Given a set of 2f + 1
