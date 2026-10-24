is computationally expensive, with a message authentication code (MAC) [4]. The use of digital signatures or MACs also enables a replica to detect corrupted or altered messages.

The restrictions assumed for an adversary is that it has limited computation power so that it cannot break the cryptography techniques used to spoof a message (i.e., to produce a valid digital signature of a nonfaulty replica). It is also assumed that an adversary cannot delay a message delivery at a nonfaulty replica indefinitely.

# ## 7.2.2 Overview of the PBFT Algorithm

The PBFT algorithm is used to implement state machine replication where a client issues a request to the replicated server and blocks waiting for the corresponding reply. To tolerate f faulty replicas, 3f + 1 or more server replicas are needed. The PBFT algorithm has the following two properties:

+   * Safety. Requests received by the replicated server are executed atomically in a sequential total order. More specifically, all nonfaulty server replicas execute the requests in the same total order.
+   * Liveness. A client eventually receives the reply to its request provided that the message delivery delay does not grow faster than the time itself indefinitely.

The minimal number of replicas, n = 3f + 1, to tolerate f faulty replicas are optimal for any asynchronous system that ensures the safety and liveness properties. Because up to f replicas may be faulty and not respond, a replica must proceed to the next step once it has collected n - f messages from different replicas. Among the n - f messages, up to f of them might actually be sent by faulty replicas. To have any hope of reaching an agreement among the nonfaulty replicas, the number of messages from nonfaulty replicas must be greater than f (i.e., among the n - f messages collected, the number of messages from nonfaulty replicas must be the majority). Hence, n - 2f > f, which means the optimal number of replicas n = 3f + 1.

In the presence of faulty clients, the PBFT algorithm can only ensure the consistency of the state of nonfaulty replicas. Furthermore, the algorithm itself does not prevent the leaking of confidential information from the replicated server to an adversary.