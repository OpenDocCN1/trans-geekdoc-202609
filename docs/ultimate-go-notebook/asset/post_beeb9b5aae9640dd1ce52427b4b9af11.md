
# Figure 12.4

![](img/8be06d78925d0d5a2d2ade851e9bad63_239_0.png)

There are two colors (or shades) that are represented in the heap graph. Orange (the darker shade) represents the amount of memory in-use on the heap at microsecond. Green (the lighter shade) represents when the next GC will be triggered based on when that amount of memory is once again in-use on the heap.

# Figure 12.5

![](img/8be06d78925d0d5a2d2ade851e9bad63_239_1.png)

This is why when the orange area reaches the top of the green area, there is a line in the GC section. Each line represents a GC that took place. BTW, the dot is the selection point for the heap information listed here.

Since the green area is in a consistent straight line for the entire run of the program, I can select any orange point to see the max size of the heap that is 4 meg of memory.

If I want more clarity on this number, I can use GDEBUG and run the program again.

# Listing 12.8

```
$ time GDEBUG=gctrace=1 ./trace > .out

gc 1 @01.06s 0%: 0.020+0.024+0.025 ms clock, 0.32+0.18/0.12+0.39 ms cpu,
4->4o MB, 5 MB goal, 16 P
gc 2 @00.29s 0%: 0.030+0.023+0.002 ms clock, 0.49+0.15/0.17/0.001+0.037 ms cpu, 4->4o MB, 5 MB goal, 16 P
gc 3 @08.04s 0%: 0.033+0.026+0.019 ms clock, 0.52+0.15/0.059+0.31 ms cpu, 4->4o MB, 5 MB goal, 16 P
gc 73 @82.79s 0%: 0.043+0.046+0.040 ms clock, 0.70+0.24/0.18/0.25+0.65 ms cpu, 4->4o MB, 5 MB goal, 16 P
gc 74 @82.80s 0%: 0.043+0.035+0.002 ms clock, 0.69+0.28/0.37+0.16+0.042 ms cpu, 4->4o MB, 5 MB goal, 16 P
gc 75 @82.814s 0%: 0.032+0.028+0.017 ms clock, 0.52+0.20/0.26+0.026+0.28 ms cpu, 4->4o MB, 5 MB goal, 16 P
```

2021/05/12 15:17:24 Searching 4000 files, found presiden 2800 times.

Sure enough, the heap was maintained at 4 meg and all the memory was transient each GC resulted in the number of live values to be zero. Exactly what I am seeing in the trace.

What I really need is more information about the GCCs. It's not about 1 GC, it's all about the GC's that needed to take place. I can get this information by using the selection tool and double clicking on any blue line.

# Figure 12.6

| 275 items selected. | Slices (275) |
| Name | Wall Duration | Self time | Average Wall Duration | Occurrences |
| :--- | :--- | :--- | :--- | :--- |
| GC | 106,639,993 ns | 106,639,993 ns | 387,72 ns | 275 |

- Selection start
  - 15,245,706 ns
- Selection extent
  - 2,647,454,596 ns
- Start
- CPU Duration
- Duration
- CPU Self Time

These numbers are helpful in determining how much the GC is doing in the execution of the program. With these numbers I have a baseline for the program's performance.

## Table 12.1

| | Single |
| :--- | :--- |
| Runtime | 2670ms |
| Top Memory | 4 Meg |
| GC Occurrences | 275 |
| GC Avg Duration | 387us |
| GC Wall Duration | 106ms |
| GC Time Spent | 4% |

With the baseline numbers, I still don't have an answer as to how I could speed up the program. Maybe looking at a larger portion of the graph will help?

Figure 12.7

- Proc 0
- Proc 1
- Proc 2
- Proc 3

![](img/8be06d78925d0d5a2d2ade851e9bad63_241_0.png)

If I look closer at this section of trace, I can see the problem. The program is only using one logical processor at any time to execute application work. The GC however is using more. If I change the algorithm to be concurrent using all the available cores on my machine, this should help with the performance.

## 12.4 Fan-Out

One concurrency pattern I could use is fan-out pattern. This would allow me to have a concurrent algorithm with the least amount of change. The idea of this pattern is to create a Goroutine for each file that needs to be processed and let the scheduler manage all the logical processors. I can fan-out all these Goroutines because the order of work doesn't matter. What matters is all the work performed.

# Listing 12.9

```go
func freqConcurrent(topic string, docs []string) {
    var found int

    g := len(docs)                << ADDED
    var wg sync.WaitGroup      << ADDED
    wg.Add(g)                   << ADDED

    for _, doc := range docs {
        .
    }

    wg.Wait()                   << ADDED
    return int
}
```

To start, I need to add code that makes the freq function doesn't return until all the work is complete. This is best implemented by using WaitGroup. I start with identifying which Goroutines need be created, which is represented by the length of docs. I add that number to the WaitGroup and at the end of function wait for WaitGroup to get back to zero.

# Listing 12.10

```go
func freqConcurrent(topic string, docs []string) int {
    var found int

    g := len(docs)
    var wg sync.WaitGroup
    wg.Add(g)

    for _, doc := range docs {
        go func(doc string) {     << ADDED
            defer wg.Done()        << ADDED
            ..
        }(doc)                   << ADDED
    }

    wg.Wait()
    return int
}
```

Next, I wrap the existing code inside the range loop around a Goroutine, where each document iterated over is passed into the new Goroutine to prevent closure bugs. With the Goroutine in place, I finalize the WaitGroup code by making sure each Goroutine calls wg.Done() right before it terminates. The last thing I need to do is remove the return value of 0 from all the conditions inside the loop when processing a file. I might think this code is ready since all the orchestration with the WaitGroup is in place, but what happens if I run this code with race detector?

# Listing 12.11

```bash
$ go build -race
$ ./trace > t.out
=====================
WARNING: DATA RACE
Read at 0x00c015748 by goroutine 21:
main.freq.func()
/Users/bill/code/src/github.com/ardlanabs/gotraining/topics/go/
profiling/trace.go:103 +0x644

Previous write at 0x00c015748 by goroutine 66:
main.freq.func()
/Users/bill/code/src/github.com/ardlanabs/gotraining/topics/go/
profiling/trace.go:103 +0x65d
```

Looks like I have a data race. The first two lines in the output says there is a read and a previous write to the same memory location on the same line of code inside the literal function. What code is on line 103?

# Listing 12.12

```go
96 for _, item := range d.Channel.Items {
97     if strings.Contains(item.Title, topic) {
98         found++
99         continue
100     }
101 
102     if strings.Contains(item.Description, topic) {
103         found++
104     }
105 }
```

If I add the line numbers to the code, I can see it's related to the increment of the found variable. This code is actually used again on line 98, so both lines of code (98, 103) contain a data race.

To fix this race I need to change the increment of the found variable to use an atomic instruction. Do this I can use the atomic package.

# Listing 12.12

```go
96 for _, item := range d.Channel.Items {
97     if strings.Contains(item.Title, topic) {
98         atomic.AddInt32(&found, 1)         << CHANGED
99         continue
100     }
101 
102     if strings.Contains(item.Description, topic) {
103         atomic.AddInt32(&found, 1)         << CHANGED
104     }
105 }
```

I have replaced lines 98 and 103 to use the atomic.AddInt32 function. The problem is function requires an int32 not an int, so I need to make two more changes.

# Listing 12.13

```go
func freq(topic string, docs []string) int {
    var found int32      << CHANGED

    .
    wg.Wait()
    return int(found)    << CHANGED
}
```

## 12.5 Cache Friendly

The problem is with the found variable. It's technically a global variable to the 4k Goroutines that will be accessing memory. Though using the atomic package helps to serialize access, each core on my machine that is executing Goroutines will receive and operate on its own copy of the found variable. The moment any copy inside of any core is incremented, it will mark all the other copies in all the other cores dirty.

When the next Goroutine goes to increment their copy, and that copy is marked dirty, a fresh copy needs to be pulled from main memory. This will result in the thrashing of memory, slowing everything down. To alleviate the thrashing I need each Goroutine to use a local variable for counting the number of times the term is found. However, before the Goroutine terminates it must add the result of it's local variable to the global variable. For the current algorithm, that means we reduce the thrashing from 28k times to 4k times. Not perfect, but much better.
