# Listing 9.35

```
func poolWork[Input any, Result any](
    size int,
    work poolWorkFn[Input, Result],
) chan Input, func() {

    var wg sync.WaitGroup
    wg.Add(size)

    ch := make(chan Input)

    for i := 0; i < size; i++ {
        go func() {
            defer wg.Done()
            for input := range ch {
                result := work(input)
                fmt.Println("pollWork: %v", result)
            }
        }()
    }

    cancel := func() {
        close(ch)
        wg.Wait()
    }

    return ch, cancel
}
```

In the poolWork function, the same generic types are declared to represent the input and return type for the work function. A WaitGroup is constructed to manage the lifecycle of the Goroutines in the pool. Then a channel is constructed of the generic Input type. This channel is used by the Goroutines in the pool to receive the input data for the work function.

The pool of Goroutines are created with each Goroutine waiting in a receive operation using a for-range loop against the channel. Finally, a cancel function is constructed to allow the caller to shut down the pool and wait for all the Goroutines to signal they have terminated.

To test the use of the poolWork function, I built a second small program.