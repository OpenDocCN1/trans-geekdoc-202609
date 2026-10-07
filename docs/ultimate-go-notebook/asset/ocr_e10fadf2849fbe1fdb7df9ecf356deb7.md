# Figure 9

![](bbox=[0.105, 0.085, 0.855, 0.345])

In figure 9, we have a multi-threaded Go program with two P’s servicing Goroutines each and a single Goroutine in the GRQ. What happens if one of the P’s services all of its Goroutines quickly?

# Figure 10

![](bbox=[0.105, 0.513, 0.855, 0.783])

In figure 10, P1 has no more Goroutines to execute. But there are Goroutines in a runnable state, both in the LRQ for P2 and in the GRQ. This is a moment where P1 needs to steal work. The rules for stealing work are as follows.

https://golang.org/src/runtime/proc.go