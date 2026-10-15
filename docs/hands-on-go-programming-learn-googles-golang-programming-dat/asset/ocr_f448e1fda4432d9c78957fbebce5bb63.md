The previous statement reads the value from the channel and stores it to variable

Let’s put it all together. We will write a program that will define a channel, a goroutine will write a value to the channel, and the main method will read the value from the channel.

# Program 11.7

```
```go
package main

import (
"fmt"
)

func main() {
ch := make(chan int, 0)
go writeVal(ch)
a := <-ch
fmt.Println(a)
}

func writeVal(ch chan int) {
ch <- 10
}
```
```

The following will be the output for the above program:

10