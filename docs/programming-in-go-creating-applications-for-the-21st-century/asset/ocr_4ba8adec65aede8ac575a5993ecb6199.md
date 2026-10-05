# 3.5. String Formatting with the Fmt Package

string without error checking (use the strconv packages for proper conversions;
 114–115), since they only output spaces between nonstring values. The latter are better for printing multiple values, since they output a space between each value and a newline at the end.

Under the hood these functions use the %w (general value) format specifier—and they can print any built-in or custom value without formatting. For example, the print functions know nothing about the custom polar type but still manage to print a polar value successfully.

In Chapter 6 we will see how to provide a String() method for custom types; this allows us to output however we like. If we want to exercise finely control over the printing of built-in types we can use the print functions that accept a format string as their first argument.

The format string used by the fmt.Error(), fmt.Printf(), fmt.Fprintf(), and fmt.Sprintf() functions consists of one or more modifiers—these are format modifiers of the %wl, where M stands for one or more optional modifiers and L stands for a particular verb letter. The verbs are listed in Table 3.4 (95 \). Some of the verbs can accept one or more modifiers; the modifiers are listed in Table 3.5 (96 \).

We will now review representative examples of format strings so that we get a clear understanding of how they work. In each case we will show a tiny code snippet and then the output it produces.

# 3.5.1. Formatting Booleans

Boolean values are output using the %t (true value) verb.

```
fmt.Printf("%t %t\n", true, false)
true false
```

If we want to output Booleans as integers we must do the conversionourselves:

```
fmt.Printf("%d %d\n", IntBool(true), IntBool(false))
1 0
```

This makes use of a tiny custom function.

```
func IntBool(b bool) int {
  if b {
```

> * C, C++, and Python 2 programmers will find Go's format strings familiar—but with some subtle differences. For example, Go's %d can be used for any integer regardless of its size or signedness.