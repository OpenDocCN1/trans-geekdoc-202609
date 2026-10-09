![](bbox=[0.1, 0.1, 0.9, 0.55])

**Figure 3.47** ◆ Four senders, routers with finite buffers, and multihop paths

Let’s consider the connection from Host A to Host C, passing through routers R1 and R2. The A–C connection shares router R1 with the D–B connection and shares router R2 with the B–D connection. For extremely small values of λin, buffer overflows are rare (as in congestion scenarios 1 and 2), and the throughput approximately equals the offered load. For slightly larger values of λin, the corresponding throughput is also larger, since more original data is being transmitted into the network and delivered to the destination, and overflows are still rare. Thus, for small values of λin, an increase in λin results in an increase in λout.

Having considered the case of extremely low traffic, let’s next examine the case that λin (and hence λ'in) is extremely large. Consider router R2. The A–C traffic arriving to router R2 (which arrives at R2 after being forwarded from R1) can have an arrival rate at R2 that is at most R, the capacity of the link from R1 to R2, regardless of the value of λ'in. If λ'in is extremely large for all connections (including the