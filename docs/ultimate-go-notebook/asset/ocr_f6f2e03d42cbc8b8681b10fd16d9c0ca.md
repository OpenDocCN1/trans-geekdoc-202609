![](bbox=[0.125, 0.055, 0.875, 0.535])

In figure 16, Threads context switch once again as the message by Thread 2 is received by Thread 1. Now Thread 2 context switches from the executing state to the waiting state and Thread 1 context switches from the waiting state to the runnable state and finally back to the executing state, which allows it to process and send a new message back.

All these context switches and state changes require time to be performed which limits how fast the work can get done. With each context switching potential incurring a latency of ~1000ns and hopefully the hardware executing 12 instructions per nanosecond, you are looking at 12k instructions, more or less, not executing during these context switches. Since these Threads are bouncing between different Cores, the chances of incurring additional latency due to cache-line misses are also high.

Let's take this same example but use Goroutines and the Go scheduler instead.