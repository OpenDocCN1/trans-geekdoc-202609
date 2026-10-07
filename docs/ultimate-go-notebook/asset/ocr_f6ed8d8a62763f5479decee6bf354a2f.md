# Listing 4.33

```
type printer interface {
    print()
}
type canon struct {
    name string
}
func (c canon) print() {
    fmt.Printf("Printer Name: %s\n", c.name)
}
type epson struct {
    name string
}
func (e epson) print() {
    fmt.Printf("Printer Name: %s\n", e.name)
}
func main() {
    c := canon("PIXMA TR4520")
    e := epson("WorkForce WF-3720")

    printers := []printer{
        c,
        &e,
    }
    c.name = "PROGRAF PRO-1000"
    e.name = "Home XP-4100"

    for _, p := range printers {
        p.print()
    }
}
```

Output:
Printer Name: PIXMA TR4520
Printer Name: Home XP-4100

The code shows how a choice of semantics of the interface printer allows me to create a collection of different concrete printer types. Iterating over the collection and leveraging polymorphism since the call to p.print changes its behavior depending on the concrete value the code is operating on.

The example also shows how the choice of data semantics changes the behavior of the program. When storing the data using value semantics, the change to the original value is not seen. This is because a copy is stored inside the interface. When pointer semantics are used, any changes to the original value are seen.

# 4.13 Embedding

This example does not show embedding, just the declaration of two types working together as a field from one type to the other.