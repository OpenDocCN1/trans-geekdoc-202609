
nodes in that membership. Hence, we use the terms multicast and broadcast interchangeably. Furthermore, a node ignores messages sent by nodes that do not belong to the current membership (often referred to as foreign messages), unless they are membership-change related messages (such as the rejoin request). This means that we assume a closed, single group system.

A group communication system must define two protocols, one for normal operation when all nodes in the current membership can communicate with each other in a timely fashion, and the other for membership change when one or more nodes are suspected as failed, or when the failed nodes are restarted. These protocols work together to ensure the safety properties and the liveness property of the group communication system.

We define two levels of safety properties for total ordering [13]:

- Uniform total ordering: Given any message that is broadcast, if it is delivered by a node according to some total order, then it is delivered in every node in the same total order unless the node has failed.

- Nonuniform total ordering: Given a set of messages that have been broadcast and totally ordered, no node delivers any of them out of the total order. However, there is no guarantee that if a node delivers a message, then all other nodes deliver the same message.

Figure 5.1 highlights the differences between uniform total ordering and nonuniform total ordering. In uniform total ordering, if a message is delivered by any node, it is delivered by all nodes in the current membership except for those that have failed (such as N1). Hence, the messages delivered by the nodes that failed subsequently after joining the membership would form a prefix of those delivered by the nodes that remain operating, assuming that the nodes initially joined the system (i.e., the current or a previous membership view) at the same time. For example, the messages delivered by N1, m1 m2 m3 form a prefix of the messages (m1 m2 m3 m4 m5 m6) delivered by N2 N3 and N4. Note that N5 joined after N1 failed, and therefore, the messages delivered by N1 do not form a prefix of the messages delivered by N5.

In nonuniform total ordering, however, this might not be the case. For example, as shown in Figure 5.1, N1 broadcasts message m4 and delivers it, and only N2 receives and delivers the message m4 and none of the other nodes. N1 and N2 subsequently failed before other nodes learn about m4. Hence, the messages delivered by N1 and N2, which are m1 m2 m3 m4, do not form a prefix of the messages delivered at N3 and N4, which are m1 m2 m3 m5 m6.

The uniform total ordering safety property is a strong property. It may be needed for applications that expose their state to components that are not part of the group communication system. For example, a replicated database system would require the uniform total ordering safety property to ensure replica consistency. However, for many applications, the nonuniform total ordering safety property would suffice. The only scenario that the uniform delivery cannot be ensured is when both the sender and the receivers (a portion of the N nodes in the system) of a message fail before other nodes learn about the message. If a node loses its state after it fails, or does not expose its state to other components of the system, such nonuniformity would not cause any negative side effect. In general, nonuniform total ordering can be achieved much faster than uniform total ordering.

The liveness of a group communication system means that if a nonfaulty node multicasts a message, it will eventually be delivered in a total order at other nodes. Liveness is ensured by fault tolerance mechanisms. For a message loss, it is addressed by retransmission. Node failures, extended delay in processing, and message propagations, are addressed by membership reconfigurations (i.e., view changes).

## 5.2 Sequencer Based Group Communication System

Ensuring reliable broadcast is challenging because a protocol must support multiple senders broadcasting to multiple receivers. Guaranteeing totally ordered reliable broadcast is even more so. The first practical approach to ensuring reliable and total ordering of broadcast messages is introduced in [12]. In this approach, as shown in Figure 5.2, a general system is structured into a combination of two much simpler subsystems:

![](img/7320b1480d74f1d65f74659cab456782_183_0.png)

Figure 5.2 In the sequencer based approach, a general system is structured into a combination of two subsystems, one with a single receiver and the other with a single sender of broadcast messages.

- Multiple senders with a single receiver.
- A single sender with multiple receivers.

The single receiver and the single sender of broadcast messages are in fact served by a single node. Therefore, all broadcast messages sent by the multiple senders are effectively funneled through this special node, which is often referred to as the sequencer. This sequencer is responsible to assign a global sequence number for each broadcast message, thereby ensuring total ordering.

The simplest implementation of the sequencer based approach is to use a dedicated node, sometimes referred to as static sequencer. A node delivers a message that has been assigned a global sequence number if it has received and delivered all messages that carry smaller sequence numbers. Obviously, the sequencer constitutes a single point of failure. To ensure liveness, the sequencer is expected to periodically broadcast sequencing messages, even if no broadcast message is sent, and the other nodes would time out the sequencer if they do not receive sequencing messages for a number of times. Subsequently, the surviving nodes elect another node to act as the sequencer. This approach is used in [14]. It is apparent that only the nonuniform safety property is guaranteed. Furthermore, it is not clear whether or not the system is designed to offer view synchrony.

A more robust sequencer based group communication system was described in [12]. To achieve uniform total ordering, the nodes in the system take turn to serve as the sequencer, and a node does not deliver a message until it has received several sequencing messages from different sequencers. Given a failure resiliency of f (i.e., at most f nodes may become faulty), the total number of nodes N in the system must satisfy N > 2f. This approach is often referred to as rotating sequencer based approach. In this section, we describe the rotating sequencer based approach in detail. In the original paper, the sequencer is referred to as the token site because the rotation of the sequencer role among the nodes resembles a token circulation among the nodes in the system (i.e., the node that has the token becomes the sequencer). In this section, we choose not to use the term “token” to avoid confusion with another approach that uses the token differently (to be described in Section 5.3).

### 5.2.1 Normal Operation

During normal operation, we assume that a membership has been formed. Each node in the current membership maintains the following data structures:

- A view number v for the current membership and the corresponding list of node identifier in the current view. For convenience, we assume that each node is assigned an index and we use the node’s index number to refer to the node.

- A local sequence number vector M[] with each element representing the expected local sequence number for the corresponding node in view v. For example, M[i] refers to the expected local sequence number carried by the next message sent by node i. Initially, every element is set to 0.

- The expected global sequence number s that is carried in the next sequencing message sent by the sequencer node.

After the formation of a membership, one of the nodes is designated as the initial sequencer. The membership also dictates the rank of each node so that a node knows when it should take over as the next sequencer.

The normal operation protocol involves three phases for each message to be totally ordered:

- Transmitting phase. A node broadcasts a message to all nodes in the current membership and waits for a sequencing message from the sequencer for the broadcast message. A broadcast message is denoted as B(v,i,n), where v is the current view number, i is the sending node index number, and n is the local sequence number n for the message. The local sequence number is initially set to 0. For each new broadcast message, the local sequence number is incremented by 1. This mechanism is needed to ensure the reliability of message delivery. The sending node retransmits the same message if it does not receive the sequencing message in a timely fashion. When a node j receives the broadcast message B(v,i,n), it accepts the message if it is in the same view and stores the message in its message queue Q_B.

- Sequencing phase. When the sequencer receives a broadcast message B(v,i,n), it verifies that the message is the next expected message from node i, i.e., M[i] = n. The sequencer then assigns the current global sequencer value s to message B(v,i,n) and broadcasts a sequencing message in the form SEQ(s,v,[i,n]), where [i,n] is the identifier for the broadcast message B(v,i,n). When a node j receives a sequencing message, it accepts the message provided that:

  - The global sequence number in the message matching its expected global sequence number, and
