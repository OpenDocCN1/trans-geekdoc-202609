```
```go
func main() {
    wg := sync.WaitGroup{}
    workItems := 5
    wg.Add(workItems)

    for i := 1; i <= workItems; i++ {
        go func() {
            defer wg.Done()
            printLater(
                fmt.Sprintf("Hello from %d\n", i),
                time.Millisecond*100)
        }()
    }

    wg.Wait()
}

func printLater(msg string, duration time.Duration) {
    time.Sleep(duration)
    fmt.Printf(msg)
}
```
```

Now run the example:

```
```
$ go run ./
Hello from 6
Hello from 6
Hello from 6
Hello from 6
Hello from 6
```
```

Note that the message reads `Hello from 6` for each of the 5 responses? The loop captured the final value of the i variable and used it for each Goroutine.

To solve the problem, we can either pass the i variable into the Goroutine as a parameter, or capture it within a closure using a new local variable.

Here’s the first approach:

```
```go
for i := 1; i <= workItems; i++ {
    go func(j int) {
        defer wg.Done()
        printLater(
            fmt.Sprintf("Hello from %d\n", j),
            time.Millisecond*100)
    }(i)
}
```
```

Notice the signature for our Goroutine changed as follows:

```
```go
i := 1
go func(j int) {
    fmt.Printf("Value is: %d", j)
}(i)
```
```

In the second approach, we define a new local variable j to capture the value of i: