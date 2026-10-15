method body by applying the dot operator on the receiver variable. We have accessed length and width in the method body by `r.length` and The method calculates the area of the rectangle by multiplying length and area and finally, it returns the result. The return type of the method is

You can give any valid identifier as a receiver name. You can define a receiver name as *this* or *self* like we define in Java or Python respectively, but it is not mandatory. It is also possible to define different receiver names for all methods. It is a good practice to give short and the same names for all receivers. *Program 8.2* declares two methods, area and perimeter, and both the methods have different receiver names, r and rect respectively.

# Program 8.2

```
```go
type rectangle struct {
length float32
width float32
}
func (r rectangle) area() float32 {
return r.length * r.width
}
func (rect rectangle) perimeter() float32 {
return (2 * rect.length) + (2 * rect.width)
}
```
```

The receiver name is not mandatory in the method declaration. You can declare a method by providing receiver type only. If a method does not read or modify any field of the receiver, we can omit the receiver name (though it is not a valid usecase because