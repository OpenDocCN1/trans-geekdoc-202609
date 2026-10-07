# Listing 8.19

```
package main

import (
    "math"
    "runtime"
    "sync"
    "testing"
)

var n []int

func init() {
    for i := 0; i < 1_000_000; i++ {
        n = append(n, i)
    }
}

func BenchmarkSingle(b *testing.B) {
    for i := 0; i < b.N; i++ {
        single(n)
    }
}

func BenchmarkUnlimited(b *testing.B) {
    for i := 0; i < b.N; i++ {
        unlimited(n)
    }
}

func BenchmarkNumCPU(b *testing.B) {
    for i := 0; i < b.N; i++ {
        numCPU(n, 0)
    }
}
```

Everything I suggests that numCPU should be the fastest since it is efficiently using the cpu capacity of the machine.

# Listing 8.20

```
$ go test -bench -benchtime 3s

goos: darwin
gearch: amd64
pkg: github.com/ardanlans/gotraining/topics/go/testing/benchmarks/validate
cpu: Intel(R) (TM) 19-9980HK CPU @ 2.40GHz
```

| BenchmarkSingle-16 | 52 | 66837183 ns/op |
| BenchmarkUnlimited-16 | 13 | 251840589 ns/op |
| BenchmarkNumCPU-16 | 78 | 46336693 ns/op |

The results of the benchmark show that my expectation was correct, numCPU is faster and in this case by 36.2%. But this is actually correct? What happens if I just run the numCPU benchmark in isolation?