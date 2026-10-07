# Figure 3

![](bbox=[0.118, 0.085, 0.881, 0.206])

Figure 3 shows how the collector took P1 for itself during the collection. Now the collector can start the Marking phase. The Marking phase consists of marking values in heap memory that are still in-use. This work starts by inspecting the stacks for all existing Goroutines to find root pointers to heap memory. Then the collector must traverse the heap memory graph from root pointers. While the Marking work is happening on P1, application work can continue concurrently on P2, P3 and P4. This means the impact of the collector has been minimized to 25% of the current CPU capacity.

I wish that was the end of the story, but it isn't. What if it's identified during the collection that the Goroutine dedicated to GC on P1 will not finish the Marking work before the heap memory in-use reaches its goal limit by the collection before starting? In this case, new allocations have to be slowed down and specifically from those Goroutines.

If the collector determines that it needs to slow down allocations, it will recruit the application Goroutines to assist with the Marking work. This is called a Mark Assist. The amount of time any Goroutine will be placed in a Mark Assist is proportional to the amount of data it's adding to heap memory. One positive side effect of Mark Assist is that it helps to finish the collection faster.

# Figure 4

![](bbox=[0.118, 0.706, 0.881, 0.827])

Figure 4 shows how the application Goroutine running on P3 is now performing a Mark Assist and helping with the collection work. Hopefully the other application Goroutines don't need to get involved as well. Applications that allocate heavy