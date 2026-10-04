# 4.2.1 Embedded methods

When a struct is embedded into other structs its methods are made available to the second one. This acts as some of inheritance in Go. In Example 4.8, the type box embeds the type Rectangle. Observe how the method value can directly invoke the Surface method from Rectangle to compute the value of the box.

# Example 4.8: Embedded methods.

```
package main

import "fmt"

type Rectangle struct {
    Height int
    Width int
}

func (r *Rectangle) Surface() int {
    return r.Height * r.Width
}

type Box struct {
    Rectangle
    depth int
}

func (b Box) Volume() int {
    return b.Surface() * b.depth
}

func main() {
    b := Box{Rectangle{3,3}}
    fmt.Printf("%v\n", b)
    fmt.Println("Volume", b.Volume())
}
```

> Remember that embedded methods only work if there is no ambiguity in its definition. Consider the following example:

type A struct {}
func (a A) Hi() string {
    return "A says Hi"
}

t B struct {
func (b B) Hi() string {
    return "B says Hi"
}