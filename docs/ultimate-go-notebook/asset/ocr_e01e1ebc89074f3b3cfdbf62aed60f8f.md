# Listing 10.5

```
var output bytes.Buffer
var in = assembleInputStream()
var find = []byte("elvis")
var repl = []byte("Elvis")

func BenchmarkAlgorithmOne(b *testing.B) {
  for i := 0; i < b.N; i++ {
    output.Reset()
    algOne(in, find, repl, &output)
  }
}

func BenchmarkAlgorithmTwo(b *testing.B) {
  for i := 0; i < b.N; i++ {
    output.Reset()
    algTwo(in, find, repl, &output)
  }
}
```

With the benchmark functions in place, I can now compare the two algorithms using the test tool. I will add the -benchmem flag so the tool reports allocations.

# Listing 10.6

```
$ go test -bench -benchtime 3s -benchmem

goos: darwin
arch: amd64
pkg: github.com/ardlanas/gotraining/topics/go/profiling/memcppu
cpu: Intel(R) Core (TM) i-9980HK CPU @ 2.40GHz

BenchmarkAlgorithmOne-16    2120113    159 ns/op    53 B/op    2
allocs/op
BenchmarkAlgorithmTwo-16   9103246    387.7 ns/op    0 B/op    0
allocs/op
PASS
ok
```

I see two things in the results. First, Tyler's algorithm is roughly 4 times faster than mine. Second, Tyler wrote a zero allocation and mine is allocating two values on the heap with a total of 52 bytes.

At this point, I want to find and remove those two values allocating on the heap with the hope that maybe my algorithm will be as fast or at least closer to the same performance as Tyler's algorithm. To find these allocations, I need a memory profile.

# 10.4 Memory Profiling

To generate a memory profile I need to add the -memprofile flag to the go test call.