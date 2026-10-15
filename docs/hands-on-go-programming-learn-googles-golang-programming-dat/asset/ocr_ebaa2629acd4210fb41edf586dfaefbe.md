```
```go
val, ok := <-ch
if !ok {
    break
}
fmt.Println(val)
}
}
}
```
```

The following will be the output for the above program:

```
```
0
1
2
3
4
5
6
7
8
9
```
```

*Program 11.11* can be refactored and the reading code can be minimized:

# Program 11.12

```
```go
package main

import "fmt"
```
```