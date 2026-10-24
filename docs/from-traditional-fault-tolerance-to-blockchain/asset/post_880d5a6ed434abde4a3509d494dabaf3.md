
- Liveness property. Eventually, one of the values proposed is chosen. Furthermore, if a value has been chosen, then a process in the system can eventually learn that value.

The safety requirement S1 ensures that the same value is chosen by all processes. The requirements S2 and S3 are to rule out trivial solution such as all processes choose a pre-defined value.

More specifically, the processes in the system may assume different roles. Some processes may propose values to be chosen and learned by others. Such a process is referred to as a proposer. Some processes may participate in the agreement negotiation (i.e., it is not necessary for every process in the system to participate). Such a process is referred to as an acceptor. Yet some processes might simply want to learn the value that has been chosen. Such a process is called a learner. Note that the roles are logical and a process can assume multiple roles (such as being a proposer and an acceptor).

We assume that the consensus algorithm will operate in an asynchronous environment with no malicious faults. This means that it may take a process arbitrary long time to complete a local task, and a message may take arbitrarily long time to be delivered at the intended destination process, possibly after many retransmissions.

A process may crash and stop operating. In the original Paxos algorithm, process restart is explicitly allowed [10]. However, allowing process restart would require each process to flush its state to stable storage pessimistically after every state change before sending out a message that reflects the latest state change. We prefer to drop this assumption for the following reasons:

- Flushing to stable storage after every state change could significantly increase the runtime overhead of the algorithm because the bandwidth of stable storage is much smaller than that of volatile memory.
- Not requiring stable storage may enable the use of the Paxos algorithm in diskless embedded devices.

Removing this assumption will not change the Paxos algorithm operation in any way. The only downside may be a temporary lower number of processes operating in the system. Because to reach a consensus using the Paxos algorithm, the majority of the processes must be operating, this may temporarily reduce the resiliency of the system. If half or more processes fails concurrently, the system as a whole would fail. As long as this corner case does not happen, restarted processes could always rejoin the system as a new member. The membership change can be treated as a distributed consensus problem, i.e., the value chosen will be the membership formation of the system when a process rejoins [17].

The original Paxos algorithm also assumes that messages are not corrupted [10]. We should clarify that messages can very well be corrupted by the network as long as the corruption can be detected. Once the corruption of a message is detected, the message is discarded by the receiving process, making this equivalent to a message loss, which can be resolved by a simple retransmission.

## 6.2 The Paxos Algorithm

In this section, we first describe the Paxos algorithm. Then we provide a sketch of proof of correctness. We also explain how the idea in the Paxos algorithm is developed as documented in [10] in details.

![](img/7320b1480d74f1d65f74659cab456782_233_0.png)

### 6.2.1 Algorithm for Choosing a Value

The algorithm for choosing a value operates in two phases, the prepare phase and the accept phase, respectively, as shown in Figure 6.1. The prepare phase is initiated by a proposer sending a prepare request P1a(n) to the acceptors in the system, where n is the proposal number selected by the proposer. At this stage, no value is included in the prepare request. This may appear to be counter-intuitive, but it is critical to limit the freedom of the proposer on what value it may propose. This is because some acceptors might have accepted a value proposed by a competing proposer. Allowing a proposer to propose an arbitrary value at all times may lead to multiple values to be accepted.

In the prepare phase, when an acceptor receives a prepare request P1a(n), it does the following:

- If the acceptor has not responded to any prepare request, it records the proposal number n, and sends its acknowledgment P1b(n) to the proposer.
- If the acceptor has already responded to another prepare request with a proposal number m, and m < n, there are two scenarios:
  - The acceptor has not received any accept request, which is sent by a proposer during the accept phase, it records the higher proposal number n and sends its acknowledgement P1b(n) to the proposer.
  - The acceptor has already received an accept request with a proposal number k, it must have received a value proposed by some proposer in the past. This full proposal [k, v] is included in the acknowledgment P1b(n, [k, v]) to the proposer. Obviously, k must be smaller than n.

The second phase (i.e., the accept phase) starts when the proposer could manage to collect responses from the majority of acceptors. The proposer determines the value to be included in the accept request in the following way:

- If the proposer received one or more P1b messages with full proposals. It selects the value v in the proposal that has the highest proposal number.
- If none of the P1b messages received by the proposer contains a full proposal, the proposer has freedom to propose any value.

Then the proposer multicasts an accept request P2a(n, v) to the acceptors. Note that the accept request contains a full proposal with a value v.

When an acceptor receives an accept request P2a(n, v), it accepts the proposal [n, v] only if it has responded to the corresponding prepare request P(n) for the same proposal number n. The acceptor sends an acknowledgement message P2b(n) if it accepts the proposal.

Note that accepting an accept request by an acceptor does not mean that the value contained in the proposal included in the accept request has been chosen. Only after the majority of acceptors have accepted the same accept request is the value considered chosen. It is possible that no value is chosen or another value is eventually chosen after a minority of acceptors have accepted an accept request.

### 6.2.2 Algorithm for Learning a Value

There are many alternative methods for a learner to find out the value that has been chosen. The most straightforward method is for an acceptor to multicast a message containing the value that has been chosen, L(n, v), to all learners whenever it has accepted a proposal (i.e., it has accepted an accept request), as shown in Figure 6.1. When a learner has collected the confirmation messages for the same proposal from the majority of acceptors, it will be rest assured that the value has been chosen.

As an alternative, if the number of learners is large, a small group of learners can be selected to receive the multicasts from the acceptors and they can relay the chosen value to the remaining learners. Yet another alternative is for each learner to periodically poll the acceptors to see if they have chosen a value.

If a learner wants to make sure that the value it has learned is indeed the value that has been chosen, it can ask a proposer to issue a new proposal. The result of this proposal would confirm whether or not the value is chosen.

### 6.2.3 Proof of Correctness

In this section, we provide a sketch of proof of correctness for the safety property of the Paxos algorithm. For the liveness property of the Paxos, we provide a discussion on the condition when the liveness holds and scenarios that prevent a value from being chosen.

The safety property S2 and S3 are obviously satisfied by the Paxos algorithm because the value chosen is not pre-defined. We prove that the Paxos algorithm satisfies the safety property S1 by contradiction. Assume that two different values, v1 and v2 are chosen. According to the Paxos algorithm, the only way for a value to be chosen is for the majority of acceptors to accept the same accept request from a proposer. Hence, a set of majority acceptors A1 must have accepted an accept request with a proposal [n1, v1], and similarly a set of majority acceptors A2 must have accepted an accept request with a proposal [n2, v2].

If the two proposal numbers are the same, i.e., n1 = n2, considering that the two sets A1 and A2 must intersect in least one acceptor, this acceptor must have accepted two different proposals with the same proposal number. This is impossible because according to the Paxos algorithm, an acceptor would ignore the prepare and accept requests with a proposal number identical to that of the prepare and/or accept requests that it has accepted.

If n1 ≠ n2, without loss of generality, assume that n1 < n2. We first further assume that n1 and n2 are for consecutive proposal rounds. A set of majority acceptors A1 must have accepted the accept request with a proposal number n1 before another set of majority acceptors A2 accepted the accept request with a proposal number n2 because an acceptor would ignore the prepare or accept request if it contains a proposal number smaller than the one it has acknowledged in response to a prepare request. Furthermore, according to the Paxos algorithm, the value selected by a proposer for the accept request must either come from an earlier proposal with the highest proposal number or a value of its own if no earlier proposal is included in the acknowledgement messages. Because A1 and A2 must intersect in at least one acceptor, and this acceptor must have accepted the accept request for the proposal [n1, v1] and the accept request for the proposal [n2, v2]. This is impossible because that acceptor would have included the proposal [n1, v1] in its acknowledgement to the prepare request for the proposal with proposal number n2, and the proposer must have selected the value v1 instead of v2.

If n1 and n2 are not consecutive proposals, any intermediate proposals must also select v1 as the value according to the above argument. This concludes the proof of correctness for the safety property S1.

The liveness of the Paxos algorithm cannot be guaranteed when two or more proposers propose concurrently. Consider the scenario illustrated in Figure 6.2. Assume that there are two competing proposers P1 and P2. P1 first completes the prepare phase and
