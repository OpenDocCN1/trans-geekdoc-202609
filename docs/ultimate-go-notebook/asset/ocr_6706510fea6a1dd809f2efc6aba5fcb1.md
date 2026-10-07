Listing 5.15

```
type System struct {
  Xenia
  Pillar
}
```

The initial idea of the System type is to compose a system that knows how to Pull and Store. In this case, composing the ability to Pull and Store from Xenia Pillar.

Listing 5.16

```
func main() {
  sys := System{
    Xenia: Xenia{
      Host: "localhost:8000",
      Timeout: time.Second,
    },
    Pillar: Pillar{
      Host: "localhost:9000",
      Timeout: time.Second,
    }
  }

  if err := Copy(&sys, 3); err != io.EOF {
    fmt.Println(err)
  }
}
```

Finally, the main function can be written to construct a Xenia and Pillar within the composition of a System. Then the System can be passed to the Copy function and data can begin to flow between the two systems.

With all this code, I now have my first draft of a concrete solution to a concrete problem.

# 5.4 Decoupling With Interfaces

The next step is to understand what could change in the program. In this case, what can change is the systems themselves. Today it's Xenia and Pillar, tomorrow it could be Alice and Bob. With this knowledge, I want to decouple the existing concrete solution from this change. To do that, I want to change the concrete functions to be polymorphic functions.