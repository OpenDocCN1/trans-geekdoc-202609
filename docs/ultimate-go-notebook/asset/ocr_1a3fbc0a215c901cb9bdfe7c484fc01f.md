# Listing 8.17

```
func numCPU(n [int]) [int] {
  ..

  // Calculate how many levels deep we can keep creating goroutines.
  // On an 8 core machine we can keep creating goroutines until level 4.
  // Lvl 0   1 Lists 1 Goroutine
  // Lvl 1   2 Lists 2 Goroutines
  // Lvl 2   4 Lists 4 Goroutines
  // Lvl 3   8 Lists 8 Goroutines
  // Lvl 4   16 Lists 16 Goroutines

  // On an 8 core machine this will produce the value of 3.
  maxLevel := int(math.Log2(float64(runtime.GOMAXPROCS(0))))

  ..
```

Once the number of levels is calculated, the sorting work begins.

# Listing 8.18

```
func numCPU(n [int], lvl int) [int] {
  ..

  // We don't need more goroutines then we have logical processors.
  if lvl <= maxLevel {
    lvl++

    // For each split we will have 2 goroutines.
    var wg sync.WaitGroup
    wg.Add(2)

    // Sort the left side concurrently.
    go func() {
      l = numCPU(n[:i], lvl)
      wg.Done()
    }()

    // Sort the right side concurrently.
    go func() {
      r = numCPU(n[i:], lvl)
      wg.Done()
    }()

    // Wait for the splitting to end.
    wg.Wait()

    // Place things in order and merge ordered lists.
    return merge(l, r)
  }

  // Sort the left and right side on this goroutine.
  l = numCPU(n[:i], lvl)
  r = numCPU(n[i:], lvl)

  // Place things in order and merge ordered lists.
  return merge(l, r)
}
```

With this function complete, I can write the benchmark functions and see what version of merge sort is faster.