Figure 4.1

![](bbox=[0.121, 0.085, 0.878, 0.253])

It has to do with the data semantics at play. The displayName method is using a value receiver so value semantics are at play.

Listing 4.21

```
func (d data) displayName() {
  fmt.Println("My Name Is", d.name)
}
```

This means that the f1 variable maintains and operates against its own copy of d. So calling the method through the f1 variable, will always use the copy and that copy is protected against change. This is what I want with value semantics. Now I will do the same thing but with the setAge method.

Listing 4.22

```
func main() {
  d := data{
    name: "Bill"
  }

f2 := d.setAge
f2(45)
d2.name = "Sammy"
f2(45)
}

Output:
Bill Is Age 45
Sammy Is Age 45
```

This time the setAge method is assigned to the variable f2. Again, the method is executed indirectly through the f2 variable passing 45 for Bill’s age. Then Bill’s name is changed to Sammy and the f2 variable is used again to make the call. This time I see the name has changed.