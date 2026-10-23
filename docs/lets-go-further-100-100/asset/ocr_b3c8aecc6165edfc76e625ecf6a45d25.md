```
defer wg.Done()

    fmt.Println("hello from a goroutine")
    }()
}

    // Wait() blocks until the WaitGroup counter is zero --- essentially
blocking until all
    // goroutines have completed.
    wg.Wait()

    fmt.Println("all goroutines finished")
}
```

If you run the above code, you’ll see that the output looks like this:

```
hello from a goroutine
hello from a goroutine
hello from a goroutine
hello from a goroutine
hello from a goroutine
all goroutines finished
```

One thing that’s important to emphasize here is that we increment the counter with wg.Add(1) immediately before we launch the background goroutine. If we called wg.Add(1) in the background goroutine itself, there is a race condition because wg.Wait() could potentially be called before the counter is even incremented.