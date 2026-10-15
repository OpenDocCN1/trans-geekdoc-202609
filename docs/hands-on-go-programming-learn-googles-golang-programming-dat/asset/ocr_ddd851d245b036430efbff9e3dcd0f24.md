not grouped. Methods are not part of its type declaration. Even methods don’t need to be in the same source file as their type. You can declare methods and their type both in different source files. So, we need a receiver on a method so that the Go compiler can understand which type it is a part of.

The most crucial point to note here is that methods and their type must be declared in the same package. You cannot declare a method in a different package than its type. This is the reason we that we cannot add a method to predefined named types. Example: You cannot add a method to However, there is a workaround for this which we will see in a later section.

# Program 8.1

```
```go
type rectangle struct {
length float32
width float32
}
func (r rectangle) area() float32 {
return r.length * r.width
}
```
```

_Program 8.1_ declares a struct named rectangle with field length and Both length and width are declared as The rectangle struct has a method named as The method is not declared as part of the rectangle body. Instead, it is declared separately. It is considered a method of the rectangle struct because the rectangle is used as the receiver type. The receiver is placed between the func keyword and the method name The receiver is declared with the receiver variable We can access fields of the receiver in a