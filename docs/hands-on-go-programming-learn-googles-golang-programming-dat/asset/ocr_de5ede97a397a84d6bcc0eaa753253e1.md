compilation error. The error says that St does not implement The reason behind this error is that *St implements ltr interface, not

If we re-run the above code by assigning the address of St to the variable the code will work just fine.

When we implement an interface by a value receiver, we can assign both the value and address of the type to the interface. Let us see this in the following code:

# Program 9.8

```
package main
import "fmt"

type ltr interface {
m1()
m2()
}
type St struct {
}

func (s St) m1() {
fmt.Println("In m1 of St")
}
func (s St) m2() {
fmt.Println("In m2 of St")
}
func main() {
var i ltr
fmt.Println("Assigning value of St")
i = St{}
```