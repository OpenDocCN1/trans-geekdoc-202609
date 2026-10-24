
be relied upon for recovery. Therefore, to ensure that the recovered state is consistent with the external view, sufficient recovery information must be logged prior to the sending of a message to the outside world. This is the so-called output commit problem [21].

### 2.1.5 Stable Storage

An essential requirement for logging and checkpointing protocols is the availability of stable storage. Stable storage can survive process failures in that upon recovery, the information stored in the stable storage is readily available to the recovering process. As such, all checkpoints and messages logged must be stored in stable storage.

There are various forms of stable storage. To tolerate only process failures, it is sufficient to use local disks as stable storage. To tolerate disk failures, redundant disks (such as RAID-1 or RAID-5 [14]) could be used as stable storage. Replicated file systems, such as the Google File System [9], can be used as more robust stable storage.

## 2.2 Checkpoint-Based Protocols

Checkpoint-based protocols do not rely on the piecewise deterministic assumption, hence, they are simpler to implement and less restrictive (because the developers do not have to identify all forms of nondeterministic events and log them properly). However, a tradeoff is that the distributed systems that choose to use checkpoint-based protocols must be willing to tolerate loss of execution unless a checkpoint is taken prior to every event, which is normally not realistic.

### 2.2.1 Uncoordinated Checkpointing

Uncoordinated checkpointing, where each process in the distributed system enjoys full autonomy and can decide when to take checkpoints, even though it appears to be attractive, is not recommended for two primary reasons.

First, the checkpoints taken by the processes might not be useful to reconstruct a consistent global state. In the worst case, the system might have to do a cascading rollback to the initial system state (often referred to as the domino effect [16]), which completely defeats the purpose of doing checkpointing. Consider the following example.

### EXAMPLE 2.2

![](img/7320b1480d74f1d65f74659cab456782_59_0.png)

Figure 2.3 An example of the domino effect in recovery with uncoordinated checkpointing.

In the example illustrated in Figure 2.3, process P1 crashed after it has sent message m8 to P0, but before it has a chance to take a checkpoint. The last checkpoint taken by P1 is C1,1. Furthermore, P2 also crashed concurrently. Now, let's examine the impact of the failure of P1 and P2:

- The most recent checkpoint at P0, C0,1, cannot be used because it is inconsistent with C1,1. Therefore, P0 would have to rollback to C0,0.
- The most recent checkpoint at P1, C1,1, cannot be used because it is inconsistent with C2,1, i.e., C1,1 reflected the receiving of m6 but C2,1 does not reflect the sending of m6. This means that P1 would have to rollback to C1,0.
- Unfortunately, C2,1 is not consistent with C1,0 because it recorded the receiving of m4 while C1,0 does not reflect the sending of m4. This means P2 would have to rollback to C2,0.
- This in turn would make it impossible to use any of the two checkpoints, C3,1 or C3,0, at P3. This would result in P3 rolling back to its initial state.
- The rollback of $P_3$ to its initial state would cause the invalidation of $C_{2,0}$ at $P_2$ because it reflects the state change resulted from the receiving of $m_1$, which is not reflected in the initial state of $P_3$. Therefore, $P_2$ would have to be rolled back to its initial state too.
- The rollback of $P_1$ to $C_{1,0}$ would invalidate the use of $C_{0,0}$ at $P_0$ because of $m_5$. This means that $P_0$ would have to rollback to its initial state too.
- Finally, the rollback of $P_0$ to its initial state would invalidate the use of $C_{1,0}$ at $P_1$, thereby forcing $P_1$ to rollback to its initial state. Consequently, the distributed system can only recover to its initial state.

Second, to enable the selection of a set of consistent checkpoints during recovery, the dependency of the checkpoints has to be determined and recorded together with each checkpoint. This would incur additional overhead and increase the complexity of the implementation [2]. As a result, the uncoordinated checkpointing is not as simple as and not as efficient as one would have expected [3].

### 2.2.2 Tamir and Sequin Global Checkpointing Protocol

In this coordinated checkpointing protocol due to Tamir and Sequin [22], one of the processes is designated as the coordinator and the remaining processes are participants. The coordinator must know all other processes in the system. The coordinator uses a two-phase commit protocol to ensure that not only the checkpoints taken at individual processes are consistent with each other, the global checkpointing operation is carried out atomically, that is, either all processes successfully create a new set of checkpoints or they abandon the current round and revert back to their previous set of checkpoints. The objective of the first phase is to create a quiescent point of the distributed system, thereby ensuring the consistency of the individual checkpoints. The second phase is to ensure the atomic switchover from the old checkpoint to the new one. When a participant fails to respond to the coordinator in a timely fashion, the coordinator aborts the checkpointing round.

### 2.2.2.1 Protocol Description.

The finite state machine specifications for the coordinator and the participant are provided in Figure 2.4 and Figure 2.5, respectively.

### Final State Machine for Coordinator

![](img/7320b1480d74f1d65f74659cab456782_61_0.png)

Figure 2.4 Finite state machine specification for the coordinator in the Tamir and Sequin checkpointing protocol.

Note that in the finite state machine specification for the coordinator as shown in Figure 2.4, the normal state is shown twice, once at the beginning (as ‘init’) and the other at the end, for clarity.

More detailed explanation of the protocol rule for the coordinator and the participant is given below. In the description of the protocol, the messages exchanged between the processes in between two rounds of global checkpointing are referred to as regular messages (and the corresponding execution is termed as normal execution), to differentiate them from the set of control messages introduced by the protocol for the purpose of coordination:

- CHECKPOINT message. It is used to initiate a global checkpoint. It is also used to establish a quiescent point of the distributed system where all processes have stopped normal execution.
- SAVED message. It is used for a participant to inform the coordinator that it has done a local checkpoint.
- FAULT message. It is used to indicate that a timeout has occurred and the current round of global checkpointing should be aborted.
- RESUME message. It is used by the coordinator to inform the participants that they now can resume normal execution.

### Final State Machine for Participant

![](img/7320b1480d74f1d65f74659cab456782_62_0.png)

Figure 2.5 Finite state machine specification for the participant in the Tamir and Sequin checkpointing protocol.

### Rule for the coordinator:

- At the beginning of the first phase, the coordinator stops its normal execution (including the sending of regular messages) and sends a CHECKPOINT message along each of its outgoing channels.
- The coordinator then waits for the corresponding CHECKPOINT message from all its incoming channels.
- While waiting, the coordinator might receive regular messages. Such messages are logged and will be appended to the checkpoint of its state. This can only happen from an incoming channel from which the coordinator has not received the CHECKPOINT message.
- The coordinator aborts the checkpointing round if it fails to receive the CHECKPOINT message from one or more incoming channels within a predefined time period.
- When the coordinator receives the CHECKPOINT message from all its incoming channels, it proceeds to take a checkpoint of its state.
- Then, the coordinator waits for a SAVED notification from every process (other than itself) in the distributed system. It aborts the checkpointing round if it fails to receive the SAVED message from one or more incoming channels within a predefined time period. It does so by sending a FAULT message along each of its outgoing channels. Note that it is impossible for the coordinator to receive any regular message at this stage.
- When the coordinator receives the SAVED notification from all other processes, it switches to the new checkpoint, and sends a RESUME message along each of its outgoing channels.
- The coordinator then resumes normal execution.

### Rule for the participant:

- Upon receiving a CHECKPOINT notification, the participant stops its normal execution and in turn sends a CHECKPOINT message along each of its outgoing channels.
- The participant then waits for the corresponding CHECKPOINT message from all its incoming channels.
- While waiting, the participant might receive regular messages. Such messages are logged and will be appended to the checkpoint of its state. Again, this can only happen from an incoming channel from which the participant has not received the CHECKPOINT message.
- The participant aborts the checkpointing round by sending a FAULT message along each of its outgoing channels if it fails to receive the CHECKPOINT message from one or more incoming channels within a predefined time period.
- Once the participant has collected the set of CHECKPOINT messages, it takes a checkpoint of its state.
