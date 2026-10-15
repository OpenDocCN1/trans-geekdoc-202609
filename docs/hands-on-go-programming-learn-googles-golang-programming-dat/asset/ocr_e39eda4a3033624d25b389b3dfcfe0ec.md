```
package main

import "fmt"

func main() {
rect := rectangle{12.3, 21.45}
p := &rect
p.increaseLength(3.4)
fmt.Println(rect)
}
type rectangle struct {
length float32

width float32
}
func (r *rectangle) increaseLength(a float32) {
r.length = r.length + a
}
```

The following will be the output for the above program:

**{15.7 21.45}**

When you run this program, it will print the updated value, for length. The most important point to note here is that the increaseLength method is called with a pointer to

It is not mandatory to call pointer receiver methods with the pointer variable. You can call these methods with a non-pointer