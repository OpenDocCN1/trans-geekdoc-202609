```
Listing 6.25
func func() {
  for i := 0; i < 2; i++ {
    value := counter
    value++
    log.Println("logging")
    counter = value
  }
  Wg.Done()
}()
```

I can clearly see the unsynchronized read and write. As a side note, the plus operation on line 39 would be a data race if the code was accessing the counter variable. The plus plus operation is a read, modify, and write operation underneath and the operating system could easily context switch in the middle of that.

So how I fix the code to make sure that I remove the data race? There are two tools, atomic instructions and mutexes.

# 6.7 Atoms

Atomics provide synchronization at the hardware level. Because of this, it's limited to words and half-words of data. They're great for counters or fast switching mechanics. The WaitGroup API'use atomics.

What changes do I need to make to apply atomics to the code?

```
Listing 6.26
var counter int32 <-- CHANGED
func main() {
  const grs = 2
  var wg sync.WaitGroup
  wg.Add(grs)

  for g := 0; g < grs; g++ {
    go func() {
      for i := 0; i < 2; i++ { <-- CHANGED
        atomic.AddInt32(&counter, 1)
      }
      wg.Done()
    }()
  }
  wg.Wait()
  fmt.Println("Counter:", counter)
}
```

I only need to do a couple things. First, change the counter variable to be a precision based integer. I can see at the top of the code listing, the atomic functions only work with precision based integers. Second, remove the manually read, modify, and write code for one call to atomic.AddInt32. That one call handles