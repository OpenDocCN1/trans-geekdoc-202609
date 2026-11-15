Figure 3. Blockchain-based fault-tolerant distributed storage structure

![](bbox=[0.168, 0.138, 0.832, 0.375])

# Efficient Blockchain-Based Recovery Algorithm

# 1. Data Recovery for Single Node Failure

When developing regenerative codes, data storage and node repair are often segregated but not exposed. When mending data in nodes, no encoding and decoding operations are required to download data, and a single failing node in the system may be precisely repaired using a simple XOR operation. It was discovered that by adjusting the current basic regenerative codes, it is possible to extract the encoding form that can properly repair several failing at the same time, nodes repairing methods, and bandwidths are detailed. This proposed unique regenerative code’s coding approach is simple to implement with storage capacity closer to theoretical minimum node storage. Because of improved local repair capacity and low overheads of disc input/output, several nodes in the connection system can quickly repair multiple failed nodes when specific conditions are satisfied, resulting in a high practical application value.

When a new storage node is added to the blockchain cloud storage system, it is supposed to distribute evenly to local codes, as well as ensure the construction of high fault-tolerant local regenerative codes while keeping the count of local codes a constant as lengths of local codes increase. If l storage nodes are added to the local code, the bandwidth cost of creating high fault-tolerant local regenerative code is reduced and the expanded code, the system’s information bits are preserved but the check bits are increased to l/2. The enhanced code (n_L + l/2, k, d’min + l/2) corresponding to the local code (n_L, k, d’min) is being built. At present time, the system’s minimum distance for expanded code is d’min + l/2.