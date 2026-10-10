
## Exercise 3.4

Following the approach of the Lissajous example in [Section 1.7](#ebook_split_017.html#id-lissajous-server), construct a web server that computes surfaces and writes SVG data to the client. The server must set the `Content-Type` header like this:

[Click here to view code image](#ch03_images.html#id060pro01_r)

```
w.Header().Set("Content-Type", "image/svg+xml")
```

(This step was not required in the Lissajous example because the server uses standard heuristics to recognize common formats like PNG from the first 512 bytes of the response, and generates the proper header.) Allow the client to specify values like height, width, and color as HTTP request parameters.

## 3.3 Complex Numbers

Go provides two sizes of complex numbers, `complex64` and `complex128`, whose components are `float32` and `float64` respectively. The built-in function `complex` creates a complex number from its real and imaginary components, and the built-in `real` and `imag` functions extract those components:

[Click here to view code image](#ch03_images.html#id061pro01_r)

```
var x complex128 = complex(1, 2) // 1+2i
var y complex128 = complex(3, 4) // 3+4i
fmt.Println(x*y)                 // "(-5+10i)"
fmt.Println(real(x*y))           // "-5"
fmt.Println(imag(x*y))           // "10"
```

If a floating-point literal or decimal integer literal is immediately followed by `i`, such as `3.141592i` or `2i`, it becomes an *imaginary literal*, denoting a complex number with a zero real component:

[Click here to view code image](#ch03_images.html#id061pro02_r)

```
fmt.Println(1i * 1i) // "(-1+0i)", i² = -1
```

Under the rules for constant arithmetic, complex constants can be added to other numeric constants (integer or floating point, real or imaginary), allowing us to write complex numbers naturally, like `1+2i` or, equivalently, `2i+1`. The declarations of `x` and `y` above can be simplified:

```
x := 1 + 2i
y := 3 + 4i
```

Complex numbers may be compared for equality with `==` and `!=`. Two complex numbers are equal if their real parts are equal and their imaginary parts are equal.

The `math/cmplx` package provides library functions for working with complex numbers, such as the complex square root and exponentiation functions.

[Click here to view code image](#ch03_images.html#id061pro03_r)

```
fmt.Println(cmplx.Sqrt(-1)) // "(0+1i)"
```

The following program uses `complex128` arithmetic to generate a Mandelbrot set.

[Click here to view code image](#ch03_images.html#id061pro04_r)

gopl.io/ch3/mandelbrot

```
// Mandelbrot emits a PNG image of the Mandelbrot fractal.
package main

import (
    "image"
    "image/color"
    "image/png"
    "math/cmplx"
    "os"
)

func main() {
    const (
        xmin, ymin, xmax, ymax = -2, -2, +2, +2
        width, height          = 1024, 1024
    )

    img := image.NewRGBA(image.Rect(0, 0, width, height))
    for py := 0; py < height; py++ {
        y := float64(py)/height*(ymax-ymin) + ymin
        for px := 0; px < width; px++ {
            x := float64(px)/width*(xmax-xmin) + xmin
            z := complex(x, y)
            // Image point (px, py) represents complex value z.
            img.Set(px, py, mandelbrot(z))
        }
    }
    png.Encode(os.Stdout, img) // NOTE: ignoring errors
}

func mandelbrot(z complex128) color.Color {
    const iterations = 200
    const contrast = 15

    var v complex128
    for n := uint8(0); n < iterations; n++ {
        v = v*v + z
        if cmplx.Abs(v) > 2 {
            return color.Gray{255 - contrast*n}
        }
    }
    return color.Black
}
```

The two nested loops iterate over each point in a 1024×1024 grayscale raster image representing the −2 to +2 portion of the complex plane. The program tests whether repeatedly squaring and adding the number that point represents eventually “escapes” the circle of radius 2. If so, the point is shaded by the number of iterations it took to escape. If not, the value belongs to the Mandelbrot set, and the point remains black. Finally, the program writes to its standard output the PNG-encoded image of the iconic fractal, shown in [Figure 3.3](#ebook_split_030.html#id-figures-mandelbrot).

### Exercise 3.5

Implement a full-color Mandelbrot set using the function `image.NewRGBA` and the type `color.RGBA` or `color.YCbCr`.

### Exercise 3.6

Supersampling is a technique to reduce the effect of pixelation by computing the color value at several points within each pixel and taking the average. The simplest method is to divide each pixel into four “subpixels.” Implement it.

### Exercise 3.7

Another simple fractal uses Newton’s method to find complex solutions to a function such as *z*⁴−1 = 0. Shade each starting point by the number of iterations required to get close to one of the four roots. Color each point by the root it approaches.

![The Mandelbrot set.](graphics/mandelbrot.png)

**Figure 3.3.** The Mandelbrot set.

### Exercise 3.8

Rendering fractals at high zoom levels demands great arithmetic precision. Implement the same fractal using four different representations of numbers: `complex64`, `complex128`, `big.Float`, and `big.Rat`. (The latter two types are found in the `math/big` package. `Float` uses arbitrary but bounded-precision floating-point; `Rat` uses unbounded-precision rational numbers.) How do they compare in performance and memory usage? At what zoom levels do rendering artifacts become visible?

### Exercise 3.9

Write a web server that renders fractals and writes the image data to the client. Allow the client to specify the *x*, *y*, and zoom values as parameters to the HTTP request.

## 3.4 Booleans

A value of type `bool`, or *boolean*, has only two possible values, `true` and `false`. The conditions in `if` and `for` statements are booleans, and comparison operators like `==` and `<` produce a boolean result. The unary operator `!` is logical negation, so `!true` is `false`, or, one might say, `(!true==false)==true`, although as a matter of style, we always simplify redundant boolean expressions like `x==true` to `x`.

Boolean values can be combined with the `&&` (AND) and `||` (OR) operators, which have *short-circuit* behavior: if the answer is already determined by the value of the left operand, the right operand is not evaluated, making it safe to write expressions like this:

```
s != "" && s[0] == 'x'
```

where `s[0]` would panic if applied to an empty string.

Since `&&` has higher precedence than `||` (mnemonic: `&&` is boolean multiplication, `||` is boolean addition), no parentheses are required for conditions of this form:

[Click here to view code image](#ch03_images.html#id064pro01_r)

```
if 'a' <= c && c <= 'z' ||
    'A' <= c && c <= 'Z' ||
    '0' <= c && c <= '9' {
    // ...ASCII letter or digit...
}
```

There is no implicit conversion from a boolean value to a numeric value like 0 or 1, or vice versa. It’s necessary to use an explicit `if`, as in

```
i := 0
if b {
    i = 1
}
```

It might be worth writing a conversion function if this operation were needed often:

[Click here to view code image](#ch03_images.html#id064pro02_r)

```
// btoi returns 1 if b is true and 0 if false.
func btoi(b bool) int {
    if b {
        return 1
    }
    return 0
}
```

The inverse operation is so simple that it doesn’t warrant a function, but for symmetry here it is:

[Click here to view code image](#ch03_images.html#id064pro03_r)

```
// itob reports whether i is non-zero.
func itob(i int) bool { return i != 0 }
```

## 3.5 Strings

A string is an immutable sequence of bytes. Strings may contain arbitrary data, including bytes with value 0, but usually they contain human-readable text. Text strings are conventionally interpreted as UTF-8-encoded sequences of Unicode code points (runes), which we’ll explore in detail very soon.
