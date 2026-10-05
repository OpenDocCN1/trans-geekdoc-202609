# 318

# Chapter 7. Concurrent Programming

other to execute functions (e.g., by sending requests to each other). Now if one of the requested functions does send to the goroutine in which it is executing—for example, to pass some data—we will get a deadlock. This is illustrated in Figure 7.2. (Later on we will see an example where this kind of deadlock is possible; ➤ 337 and ➤ 340.)

![](bbox=[0.235, 0.203, 0.873, 0.329])

**Figure 7.2** Deadlock: a goroutine that tries to service a request with a request to itself

Channels provide a lock-free means of communication between concurrently running goroutines. (Under the hood locks may be used, but are implementation detail that we don't have to concern ourselves with.) When a channel communication takes place, at the moment of communication the sending and receiving channels (and their respective goroutines) are synchronized.

By default channels are bidirectional, that is, we can send values into and receive values from them. However it is quite common for a channel that is a field in a struct or channel that is passed as a parameter to be unidirectionally, that is, only to be sent to, or only to be received from. In such cases we can express the semantics (and force the compiler to check for us) by specifying the channel's direction. For example, the type<- Type is a receive-only channel. We have not used this syntax in earlier chapters, because it is never required—we can always use chan instead—and there was plenty of other material to learn. But from now on we will use unidirectional channels wherever they are appropriate, since they provide additional compile-time checking and are best practice.

Sending values as bools, ints, and float64s through channels is intrinsically safe since they are copied, there is no risk of inadvertent concurrent access to them. Similarly, sending strings is safe because they are immutable.

Sending pointers or references (e.g., slices or maps) through channels is not intrinsically safe since the pointed-to or referred-to value could be changed by the sending goroutine and by receiving goroutine at the same time—with unpredictable results. So, when it comes to pointers and references, we must make sure that they are ever accessed by one goroutine at any one time, that is, accesses must be serialized. The exception is where the documentation specifically says it is safe to pass a pointer—for example, the same *regexp.Regexp can be safely used in many goroutines as we like, because none of the methods called on the pointed-value change the value's state.