![](bbox=[0.22, 0.12, 0.78, 0.58])

Figure 14.6 Globus security policy architecture.

# 14.5 Distribution of Security Mechanism

The dependency existing among services concerning trust gives rise to the notion of a Trusted Computing Base (TCB). A TCB represents a set of all security mechanisms in a distributed computer system that are necessary for ensuring a security policy, and which are required to be trusted. The smaller the TCB is, the better it will be. Furthermore, TCB in a distributed system can incorporate the local operating systems at several hosts. A file server in a distributed file system might need to to be believed on the several protection mechanisms afforded by corresponding local operating system. Moreover, middleware-based distributed systems need to trust in the existing local operating systems. If no trust exists, then part of the functionality of the local operating systems has to be incorporated into the distributed system itself.