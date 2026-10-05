66

Chapter 2. Booleans and Numbers

# Table 2.9 The Math Package's Constants and Functions #2

| Syntax | Description/result |
|---|---|
| math.Floor(x) | [x], i.e., the largest integer less than or equal to x; e.g., math.Floor(5.4) == 5.0 |
| math.Frexp(x) | frac of type float64 and exp of type int such that x = frac * 2^exp; the inverse function is math.Ldexp() |
| math.Gamma(x) | Γ(x), (x - 1)! |
| math.Hypot(x, y) | math.Sqrt(x * x, y * y) |
| math.log1(x) | The binary exponent of x as an int; see also math.Logb() |
| math.Inf(n) | A float64 value of +∞ if n of type int is ≥ 0; otherwise -∞ |
| math.IsInf(x, n) | true if x of type float64 and n of type int is > 0, or x is infinity and n < 0, or if x is either infinity and n is 0; otherwise false |
| math.isNaN(x) | true if x is the IEEE-754 “not a number” value |
| math.J0(x) | J₀(x), the Bessel function of the first kind |
| math.J1(x) | J₁(x), the Bessel function of the first kind |
| math.Jn(n, x) | Jₙ(x), the order-n (where n is of type int) Bessel function of the first kind |
| math.Ldexp(x, n) | x * 2^n where x is of type float64 and n is of type int; the inverse function is math.Frexp() |
| math.Gamma(x) | log(Γ(x)) as a float64 and the sign of Γ(x) as an int (-1 or1) |
| math.Ln2(x) | log₂(x), approximately 0.69314718055945 |
| math.Ln10(x) | log₁₀(x), approximately 2.30258509299404 |
| math.Log(x) | log(x) |
| math.Log2E(x) | log₂(x), approximately 1.44269502169333 |
| math.Log10(x) | log₁₀(x) |
| math.Log10E(x) | log₁₀(x), approximately 0.434294492006301 |
| math.Log1p(x) | log(1+x) is more accurate than using math.Log() when x is near zero |
| math.Log2(x) | log₂(x) |
| math.Logb(x) | The binary exponent of x; see also math.Iogb() |
| math.Max(x, y) | The larger of x and y |
| math.Min(x, y) | The smaller of x and y |
| math.Mod(x, y) | The remainder of x/y; see also math.Remainder()