If you'll first assign 22 & 7.0 to variables and try the same code, it will fail.
The following won't compile:

Listing 2. pi_var.go

```
package main

import (
	"fmt"
)

func main() {
	a, b := 22, 7.0
	var π = a / b
	fmt.Println(π)
}
```