# Chapter 1. An Overview in Five Examples

```
import {
  "bufio"
  "fmt"
  "math"
  "os"
  "runtime"
}
```

The polar2cartesian program imports several packages, some of which have been mentioned in earlier sections, so we will only mention the new ones here. The math package provides mathematical functions for operating on floating-point numbers (§2.3.2, ➤ 64) and the runtime package provides functions that access the program's runtime properties, as which platform the program is running on.

```
type polar struct {
  radius float64
  theta float64
}
```

```
type cartesian struct {
  x float64
  y float64
}
```

In Go a struct is a type that holds (aggregates or embeds) one or more data fields. These fields can be built-in types as here (float64), structs, or interfaces, or any combination of these. (An interface data field is in effect a pointer to an item—of any kind—that satisfies the interface, i.e., that has the methods with interface specifications.)

It seems natural to use the Greek lowercase theta (θ) to represent the polar coordinate's angle, and thanks to Go's use of UTF-8 we are free to do so. This is because Go allows us to use any Unicode letters in our identifiers, not just letters.

Although the two structs have the same data field types they are distinct types and no automatic conversion between them is possible. This supports defensive programming; after all, it wouldn't make sense to simply substitute a cartesian's positional coordinates for polar coordinates. In some cases conversions make sense, in which case we can easily create a conversion method (i.e., a method of one type that returned a value of another type) that made use Go's composite literal syntax to create a value of the target type populated by the fields from the source type. (Numeric data type conversions are covered in Chapter 2; string conversions are covered in Chapter 3.)