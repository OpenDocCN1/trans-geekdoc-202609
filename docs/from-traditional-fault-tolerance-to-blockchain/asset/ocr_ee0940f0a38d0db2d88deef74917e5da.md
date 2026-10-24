# 7.2.3 Normal Operation of PBFT

During normal operation, i.e., when the primary is not faulty, the server replicas can establish and agree on the total order of each request in three phases (referred to as pre-prepare, prepare, and commit phases), as shown in Figure 7.4. PBFT also requires each replica to log both application messages (requests received and reply generated), and control messages that sent during the three phases to achieve Byzantine agreement on the total order of messages.

![](bbox=[0.2, 0.31, 0.78, 0.56])

Figure 7.4 Normal operation of the PBFT algorithm.

During the first phase, i.e., the pre-prepare phase, when the primary receives a new request m, it assigns the next available sequence number s to the request and multicasts a pre-prepare message to the backups. The pre-prepare message has the form <PRE-PREPARE, v, s, d>_sigma_p, where d is the digest for the request m.

A backup verifies a pre-prepare message in the following way before it accepts the message:

+   - The pre-prepare message has a valid digital signature.
+   - The backup is in view v and it has not accepted a pre-prepare message with sequence number s.
+   - Furthermore, the sequence number is within the expected range bounded by a low water mark h and a high water mark H. This is to prevent a faulty primary to exhaust the address space of the sequence number (to avoid the sequence number wrap-around problem).