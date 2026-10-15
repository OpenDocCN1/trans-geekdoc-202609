We have refactored the We have read the value and ok in the initialization section of We are checking the value of the ok variable in the condition section, and reading the value and ok in the postcondition again.

The second way is using the range clause. This is the best way because we don’t need a condition and when the channel is closed and all the values of the channel are read, the range cause ends automatically:

# Program 11.13

```
package main

import "fmt"

func main() {

ch := make(chan int)

go func() {
for i := 0; i < 10; i++ {
ch <- i
}
close(ch)
}()

for val := range ch {
fmt.Println(val)

}
}
```