# # 25. YOU HAVE MY PERMISSION

```
package main

import (
	"fmt"
)

const (
	Read = 1 << iota
	Write
	Execute
)

func main() {
	fmt.Println(Execute)
}
```

Try to guess what the output is before moving to the next page.