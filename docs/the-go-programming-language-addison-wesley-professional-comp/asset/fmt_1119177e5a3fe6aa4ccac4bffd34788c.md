
It would be straightforward to copy the elements with explicit loops, but it’s easier to use the built-in function `copy`, which copies elements from one slice to another of the same type. Its first argument is the destination and its second is the source, resembling the order of operands in an assignment like `dst = src`. The slices may refer to the same underlying array; they may even overlap. Although we don’t use it here, `copy` returns the number of elements actually copied, which is the smaller of the two slice lengths, so there is no danger of running off the end or overwriting something out of range.

For efficiency, the new array is usually somewhat larger than the minimum needed to hold `x` and `y`. Expanding the array by doubling its size at each expansion avoids an excessive number of allocations and ensures that appending a single element takes constant time on average. This program demonstrates the effect:

[Click here to view code image](#part0134_split_018.html#id089pro01_r)

```
func main() {
    var x, y []int
    for i := 0; i < 10; i++ {
        y = appendInt(x, i)
        fmt.Printf("%d  cap=%d\t%v\n", i, cap(y), y)
        x = y
    }
}
```

Each change in capacity indicates an allocation and a copy:

```
0  cap=1   [0]
1  cap=2   [0 1]
2  cap=4   [0 1 2]
3  cap=4   [0 1 2 3]
4  cap=8   [0 1 2 3 4]
5  cap=8   [0 1 2 3 4 5]
6  cap=8   [0 1 2 3 4 5 6]
7  cap=8   [0 1 2 3 4 5 6 7]
8  cap=16  [0 1 2 3 4 5 6 7 8]
9  cap=16  [0 1 2 3 4 5 6 7 8 9]
```

Let’s take a closer look at the `i=3` iteration. The slice `x` contains the three elements `[0 1 2]` but has capacity `4`, so there is a single element of slack at the end, and `appendInt` of the element `3` may proceed without reallocating. The resulting slice `y` has length and capacity `4`, and has the same underlying array as the original slice `x`, as [Figure 4.2](#part0037.html#id-figures-append-nogrow) shows.

![Appending with room to grow.](images/00018.jpeg)

**Figure 4.2.** Appending with room to grow.

On the next iteration, `i=4`, there is no slack at all, so `appendInt` allocates a new array of size 8, copies the four elements `[0 1 2 3]` of `x`, and appends `4`, the value of `i`. The resulting slice `y` has a length of 5 but a capacity of 8; the slack of 3 will save the next three iterations from the need to reallocate. The slices `y` and `x` are views of different arrays. This operation is depicted in [Figure 4.3](#part0037.html#id-figures-append-grow).

![Appending without room to grow.](images/00019.jpeg)

**Figure 4.3.** Appending without room to grow.

The built-in `append` function may use a more sophisticated growth strategy than `appendInt`’s simplistic one. Usually we don’t know whether a given call to `append` will cause a reallocation, so we can’t assume that the original slice refers to the same array as the resulting slice, nor that it refers to a different one. Similarly, we must not assume that assignments to elements of the old slice will (or will not) be reflected in the new slice. Consequently, it’s usual to assign the result of a call to `append` to the same slice variable whose value we passed to `append`:

```
runes = append(runes, r)
```

Updating the slice variable is required not just when calling `append`, but for any function that may change the length or capacity of a slice or make it refer to a different underlying array. To use slices correctly, it’s important to bear in mind that although the elements of the underlying array are indirect, the slice’s pointer, length, and capacity are not. To update them requires an assignment like the one above. In this respect, slices are not “pure” reference types but resemble an aggregate type such as this struct:

```
type IntSlice struct {
    ptr      *int
    len, cap int
}
```

Our `appendInt` function adds a single element to a slice, but the built-in `append` lets us add more than one new element, or even a whole slice of them.

[Click here to view code image](#part0134_split_019.html#id091pro01_r)

```
var x []int
x = append(x, 1)
x = append(x, 2, 3)
x = append(x, 4, 5, 6)
x = append(x, x...) // append the slice x
fmt.Println(x)      // "[1 2 3 4 5 6 1 2 3 4 5 6]"
```

With the small modification shown below, we can match the behavior of the built-in `append`. The ellipsis “`...`” in the declaration of `appendInt` makes the function *variadic*: it accepts any number of final arguments. The corresponding ellipsis in the call above to `append` shows how to supply a list of arguments from a slice. We’ll explain this mechanism in detail in [Section 5.7](#part0049.html#id-variadicfunctions).

[Click here to view code image](#part0134_split_020.html#id091pro02_r)

```
func appendInt(x []int, y ...int) []int {
    var z []int
    zlen := len(x) + len(y)
    // ...expand z to at least zlen...
    copy(z[len(x):], y)
    return z
}
```

The logic to expand `z`’s underlying array remains unchanged and is not shown.

### 4.2.2 In-Place Slice Techniques

Let’s see more examples of functions that, like `rotate` and `reverse`, modify the elements of a slice in place. Given a list of strings, the `nonempty` function returns the non-empty ones:

[Click here to view code image](#part0134_split_021.html#id091pro03_r)

`gopl.io/ch4/nonempty`

```
// Nonempty is an example of an in-place slice algorithm.
package main

import "fmt"

// nonempty returns a slice holding only the non-empty strings.
// The underlying array is modified during the call.
func nonempty(strings []string) []string {
    i := 0
    for _, s := range strings {
        if s != "" {
            strings[i] = s
            i++
        }
    }
    return strings[:i]
}
```

The subtle part is that the input slice and the output slice share the same underlying array. This avoids the need to allocate another array, though of course the contents of `data` are partly overwritten, as evidenced by the second print statement:

[Click here to view code image](#part0134_split_022.html#id092pro01_r)

```
data := []string{"one", "", "three"}
fmt.Printf("%q\n", nonempty(data)) // `["one" "three"]`
fmt.Printf("%q\n", data)           // `["one" "three" "three"]`
```

Thus we would usually write: `data = nonempty(data)`.

The `nonempty` function can also be written using `append`:

[Click here to view code image](#part0134_split_023.html#id092pro02_r)

```
func nonempty2(strings []string) []string {
    out := strings[:0] // zero-length slice of original
    for _, s := range strings {
        if s != "" {
            out = append(out, s)
        }
    }
    return out
}
```

Whichever variant we use, reusing an array in this way requires that at most one output value is produced for each input value, which is true of many algorithms that filter out elements of a sequence or combine adjacent ones. Such intricate slice usage is the exception, not the rule, but it can be clear, efficient, and useful on occasion.

A slice can be used to implement a stack. Given an initially empty slice `stack`, we can push a new value onto the end of the slice with `append`:

[Click here to view code image](#part0134_split_024.html#id092pro03_r)

```
stack = append(stack, v) // push v
```

The top of the stack is the last element:

[Click here to view code image](#part0134_split_025.html#id092pro04_r)

```
top := stack[len(stack)-1] // top of stack
```

and shrinking the stack by popping that element is

[Click here to view code image](#part0134_split_026.html#id092pro05_r)

```
stack = stack[:len(stack)-1] // pop
```

To remove an element from the middle of a slice, preserving the order of the remaining elements, use `copy` to slide the higher-numbered elements down by one to fill the gap:

[Click here to view code image](#part0134_split_027.html#id093pro01_r)

```
func remove(slice []int, i int) []int {
    copy(slice[i:], slice[i+1:])
    return slice[:len(slice)-1]
}

func main() {
    s := []int{5, 6, 7, 8, 9}
    fmt.Println(remove(s, 2)) // "[5 6 8 9]"
}
```
