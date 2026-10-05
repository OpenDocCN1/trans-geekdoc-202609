receiving and proxying the command to the leader. Step 3 shows the leader executing it.

![](bbox=[0.153, 0.226, 0.77, 0.381])

Figure 10.3

Leader and follower is Raft terminology, and we use it because Swarm implements the Raft consensus algorithm to maintain a consistent cluster state across multiple highly-available managers.

The following good practices apply when it comes to manager HA:

+   1. Always deploy an odd number of managers
2. Don't deploy too many managers (3 or 5 is usually enough)
3. Spread managers across availability zones