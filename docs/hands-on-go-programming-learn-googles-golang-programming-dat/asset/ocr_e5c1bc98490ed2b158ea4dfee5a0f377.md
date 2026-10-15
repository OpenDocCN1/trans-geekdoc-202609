# 10.2 Pointer type

Till now, we have created a pointer variable using := and the type of variable was inferred as We can print the type of variable using the reflect package as shown below:

# Program 10.5

```
package main

import (
"fmt"
"reflect"
)

func main() {
 x := 15
 a := &x
 fmt.Println(reflect.TypeOf(a))
}
```

The following will be the output for the above program:

*int

It is also an important point to note that the address of type T can only be assigned to type Violating this rule gives a