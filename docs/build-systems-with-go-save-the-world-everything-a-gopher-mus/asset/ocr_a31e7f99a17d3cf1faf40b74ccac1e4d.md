```
time.Sleep(time.Millisecond * 300)
go go writer(x, 3, &)
time.Sleep(time.Second*4)
}
```

The Lock method blocks the thread execution. This means that the longer exclusion area, the longer is the wait. The size of the mutual exclusion area must be small enough to permit the correctness of the execution.

# # 6.9 ATOMIC

The package sync/atomic defines a set of functions for atomic operations. Atomic use low-level atomic primitives outperforming mutexes when used correctly. However, as stated in the Go reference, these functions must be used with care and only for low-level applications. For other applications, the sync package offers better tools (Waitgroup, etc.).

Atomic offers functions for specific native types. See Table 6.1 for a description of the available functions for type int32. Similar functions are available for uint32, int64, and uintptr.

| Function | Description |
|---|---|
| AddInt32(addr *int32, delta int32) (new int32) | Add a delta value |
| CompareAndSwapInt32(addr *int32, old, new int32) (swapped bool) | If value at *addr is equal to old, return true |
| LoadInt32(addr *int32) (val int32) | Safe load |
| StoreInt32(addr *int32, val int32) | Safe store |
| SwapInt32(addr *int32, new int32) (old int32) | Swap value at *addr |

**Table 6.1:** Atomic operations available for the int32 type.

With atomic is similar to work with mutexes, we ensure safe reading and writing operations for shared variables. Example 6.22 shows how two goroutines concurrently modify the shared variable and how this is accessed to. Notice how AddInt32 ensures safe concurrency without the need for a mutual exclusion area. On the other side, to ensure a safe read we use atomic.LoadInt32.

**Example 6.22:** Atomic access to variable.

```
package main
import (
	"fmt"
	"sync/atomic"
	"time"
)
```