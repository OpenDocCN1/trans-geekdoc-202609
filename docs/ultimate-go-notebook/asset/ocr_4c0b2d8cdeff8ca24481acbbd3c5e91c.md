type is respected.

# 9.9 Channels

I wanted to explore how the Go team could add a package of concurrency patterns into the standard library thanks to generics. This would require declaring channels and functions using generic types.

Listing 9.31

```
type workFn[Result any] func(context.Context) Result
```

In this example, I declare a type that represents a function which accepts a context and returns a value of generic type Result. This function declaration describes a function that implements the concurrent work that will be performed and the result of that work.

Listing 9.32

```
func doWork[Result any](ctx context.Context, workFn func[Result]) chan
Result {
	ch := make(chan Result, 1)

	go func() {
		ch <- workFn(ctx)
		fmt.Println("doWork : complete")
	}()

	return ch
}
```

Now I write a function named doWork that executes the specified work function concurrently and returns a channel so the caller can receive the result of the work performed by the work function. A generic type named Result is declared to represent the return type for the work function and the type for the channel.

In the implementation of the doWork function, a buffered channel of one is constructed of generic type Result. That's the channel returned to the caller to receive the result of the concurrent work. In the middle of the function, a goroutine is constructed to execute the work function concurrently. Once the work function returns, the return argument is sent back to the caller through the channel.

To test the use of the doWork function, I built a small program.