counter by 1. You can then monitor the counter, and when it equals zero you know that all your background goroutines have finished.

Let’s take a quick look at a standalone example of how `sync.WaitGroup` works in practice.

In the code below, we’ll launch five goroutines that print out "hello from a goroutine", and use `sync.WaitGroup` to wait for them all to complete before the program exits.

```
```go
package main

import (
    "fmt"
    "sync"
)

func main() {
    // Declare a new WaitGroup.
    var wg sync.WaitGroup

    // Execute a loop 5 times.
    for i := 1; i <= 5; i++ {
        // Increment the WaitGroup counter by 1, BEFORE we launch the
        // background routine.
        wg.Add(1)

        // Launch the background goroutine.
        go func() {
            // Defer a call to wg.Done() to indicate that the background
            // goroutine has
            // completed when this function returns. Behind the scenes this
            // decrements
            // the WaitGroup counter by 1 and is the same as writing
            wg.Add(-1).
```
```