# Why Go programming?

Multithreading is supported by most of the programming languages, but race conditions and deadlocks create difficulties in creating the multithreaded application. For example, creating a new thread in Java consumes approximately 1 MB of the memory heap size. Now, consider a case wherein you need to spin thousands of such threads. Then, it will create out of memory.

Moreover, there is a limit to the number of cores you can add to the processors like quad-core and octa-core to increase processing power. You cannot keep on adding more cache to the processor in order to boost performance since there is a cost involved. Therefore, we are left with only one option to build a more efficient software having high performance.

Go provides a solution to the problem with goroutines. You can spin millions of them at a time since they consume ~2KB heap memory. Goroutines have faster startup time and they use more memory on a need basis only. Also, a single goroutine can run on multiple threads since goroutines and OS threads don’t have 1:1 mapping.