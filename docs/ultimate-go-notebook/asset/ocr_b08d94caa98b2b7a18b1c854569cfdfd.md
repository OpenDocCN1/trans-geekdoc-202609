# Listing 2.31

```
const (
    A2 = iota // 0 : Start at 0
    B2        // 1 : Increment by 1
    C2        // 2 : Increment by 1
)
fmt.Println(A2, B2, C2)
```

Output:
0 1 2

I don't need to repeat the use of the iota keyword. The successive nature of the integer constants are assumed once applied.

# Listing 2.32

```
const (
    A3 = iota + 1 // 1 : 0 + 1
    B3            // 2 : 1 + 1
    C3            // 3 : 2 + 1
)
fmt.Println(A3, B3, C3)
```

Output:
1 2 3

If I didn't want to apply a mathematical pattern, I can perform some math and the math is reapplied with an increasing value of iota.

# Listing 2.33

```
const (
    Ldate = 1 << iota // 1 : Shift to the left 0. 0000 0001
    Ltime             // 2 : Shift to the left 1. 0000 0010
    Lmicroseconds      // 4 : Shift to the left 2. 0000 0100
    Llongfile          // 8 : Shift to the left 3. 0000 1000
    Lshortfile         // 16 : Shift to the left 4. 0001 0000
    LUTC               // 32 : Shift to the left 5. 0010 0000
)
fmt.Println(Ldate, Ltime, Lmicroseconds, Llongfile, Lshortfile, LUTC)
```

Output:
1 2 4 8 16 32

I can use this feature like the Log package does for setting flags. In this case, operations are being applied with increasing values of iota to calculate flag values.