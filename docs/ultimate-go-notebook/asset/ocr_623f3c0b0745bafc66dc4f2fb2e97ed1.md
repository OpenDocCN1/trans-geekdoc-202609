# Listing 12.11

```
$ go build -race
$ ./trace > t.out
=====================
WARNING: DATA RACE
Read at 0x00c00157548 by goroutine 21:
main.freq.func()
/Users/bill/code/src/github.com/ardlanabs/gotraining/gotraining/topics/go/
profiling/trace/trace.go:103 +0x644

Previous write at 0x00c00157548 by goroutine 66:
main.freq.func()
/Users/bill/code/src/github.com/ardlanabs/gotraining/gotraining/topics/go/
profiling/trace/trace.go:103 +0x65d
```

Looks like I have a data race. The first two lines in the output says there is a read and a previous write to the same memory location on the same line of code inside the literal function. What code is on line 103?

# Listing 12.12

```
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

To fix this race I need to change the increment of the found variable to use an atomic instruction. Do this do I can use the atomic package.

# Listing 12.12

```
96 for _, item := range d.Channel.Items {
97     if strings.Contains(item.Title, topic) {
98         atomic.AddInt32(&found, 1)         <-- CHANGED
99         continue
100     }
101 
102     if strings.Contains(item.Description, topic) {
103         atomic.AddInt32(&found, 1)         <-- CHANGED
104     }
105 }
```

I have replaced lines 98 and 103 to use the atomic.AddInt32 function. The problem