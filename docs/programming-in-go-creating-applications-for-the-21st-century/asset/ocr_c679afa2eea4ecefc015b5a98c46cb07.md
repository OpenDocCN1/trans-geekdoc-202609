# Chapter 2. Booleans and Numbers

operations. We won't list all the functions and methods provided by the math/big package since they can easily be looked up in the documentation and may have been added since this was written; however, we will look at a representative example to get a flavor of how Ints are.

Using Go's float64 type allows us to accurately compute about 15 decimal digits—which is more than enough for most situations. However, if we want to compute to a large number of decimal places, tens or hundreds of places, as we might want when computing π, no built-in type is sufficient.

In 1706 John Mach developed a formula for calculating π to an arbitrary number of decimal places, and we can adapt this formula in conjunction with the Go standard library's big.Int to compute to any number of decimal places. The pure formula (and the arccos(t) function it relies on, are shown in Figure 2.1. (No understanding of Mach's formula is required to use of the big.Int package included here.) Our implementation of the arccos() function accepts an additional argument to limit the precision of the calculation so that we don't get beyond the number of digits required.

$$\pi = 4 \times (4 \times arccos(5) - arccos(239)) \quad arccos(x) = \frac{1}{x} - \frac{1}{3x^3} + \frac{1}{5x^5} - \frac{1}{7x^7} + \dots$

Figure 2.1 Machin's formula

The entire program is less than 80 lines and is in the file pi_by_digits/pi_by_digits.go; here is its main() function.*

```
func main() {
    places := handleCommandLine(1000)
    scaledPI := fmt.Sprint(pi(places))
    fmt.Printf("%.3s\n", scaledPI[:1])
}
```

The program assumes a default value of 1000 decimal places, although the user can choose any number they like by entering a value on the command line. The handleCommandLine() function (not shown) returns the value it is passed or the number the user entered on the command line (if any, and if it is valid). The π() function returns as a big.Int of value 314159...; we print this to a string, and then print the string on the console properly formatted so that the output appears as, say, 3.14159265358973238462433832795028841971639937510 (here we have used a more 50 digits).

> * The implementation used here is based on http://en.literateprograms.org/Pi_with_Machin's_formula-(Python).