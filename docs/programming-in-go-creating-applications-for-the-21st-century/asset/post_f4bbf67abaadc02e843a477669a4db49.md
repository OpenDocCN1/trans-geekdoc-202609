
## 2.3. Numeric Types

is passed as the limit. It relies on functions (and a constant) from the standard library's math package.
An alternative (and slower) approach is to compare numbers as strings.

```go
func EqualFloatPrec(x, y float64, decimals int) bool {
    a := fmt.Sprintf("%.*f", decimals, x)
    b := fmt.Sprintf("%.*f", decimals, y)
    return len(a) == len(b) && a == b
}
```

For this accuracy is specified as the number of digits after the decimal point. The fmt.Sprintf()'s % formatting argument can accept a * placeholder where it expects a number, so we create two strings based on two given float64s, formatting each with the specified number of decimal places. The magnitudes of the numbers differ, so will be the lengths of the a and b strings (e.g., 592.85), which gives us a relatively fast short-circuiting equality test. (String formatting is covered in $3.5) ▶ 93.

```go
func IntFromFloat64(x float64) int {
    if math.MinInt32 <= x <= math.MaxInt32 {
        whole, fraction := math.Modf(x)
        if fraction >= 0.5 {
            whole++
        }
        return int(whole)
    }
    panic(fmt.Sprintf("%g is out of the int32 range", x))
}
```

The Go Specification (golang.org/doc/go_spec.html) states that an int occupies the same number of bits as a uint and that a uint is always 32 or 64 bits. This implies that an int is at least 32 bits which means that we can safely use the math.MinInt32 and math.MaxInt32 constants as the int range.

We use the math.Modf() function to separate the whole and fractional parts of the given number (both as float64), and rather than simply returning the whole part (i.e., truncating), we perform a simple rounding if the fractional part is ≥ 0.5.

Rather than return an error as we did for our custom Uint8ToInt() function (58, we have chosen to treat out-of-range values as enough to stop the program, we have used the built-in panic() function which will cause a runtime panic and stop the program unless the panic is caught by a recover() ($55, 212). This means that if the program runs successfully we know that no out-of-range conversions were attempted. (Notice that the function does not end with a return statement; the Go compiler is smart enough to realize that a call to panic() means that a normal return cannot occur at point.)

## 2.3.2.1. Complex Types

The two complex types supported by Go are shown in Table 2.7 (64). Complex numbers can be created using the built-in complex() function or by using constant literals involving imaginary numbers. Complex numbers' components can be retrieved using the built-in real() and imag() functions, both of which return a float64 (or a float32 for complex64).

Complex numbers support all arithmetic operations listed in Table 2.4 (59). The comparison operators that can be used with complex numbers are == and != (see Table 2.3, 57), but these suffer from the same issues as when comparing floating-point numbers. The standard library has a complex number-specific package, math/cmplx, whose functions are listed in Table 2.11.

Here are some simple examples:

```go
f := 3.2e5
x := -7.3 - 8.9i
y := complex(-18.3 + 8.9i)
z := complex(f, 13.2)
fmt.Println(x, real(y), imag(z)) // Prints: (-7.3-8.9i) -18.3 13.2
```

Go signifies imaginary numbers using the i suffix as used in pure mathematics. Here, the numbers x and z are of type complex128, so their real and imaginary parts are of type float64; y is of type complex64 so its components are of type float32. One subtle point to notice is that using the complex64 type performs a type conversion (or any other built-in type conversion). So here (), the complex number-18.3+8.9i (of type complex128—

> * By contrast, in engineering and Python, imaginary numbers are indicated using j.

### Table 2.11 The Complex Math Package's Functions

Import "math/cmplx". All the functions accept and return complex128 unless specified otherwise.

| Syntax | Description/result |
|--- | --- |
| cmplx.Abs(x) | |x|, i.e., the absolute value of x as a float64 |
| cmplx.Acos(x) | The arc cosine of x in radians |
| cmplx.Acosh(x) | The hyperbolic cosine of x in radians |
| cmplx.Asin(x) | The sine of x in radians |
| cmplx.Asinh(x) | The hyperbolic sine of x in radians |
| cmplx.Atan(x) | The tangent of x in radians |
| cmplx.Atanh(x) | The hyperbolic tangent of x in radians |
| cmplx.Conj(x) | The complex conjugate of x |
| cmplx.Cos(x) | The cosine of x in radians |
| cmplx.Cosh(x) | The hyperbolic cosine of x in radians |
| cmplx.Cot(x) | The cotangent of x in radians |
| cmplx.Exp(x) | $e^x$ |
| cmplx.Inf() | $\infty$ |
| cmplx.IsInf(x) | true if real(x) or imag(x) |
| cmplx.isnan(x) | true if real(x) or imag(x) |
| cmplx.Log(x) | $\log(x)$ |
| cmplx.Log10(x) | $\log_{10}(x)$ |
| cmplx.NaN() | “not a number” |
| cmplx.Phase(x) | The phase of x |
| cmplx.Polar(x) | The absolute value of x |
| cmplx.Pow(x, y) | $x^y$ |
| cmplx.Rect(r, y) | Rect coordinates |
| cmplx.Sin(x) | The sine of x in radians |
| cmplx.Sinh(x) | The hyperbolic sine of x in radians |
| cmplx.Sqrt(x) | $\sqrt{x}$ |
| cmplx.Tan(x) | The tangent of x in radians |
| cmplx.Tanh(x) | The hyperbolic tangent of x in radians |
