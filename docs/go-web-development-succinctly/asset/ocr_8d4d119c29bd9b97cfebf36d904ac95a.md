# Code Listing 44: The Average Function in the Math Package

```
package math

func Average(nums []float64) float64 {
    total := float64(0)
    for _, x := range nums {
        total += x
    }
    return total / float64(len(nums))
}
```

Code Listing 45 shows the main function in main.go that we would normally use to invoke our
Average function.

# Code Listing 45: main.go, in Package Main

```
package main

import (
    "fmt"

    "github.com/marklewin/go-web-succinctly/ch07/testing/math"
)

func main() {
    nums := []float64{1, 2, 3, 4}
    avg := math.Average(nums)
    fmt.Println(avg)
}
```

Next, we can create a function called TestAverage in a file average_test.go, also in
math, in order to test the function.

# Code Listing 46: The Code to Test the Average Function in the Math Package

```
package math

import "testing"

func TestAverage(t *testing.T) {
    var v float64
    v = Average([]float64{1, 2, 3, 4, 5})
    if v != 3.0 {
        t.Error("Expected 3.0, got %v", v)
    }
}
```