# Listing 8.9

| BenchmarkSprint-16 | 56956252 | 55.48 ns | 5 B/op | 1 allocs/op |
| Benchmarkf-16 | 80984947 | 42.46 ns | 5 B/op | 1 allocs/op |

BenchmarkSprint-16 Name of the benchmark function and the number of threads which was 16.

56956252 The number of iterations of the loop that were executed which was 56,956,252.

55.48 ns/op The amount of time code inside the loop to execute which was 55.48 nanoseconds.

5 B/op The amount of memory the code inside the loop allocated which was 5 bytes.

1 allocs/op The number of values the code inside the loop allocated which was 1 value.

In the end, use of Sprintf was faster than Sprint for the string hello, though the both allocated the same number of values and total amount of memory on the heap.

# 8.2 Basic Sub-Benchmarks

There are times I might want to go a set of benchmarks together under a single benchmark function. I might have a data table that I want to control which data is being benchmarked on the command line. If I fall into any of these cases, the sub-benchmarking support in Go is what I need.

# Listing 8.10

```
package basic

import (
	"fmt"
	"testing"
)

var gs string

func BenchmarkSprint(b *testing.B) {
	b.Run("none", benchSprint)
	b.Run("format", benchSprint)
}
```

A quick way to show this is to rename the existing benchmark functions to benchSprint and benchf, then write a single benchmark function that uses the b.Run function.

Now on the command line I can control runs.