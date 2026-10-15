We have defined a channel of int type in the main function. We have called the writeVal function as the goroutine and passed the channel variable to it. In the main function, we are reading the value from the channel, assigning to variable and printing the value of Please note that read value in the main function will be blocked until the wrtieVal function writes in the channel. So, the main function will be waiting for the value to be available on the channel.

Since read and write operations are blocking calls in the above code, if the main function is waiting for the read from the channel and there is no goroutine that exists, the Go runtime will find it as deadlock and the program will panic. This can be seen in Program

# Program 11.8

```
package main

import (
"fmt"
)

func main() {

ch := make(chan int, 0)
a := <-ch
fmt.Println(a)
}
```

The following will be the output for the above program: