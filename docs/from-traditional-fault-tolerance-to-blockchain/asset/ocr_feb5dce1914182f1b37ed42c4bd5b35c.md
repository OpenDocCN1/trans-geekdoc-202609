# List of Figures

+   1.1 An example of a chain of threats with two levels of recursion. 4
+   1.2 The rollback recovery is enabled by periodically taking checkpoints and usually logging of the requests received. 12
+   1.3 With redundant instances in the system, the failure of a replica in some cases can be masked and the system continue providing services to its clients without any disruption. 12
+   1.4 Main types of assets in a distributed system. 14
+   2.1 An example distributed system. 22
+   2.2 Consistent and inconsistent global state examples. 24
+   2.3 An example of the domino effect in recovery with uncoordinated checkpointing. 28
+   2.4 Finite state machine specification for the coordinator in the Tamir and Sequin checkpointing protocol. 30
+   2.5 Finite state machine specification for the participant in the Tamir and Sequin checkpointing protocol. 31
+   2.6 Normal operation of the Tamir and Sequin checkpointing protocol in an example three-process distributed system. 33
+   2.7 Finite state machine specification for the Chandy and Lamport distributed snapshot protocol. 36
+   2.8 Normal operation of the Chandy and Lamport global snapshot protocol in an example three-process distributed system. 38
+   2.9 A comparison of the channel state definition between (a) the Chandy and Lamport distributed snapshot protocol and (b) the Tamir and Sequin global checkpointing protocol. 39
+   2.10 Example state intervals. 41
+   2.11 An example for pessimistic logging. 43
+   2.12 Transport level (a) and application level (b) reliable messaging. 46
+   2.13 Optimization of pessimistic logging: (a) concurrent message logging and execution (b) logging batched messages. 47
+   2.14 Probability density function of the logging latency. 48