# # Sync

[You can find all the code for this chapter here](#)

We want to make a counter which is safe to use concurrently.

We'll start with an unsafe counter and verify its behaviour works in a single-threaded environment.

Then we'll exercise it's unsafeness with multiple goroutines trying to use it via a test and fix it.

# ## Write the test first

We want our API to give us a method to increment the counter and then retrieve its value.

```
```go
func TestCounter(t *testing.T) {
    t.Run("incrementing the counter 3 times leaves it at 3", func(t *testing.T) {
        counter := Counter{}
        counter.Inc()
        counter.Inc()
        counter.Inc()

        if counter.Value() != 3 {
            t.Errorf("got %d, want %d", counter.Value(), 3)
        }
    })
}
```
```

# ## Try to run the test

```
```text
./sync_test.go:9:14: undefined: Counter
```
```