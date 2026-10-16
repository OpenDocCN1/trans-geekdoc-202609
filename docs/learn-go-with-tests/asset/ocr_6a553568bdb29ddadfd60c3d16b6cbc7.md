```
```go
func main() {
    fmt.Println(10.0 / 0.0) // fails to compile
}
```
```

Obviously the compiler can't always predict that you'll divide by zero, such as our t.Second()

# Try this

```
```go
func main() {
    fmt.Println(10.0 / zero())
}

func zero() float64 {
    return 0.0
}
```
```

It will print +Inf (infinity). Dividing by +Inf seems to result in zero and we can see this with the following:

```
```go
package main

import (
    "fmt"
    "math"
)

func main() {
    fmt.Println(secondsinradians())
}

func zero() float64 {
    return 0.0
}

func secondsinradians() float64 {
    return (math.Pi / (30 / (float64(zero()))))
}
```
```