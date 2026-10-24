must have received the corresponding ORDER message sent by \( P_i \). Hence, upon recovery, \( P_k \) will be contacted by \( P_i \) and the regular message with a valid \( rsn \) value will be retransmitted to \( P_i \). This would ensure the recovering process \( P_i \) to reinitiate the state interval in the correct order. The regular message received by \( P_j \) will be correctly regenerated and logged at \( P_i \) during recovery. This completes our proof.

# 2.3.2.5 Discussion.

As we have mentioned before, unlike the receiver-based pessimistic logging, performing a local checkpointing at a process does not truncate its message log because the log contains messages sent to other processes and they might be needed for the recovery of these other processes. This is rather undesirable. Not only it means unbounded message log size, but it leads to unbounded recovery time as well.

The sender-based message logging protocol can be modified to at least partially fix the problem. However, it will be at the expense of the locality of local checkpointing. Once a process completes a local checkpoint, it broadcasts a message containing the highest \( rsn \) value for the messages that it has executed prior to the checkpoint. All messages sent by other processes to this process that were assigned a value that is smaller or equal to this \( rsn \) value can now to purged from its message log (including those in stable storage as part of a checkpoint). Alternatively, this highest \( rsn \) value can be piggybacked with each message (regular or control messages) sent to another process to enable asynchronous purging of the logged messages that are no longer needed.

# REFERENCES

+   1. L. Alvisi and K. Marzullo. Message logging: Pessimistic, optimistic, causal, and optimal. IEEE Trans. Softw. Eng., 24(2):149–159, Feb. 1998.
+   
+   2. B. K. Bhargava and S.-R. Lian. Independent checkpointing and concurrent rollback for recovery in distributed systems - an optimistic approach. In Symposium on Reliable Distributed Systems, pages 3–12, 1988.
+   
+   3. B. K. Bhargava, S.-R. Lian, and P.-J. Leu. Experimental evaluation of concurrency checkpointing and rollback-recovery algorithms. In ICDE, pages 182–189. IEEE Computer Society, 1990.