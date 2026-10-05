# 4.1. Values, Pointers, and Reference Types

whether directly or inside a function they have been passed to—are visible to all the variables that refer to them.

```
func inflate(numbers []int, factor int) {
  for i := range numbers {
    numbers[i] *= factor
  }
}
```

The grades slice is passed in as the parameter numbers—but unlike we pass values, any changes applied to numbers are reflected in grades since they both refer to the same underlying slice.

Since we want to modify the slice's values in-place we have used a loop counter to access each item. We didn't use a for index, item ... loop that gets a copy of each item from the slice it operates on—would result in the copy being multiplied by the factor each time and then discarded, leaving the original unchanged. We could have used a for loop familiar in other languages (e.g., for i := 0; i < len(numbers); i++), but instead we have used the more convenient for index := range syntax. (All the loop syntaxes are covered in the next chapter; 5.3, 203.3.)

Let's imagine we have a rectangle that stores a rectangle position as its top-left and bottom-right x, y coordinates, and its fill color. We could represent the rectangle's data using a struct.

```
type rectangle struct {
  x0, y0, x1, y1 int
  color.RGBA
}
```

Now we create a value of the rectangle type, print it, resize it, and then print it again.

```
rect := rectangle{4, 8, 20, 10, color.RGBA{0xFF, 0, 0, 0xFF}}
fmt.Println(rect)
resizeRect(&rect, 5, 5)
fmt.Println(rect)
```

```
{4 8 20 10 {255 0 255}}
{4 28 15 25 {255 0 255}}
```

As we noted in the previous chapter, even though our custom rectangle type is it still able to print it in a sensible way. The output shown below the code snippet clearly shows that the custom resizeRect() function correctly did its job. And rather than passing the whole rectangle (at least 16 bytes