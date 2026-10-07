# Listing 10.17

```
func algOne() {
    // Before inlining
    input := bytes.NewBuffer(data)    <-- Original Call
    // After inlining
    input := &bytes.Buffer(buf: data)    <-- After Inlining Optimization
}
```

I can see that after the inlining optimization, the algOne function becomes the owner of the construction of the Buffer value, not the NewBuffer function. Therefore, the value doesn't need to escape to the heap unless the value still needs to exist after the algOne function returns.

It's important to note that Tyler's algorithm is a zero allocation algorithm in part thanks to the same inlining optimization.

# Listing 10.18

```
func algOne() {
    // Before inlining
    input := bytes.NewReader(data)    <-- Original Call
    // After inlining
    input := &bytes.Reader(buf: data)    <-- After Inlining Optimization
}
```

Since the NewReader function is inlined, the construction of the Reader value is owned by Tyler's algorithm. Somehow Tyler is not doing anything in algTwo that is causing the Reader value to escape, where I am doing something in algOne with the Buffer value.

# 10.6 Escape Analysis

How do I know inlining is absolutely happening and I still don't know why algOne is causing allocations where algTwo is zero allocation? Only one tool can tell me the why and that that the compiler. The compiler is making the decision using the escape analysis algorithm.

Luckily, the compiler builds the test binary before anything runs so I can ask the compiler to generate an escape analysis report before running the benchmark.

# Listing 10.19

```
$ go test -bench . -bench 3s -benchmem -memprofile .out -gcflags -m=2
```

I added -gcflags -m=2 as flags on the call to go test. This produces an escape analysis report before running the benchmark.