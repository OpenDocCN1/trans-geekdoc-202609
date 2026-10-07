![](bbox=[0.125, 0.053, 0.875, 0.355])

In figure 5, the asynchronous network system call is completed by the network poller and Goroutine-1 is moved back into the LRQ for the P. Once Goroutine-1 can be context switched back on the M, the Go related code it's responsible for can execute again. The big win here is that, to execute network system calls, no extra Ms are needed. The network poller has an OS Thread and it is handling an efficient event loop.

# Synchronous System Calls

What happens when the Goroutine wants to make a system call that can't be done asynchronously? In this case, the network poller can't be used and the Goroutine making the system call is going to block the M. This is unfortunate but there's no way to prevent this from happening. One example of a system call that can't be made asynchronously is file-based system calls. If you are using CGO, there may be other situations where calling C functions block the M as well.

Let's walk through what happens with a synchronous system call (like file I/O) that will cause the M to block.