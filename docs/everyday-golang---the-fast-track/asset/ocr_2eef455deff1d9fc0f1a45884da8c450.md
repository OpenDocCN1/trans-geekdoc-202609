```
fmt.Printf("- %s = error: %s\n", k, v.Error.Error())
    } else {
        fmt.Printf("- %s = [%d] %d bytes\n", k, v.HTTPCode, v.HTTPLength)
    }
}
}
```

This is the output from running the program:

```
$ go run .
- https://notfound.example.com/ = error: Get "https://notfound.example.com/": dial tcp:
  lookup notfound.example.com: no such host
- https://openfaas.com/ = [200] 32696 bytes
- https://inlets.dev/ = [200] 69805 bytes
```

Did you know? The sync.Mutex makes an exclusive lock on the object, meaning that no other reads or writes are possible until the lock is released. This can cause a bottleneck if there are both readers and writers of an object.

The sync.RWMutex type can be used as a drop-in replacement for sync.Mutex, where an arbituary number of readers can obtain a lock or a single writer.

```
package main

import (
    "sync"
)

func main() {
    lock := sync.RWMutex{}
    go readOperation(data, "key", &lock)
    go writeOperation(data, "key", "value", &lock)

    // Add synchronisation for the two routines here.
}

func readOperation(data map[string]string, key string, lock *sync.RWMutex) {
    lock.RLock()
    defer lock.RUnlock()
    fmt.Println(data["key"])
}

func writeOperation(data map[string]string, key, value string, lock *sync.RWMutex) {
    lock.Lock()
    defer lock.Unlock()
    data[key] = value
}
```

In this case, the read and write operations can happen at the same time, because the write lock will not block the function which reads the value.

What’s a real-world use-case for this pattern? Perhaps you have an in-memory cache holding a list of active customers. The list needs to be downloaded over the network, which can be an expensive operation. The list is then shared with a number of Goroutines or handlers in your HTTP server. The read lock would be obtained for accessing the data, and the write lock would be used by something like a timer or a long-running loop that updates items within the cache.

The second approach would be for the Goroutines to simply output data, without sharing a type. The calling code can then aggregate the results, without needing to create a separate type with a lock. You’ll see an example of this in the