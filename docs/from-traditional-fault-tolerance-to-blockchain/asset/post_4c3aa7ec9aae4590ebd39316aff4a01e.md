
- 1. Immediately change the quorum size from $f + 1$ to $f + 2$ after adding the first replica to the system, as shown in Figure 6.15. Note that the bigger quorum does not mean higher failure resiliency at this stage because the system can only tolerate $f$ faulty replicas. The bigger quorum ($f + 2$) must be used when adding the second replica. Not enlarging the quorum size might result in two different values be chosen.

- 2. As shown in Figure 6.16, after the first replica is added to the system, it is not allowed to participate in any Paxos instance until the second replica is also added. At this stage, the new member is only marked. The quorum size remains to be $f + 1$ after the first replica is added. Only original group of replicas participate in the Paxos instance to add the second replica into the system. Immediately after the second replica is added, the quorum is changed to $f + 2$.

![](img/7320b1480d74f1d65f74659cab456782_270_0.png)

## 6.6.3.3 Membership Reduction

Similar to membership expansion, if the replication degree is to be reduced, two replicas must be removed from the membership at a time. To leave the current membership, a replica multicast a leave request to all other members and the leave request is totally ordered with respect to all other requests.

Membership reduction is more subtle than membership expansion due to the fact that other replicas might become faulty in due course. For example, if after the decision of reducing the membership size is made, another replica becomes faulty, the system should remove only one more replica from the system. If on the other hand, two replicas become faulty, no other replicas should be removed from the membership. This observation calls for the following conservative approach in removing replicas.

![](img/7320b1480d74f1d65f74659cab456782_271_0.png)

As shown in Figure 6.17, when a leave request is executed, the replica is only marked for removal and the quorum size is not changed. That replica should continue participating the Paxos algorithm as usual. Only when the second leave request is executed, do both replicas be removed from the membership, and the quorum size is reduced by one. If before the second leave request is executed, another replica becomes faulty, the faulty replica together with the first marked replica are removed. Furthermore, the system administrator is alerted regarding the failure. If two other replicas become faulty, the originally marked replica is unmarked and again, the system administrator is alerted.

If the replica that issued the leave request is the primary, a planned view change would take place when the leave request is executed. Because it is the primary that initiates the view change, the current primary can pass on its latest status to the new primary without engaging a round message exchange. The new view can be installed immediately after the new primary is informed of the need for the new view.

The above discussion assumes that replicas themselves initiate the leave process. As an alternative, a system administrator could issue one request to remove two replicas at the same time, in which case, both replicas are removed after the request is totally ordered and executed.

## 6.6.4 Limited Disk Space for Logging

The Paxos algorithm did not provide any mechanism to truncate the logs. Because each acceptor must log its promises it has made and votes it has cast, the log might eventually saturate the disk without an appropriate log truncation mechanism. In Chubby, each replica periodically takes a snapshot (i.e., a checkpoint) of the application state and when the snapshot is fully recorded on local disk, the logged entries prior to the snapshot are truncated. The following mechanism is used so that the application layer and the fault tolerance framework layer are in sync when taking a snapshot:

- A snapshot handle is used to record the Paxos-specific information regarding a snapshot. Hence, the snapshot handle is always stored together with the actual snapshot.
- The application must first request a snapshot handle from the fault tolerance framework layer prior to taking a snapshot.
- While the application is taking a snapshot, the system does not stop processing new requests. To accomplish this, Chubby uses a shadow data structure to track the changes to the application’s state to ensure the state recorded in the application snapshot corresponds to the framework state as reflected in the snapshot handle.
- When the application finishes taking a snapshot, it informs the framework layer, using the snapshot handler as the identifier for the snapshot. The framework layer then can truncate the log according to the information contained in the handler.

The truncation of logs could lead to the inability for a replica to supply a log entry for a slow replica, in which case, the slow replica must recover via a state transfer by using the latest snapshot of another replica in the leading quorum, as we have described in Section 6.3.1. After applying the snapshot, the slow replica must also obtain all entries logged since the snapshot. If another snapshot is taken and the log is truncated accordingly while the slow replica is applying the snapshot, it would have to request a new state transfer.

## REFERENCES

- 1. Y. Amir and J. Kirsch. Paxos for system builders: An overview. In Proceedings of the Workshop on Large-Scale Distributed Systems and Middleware, Yorktown, NY, September 2008.
- 2. W. J. Bolosky, D. Bradshaw, R. B. Haagens, N. P. Kusters, and P. Li. Paxos replicated state machines as the basis of a high-performance data store. In Proceedings of the 8th USENIX Symposium on Networked Systems Design and Implementation, 2011.
- 3. M. Burrows. The chubby lock service for loosely-coupled distributed systems. In Proceedings of the 7th symposium on Operating systems design and implementation, OSDI ’06, pages 335–350, Berkeley, CA, USA, 2006. USENIX Association.
- 4. M. Castro and B. Liskov. Practical byzantine fault tolerance and proactive recovery. ACM Transactions on Computer Systems, 20(4):398–461, 2002.
- 5. T. D. Chandra, R. Griesemer, and J. Redstone. Paxos made live: an engineering perspective. In Proceedings of the twenty-sixth annual ACM symposium on Principles of distributed computing, PODC ’07, pages 398–407, New York, NY, USA, 2007. ACM.
- 6. M. J. Fischer, N. A. Lynch, and M. S. Paterson. Impossibility of distributed consensus with one faulty process. J. ACM, 32(2):374–382, Apr. 1985.
- 7. C. Gray and D. Cheriton. Leases: an efficient fault-tolerant mechanism for distributed file cache consistency. In Proceedings of the twelfth ACM symposium on Operating systems principles, SOSP ’89, pages 202–210, New York, NY, USA, 1989. ACM.
- 8. Z. Guo, C. Hong, M. Yang, D. Zhou, L. Zhou, and L. Zhuang. Paxos made parallel. Technical report, Microsoft Research, 2012.
- 9. F. Junqueira, Y. Mao, and K. Marzullo. Classic paxos vs. fast paxos: caveat emptor. In Proceedings of the 3rd workshop on Hot Topics in System Dependability, HotDep’07, Berkeley, CA, USA, 2007. USENIX Association.
- 10. L. Lamport. Paxos made simple. ACM SIGACT News (Distributed Computing Column), 32(4):18–25, December 2001.
- 11. L. Lamport. Generalized consensus and paxos. Technical report, Microsoft Research, March 2005.
- 12. L. Lamport. Fast paxos. Distributed Computing, 19(2):79–193, 2006.
- 13. L. Lamport, D. Malkhi, and L. Zhou. Vertical paxos and primary-backup replication. In Proceedings of the 28th ACM symposium on Principles of distributed computing, PODC ’09, pages 312–313, New York, NY, USA, 2009. ACM.
- 14. L. Lamport and M. Massa. Cheap paxos. In Proceedings of the 2004 International Conference on Dependable Systems and Networks, DSN ’04, pages 307–314, Washington, DC, USA, 2004. IEEE Computer Society.
- 15. G. M. D. Vieira and L. E. Buzato. On the coordinator’s rule for fast paxos. Inf. Process. Lett., 107(5):183–187, Aug. 2008.
