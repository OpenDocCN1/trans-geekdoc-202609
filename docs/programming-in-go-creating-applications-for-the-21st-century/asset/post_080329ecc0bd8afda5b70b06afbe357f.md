
## 7.1. Key Concepts

In concurrent programming we typically want to split up the processing that needs doing over one or more goroutines (in addition to the main orchestrating goroutine), and either output results as soon as they are computed or gather the results for outputting at the end.

Even with Go’s high-level approach to concurrency there are pitfalls that we must avoid. One such pitfall is when the program finishes almost immediately but produces no results. Go programs automatically terminate when the main goroutine terminates—even if other goroutines are processing at the time—so we must be careful to keep the main goroutine alive enough for all the work to be done.

Another pitfall must be avoided. One form of problem is essentially the opposite of the first pitfall: The main goroutine and all the processing goroutines are alive even though all the work has been done. This is typically due to a failure to report the completion of processing. Another cause of deadlock is when two different goroutines (threads) are using locks to protect resources and try to acquire the same locks at the same time, as illustrated in Figure 7.1. This kind of deadlock can only occur when locking is used, so is a common risk in other languages but quite rare in Go, since Go applications can avoid the use of locks by using channels.

![](img/005bb569dac79e0facc29f476bd67ade_333_0.png)

**Figure 7.1** Deadlock: two or more blocked threads trying to acquire each’s locks

The common way to avoid premature termination and nontermination is to make the main goroutine wait for a “done” channel to report that the work is finished (as we will see in a moment, and also in §7.2.2, ➤ 326 and §7.2.4, ➤ 341). (It is also possible to use a sentinel value to act as the “result”, but this is rather clumsy compared to the other approaches.)

Another way to avoid the pitfalls is to wait for all the processing goroutines to report that they are finished using a sync.WaitGroup. However, using a sync.WaitGroup itself can cause a deadlock, particularly if the sync.WaitGroup.Wait() occurs in the main goroutine when all the processing goroutines are blocked (e.g., waiting to receive on a channel). We will see how to use a sync.WaitGroup later (§7.2.5, ➤ 349).

It is still possible to get deadlocks in Go, even if we use only channels, and not use locks. For example, suppose we have a set of goroutines that can ask each other to execute functions (e.g., by sending requests to each other). Now if one of the requested functions does send to the goroutine in which it is executing—for example, to pass some data—we will get a deadlock. This is illustrated in Figure 7.2. (Later on we will see an example where this kind of deadlock is possible; ➤ 337 and ➤ 340.)

![](img/005bb569dac79e0facc29f476bd67ade_334_0.png)

**Figure 7.2** Deadlock: a goroutine that tries to service a request with a request to itself

Channels provide a lock-free means of communication between concurrently running goroutines. (Under the hood locks may be used, but are implementation detail that we don't have to concern ourselves with.) When a channel communication takes place, at the moment of communication the sending and receiving channels (and their respective goroutines) are synchronized.

By default channels are bidirectional, that is, we can send values into and receive values from them. However it is quite common for a channel that is a field in a struct or channel that is passed as a parameter to be unidirectionally, that is, only to be sent to, or only to be received from. In such cases we can express the semantics (and force the compiler to check for us) by specifying the channel's direction. For example, the type `<-Type` is a receive-only channel. We have not used this syntax in earlier chapters, because it is never required—we can always use chan instead—and there was plenty of other material to learn. But from now on we will use unidirectional channels wherever they are appropriate, since they provide additional compile-time checking and are best practice.

Sending values as bools, ints, and float64s through channels is intrinsically safe since they are copied, there is no risk of inadvertent concurrent access to them. Similarly, sending strings is safe because they are immutable.

Sending pointers or references (e.g., slices or maps) through channels is not intrinsically safe since the pointed-to or referred-to value could be changed by the sending goroutine and by receiving goroutine at the same time—with unpredictable results. So, when it comes to pointers and references, we must make sure that they are ever accessed by one goroutine at any one time, that is, accesses must be serialized. The exception is where the documentation specifically says it is safe to pass a pointer—for example, the same `regexp.Regexp` can be safely used in many goroutines as we like, because none of the methods called on the pointed-value change the value's state.

One way to serialize accesses to use mutexes. Another way is to apply a policy that a pointer or reference is only sent once, and once sent the sender never accesses it again. This leaves the receiver free to access the pointed-to or referred-value—and to send on the pointer or referred-value.
