# Figure 6

G1 is running on the M and wants to make a blocking system call.

![](bbox=[0.095, 0.086, 0.853, 0.401])

Figure 6 is showing our basic scheduling diagram again this time Goroutine-1 is going to make a synchronous system call that will block M1.

# Figure 7

![](bbox=[0.095, 0.537, 0.875, 0.768])

In figure 7, the scheduler is able to identify that Goroutine-1 has caused the M to block. At this point, the scheduler detaches M1 from the P with the blocking Goroutine-1 still attached. Then the scheduler brings in a new M2 to service the P. At that point, Goroutine-2 can be selected from the LRQ and context switched on M2. If an M already exists of a previous swap, this transition is quicker than having to create a new M.