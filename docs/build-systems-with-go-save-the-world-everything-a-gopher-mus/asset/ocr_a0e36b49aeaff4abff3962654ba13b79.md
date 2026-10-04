```
u := User("John",nil)
fmt.Println(u.GetUserId())
// Output:
// JOHN
}
func ExampleUser_CountFriends() {
  u := User("John", nil)
  fmt.Println(u.CountFriends())
  // Output:
  // 0
}
```

# 11.3 BENCHMARKING

Provides benchmarking for those functions starting with the Benchmark prefix. Benchmarks are executed with the go test command when the -bench flag is set. They use the testing.B type instead of testing.T normal tests.

A basic benchmarking is shown in Example 11.7 for a loop computing a sum of numbers. The value of b contains the number of repetitions per operation in performance is being measured. As confirmed from the benchmark output, the benchmark runs three times with b.N values. This is done to ensure the reliability of the benchmark.

Benchmarks are highly configurable using the available go test flags. The benchmark output indicates the number of available goroutines (BenchmarkSum-16), the number of executed iterations (3817), and the nanoseconds elapsed per iteration (265858).

# Example 11.7: Function benchmarking.

```
package example_01

import (
  "fmt"
  "testing"
)

func Sum(n int64) int64 {
  var result int64 = 0
  for i := 0; i<n; i++ {
    result = result + i
  }
  return result
}

func BenchmarkSum(b *testing.B) {
  fmt.Printf("b.N: %d\n", b.N)
  for i:=0; i<b.N; i++ {
    Sum(1000000)
  }
}
```