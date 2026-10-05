# 116

# Chapter 3. Strings

All the strconv conversion functions return the converted value and an error, with the latter nil if the conversion succeeded.

```
x, err := strconv.ParseFloat("-99.7", 64)
fmt.Printf("%v %v\n", x, err)
yy, err := strconv.ParseInt("71309", 10, 0)
fmt.Printf("%v %v\n", y, err)
z, err := strconv.Atoi("71309")
fmt.Printf("%v %v\n", z, err)
```

+   -float64--99.7 <nil>
-int64--71309 <nil>
-int64--nil>

The strconv.ParseFloat(s), strconv.ParseInt(), and strconv.Atoi(ASCII to int") functions show work here as much as we expect. The strconv Atoi(s) is almost as strconv base-10 integer and return an integer, only Atoi(int) returns an int and ParseInt(int) returns an int64. As we would, the strconv.ParseInt() function converts to an unsigned integer type and will fail if there is a leading minus sign in the string it is. These functions will fail if there is any leading or trailing whitespace, but we can easily eliminate this with the strings.TrimSpace() function or by using the fmt package's scan functions (Table 8.2). Normally, the floating-point conversions will accept strings that use standard or exponential notation, as "984", "424.019", and "3.916e-12".

```
s := strconv.FormatBool(z > 100)
fmt.Println(s)
i, err := strconv.ParseInt("0xDEED", 0, 32)
fmt.Println(i, err)
j, err := strconv.ParseInt("0707", 0, 32)
fmt.Println(j, err)
k, err := strconv.ParseInt("10111010001", 0, 32)
```

```
true
50769 <nil>
455 <nil>
1489 <nil>
```

The strconv.FormatBool() function returns a string representing the Boolean expression it is given as "true" or "false". The strconv.ParseInt() function converts an integer in string form into an int64. The second argument is the base to use, with 0 meaning the base be used by the string's prefix: "0x" or "0" for hexadecimal, "0" for octal and decimal otherwise. In this snippet we have converted a hexadecimal and an octal number using their implied base and a binary number by specifying an explicit base of 2. Valid bases are 2 to 36 inclusive with bases