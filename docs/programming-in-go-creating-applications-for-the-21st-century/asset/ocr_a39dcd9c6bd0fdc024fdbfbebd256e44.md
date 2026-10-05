# 2.3. Numeric Types

Table 2.11 The Complex Math Package's Functions

Import "math/cmpx". All the functions accept and return complex12s unless specified otherwise.

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
| cmplx.Inf() | complex(math.Inf(1), math.Inf(1)) |
| cmplx.IsInf(x) | true if real(x) or imag(x) is $\pm\infty$; otherwise false |
| cmplx.isnan(x) | true if real(x) or imag(x) is “not a number” and if neither false |
| cmplx.Log(x) | $\log(x)$ |
| cmplx.Log10(x) | $\log_{10}(x)$ |
| cmplx.NaN() | A complex “not a number” in the range $[-\pi, +\pi]$ |
| cmplx.Phase(x) | The phase of x as a float64 in $[-\pi, +\pi]$ |
| cmplx.Polar(x) | The absolute value $r$ and phase $	heta$ of both type float64, satisfying $x = re^{	heta}$; phase is in the range $[-\pi, +\pi]$ |
| cmplx.Pow(x, y) | A complex128 with polar coordinates $r$ and $	heta$ of both type float64 |
| cmplx.Rect(r, \theta) | |
| cmplx.Sin(x) | The sine of x in radians |
| cmplx.Sinh(x) | The hyperbolic sine of x in radians |
| cmplx.Sqrt(x) | $\sqrt{x}$ |
| cmplx.Tan(x) | The tangent of x in radians |
| cmplx.Tanh(x) | The hyperbolic tangent of x in radians |