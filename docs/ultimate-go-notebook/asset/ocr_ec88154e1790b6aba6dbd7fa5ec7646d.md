# Listing 12.9

```
func freqConcurrent(topic string, docs []string) int {
    var found int

    g := len(docs)                <-- ADDED
    var wg sync.WaitGroup      <-- ADDED
    wg.Add(g)                   <-- ADDED

    for _, doc := range docs {
        .\.
    }

    wg.Wait()                   <-- ADDED
    return int
}
```

To start, I need to add code that makes the freq function doesn't return until all the work is complete. This is best implemented by using a WaitGroup. I start with identifying which Goroutines need to be created, which is represented by the length of the docs collection. I add that number to the WaitGroup and at the end of the function wait for the WaitGroup to get back down to zero.

# Listing 12.10

```
func freqConcurrent(topic string, docs []string) int {
    var found int

    g := len(docs)
    var wg sync.WaitGroup
    wg.Add(g)

    for _, doc := range docs {
        go func(doc string) {     <-- ADDED
            defer wg.Done()\        <-- ADDED
            .\.\.
        }(doc)                   <-- ADDED
    }

    wg.Wait()
    return int
```

Next, I wrap the existing code inside the range loop around a Goroutine, where each document iterated over is passed into the new Goroutine to prevent any closure bugs. With the Goroutine in place, I finalize the WaitGroup code by making sure each Goroutine calls wg.Done() right before it terminates.

The last thing I need to do is remove the return value of 0 from all the error conditions inside the loop when processing a file. I might think this code is ready since all the orchestration with the WaitGroup is in place, but what happens if I run this code with the race detector?