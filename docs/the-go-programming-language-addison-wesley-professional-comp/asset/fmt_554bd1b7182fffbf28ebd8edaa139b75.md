
### Maps

The `MapKeys` method returns a slice of `reflect.Value`s, one per map key. As usual when iterating over a map, the order is undefined. `MapIndex(key)` returns the value corresponding to `key`. We append the subscript notation `"[key]"` to the path. (We're cutting a corner here. The type of a map key isn't restricted to the types `formatAtom` handles best; arrays, structs, and interfaces can also be valid map keys. Extending this case to print the key in full is [Exercise 12.1](#part0114.html#id-ex-printstruct).)

### Pointers

The `Elem` method returns the variable pointed to by a pointer, again as a `reflect.Value`. This operation would be safe even if the pointer value is `nil`, in which case the result would have kind `Invalid`, but we use `IsNil` to detect nil pointers explicitly so we can print a more appropriate message. We prefix the path with a `"*"` and parenthesize it to avoid ambiguity.

### Interfaces

Again, we use `IsNil` to test whether the interface is nil, and if not, we retrieve its dynamic value using `v.Elem()` and print its type and value.

Now that our `Display` function is complete, let's put it to work. The `Movie` type below is a slight variation on the one in [Section 4.5](#part0040.html#id-json):

```
type Movie struct {
    Title, Subtitle string
    Year            int
    Color           bool
    Actor           map[string]string
    Oscars          []string
    Sequel          *string
}
```

Let's declare a value of this type and see what `Display` does with it:

```
strangelove := Movie{
    Title:    "Dr. Strangelove",
    Subtitle: "How I Learned to Stop Worrying and Love the Bomb",
    Year:     1964,
    Color:    false,
    Actor: map[string]string{
        "Dr. Strangelove":            "Peter Sellers",
        "Grp. Capt. Lionel Mandrake": "Peter Sellers",
        "Pres. Merkin Muffley":       "Peter Sellers",
        "Gen. Buck Turgidson":        "George C. Scott",
        "Brig. Gen. Jack D. Ripper":  "Sterling Hayden",
        `Maj. T.J. "King" Kong`:      "Slim Pickens",
    },

    Oscars: []string{
        "Best Actor (Nomin.)",
        "Best Adapted Screenplay (Nomin.)",
        "Best Director (Nomin.)",
        "Best Picture (Nomin.)",
    },
}
```

The call `Display("strangelove", strangelove)` prints:

```
Display strangelove (display.Movie):
strangelove.Title = "Dr. Strangelove"
strangelove.Subtitle = "How I Learned to Stop Worrying and Love the Bomb"
strangelove.Year = 1964
strangelove.Color = false
strangelove.Actor["Gen. Buck Turgidson"] = "George C. Scott"
strangelove.Actor["Brig. Gen. Jack D. Ripper"] = "Sterling Hayden"
strangelove.Actor["Maj. T.J. \"King\" Kong"] = "Slim Pickens"
strangelove.Actor["Dr. Strangelove"] = "Peter Sellers"
strangelove.Actor["Grp. Capt. Lionel Mandrake"] = "Peter Sellers"
strangelove.Actor["Pres. Merkin Muffley"] = "Peter Sellers"
strangelove.Oscars[0] = "Best Actor (Nomin.)"
strangelove.Oscars[1] = "Best Adapted Screenplay (Nomin.)"
strangelove.Oscars[2] = "Best Director (Nomin.)"
strangelove.Oscars[3] = "Best Picture (Nomin.)"
strangelove.Sequel = nil
```

We can use `Display` to display the internals of library types, such as `*os.File`:

```
Display("os.Stderr", os.Stderr)
// Output:
// Display os.Stderr (*os.File):
// (*(*os.Stderr).file).fd = 2
// (*(*os.Stderr).file).name = "/dev/stderr"
// (*(*os.Stderr).file).nepipe = 0
```

Notice that even unexported fields are visible to reflection. Beware that the particular output of this example may vary across platforms and may change over time as libraries evolve. (Those fields are private for a reason!) We can even apply `Display` to a `reflect.Value` and watch it traverse the internal representation of the type descriptor for `*os.File`. The output of the call `Display("rV", reflect.ValueOf(os.Stderr))` is shown below, though of course your mileage may vary:

```
Display rV (reflect.Value):
(*rV.typ).size = 8
(*rV.typ).hash = 871609668
(*rV.typ).align = 8
(*rV.typ).fieldAlign = 8
(*rV.typ).kind = 22
(*(*rV.typ).string) = "*os.File"
```

```
(*(*(*rV.typ).uncommonType).methods[0].name) = "Chdir"
(*(*(*(*rV.typ).uncommonType).methods[0].mtyp).string) = "func() error"
(*(*(*(*rV.typ).uncommonType).methods[0].typ).string) = "func(*os.File) error"
...
```

Observe the difference between these two examples:

```
var i interface{} = 3

Display("i", i)
// Output:
// Display i (int):
// i = 3

Display("&i", &i)
// Output:
// Display &i (*interface {}):
// (*&i).type = int
// (*&i).value = 3
```

In the first example, `Display` calls `reflect.ValueOf(i)`, which returns a value of kind `Int`. As we mentioned in [Section 12.2](#part0113.html#id-reflecttypeandreflectvalue), `reflect.ValueOf` always returns a `Value` of a concrete type since it extracts the contents of an interface value.

In the second example, `Display` calls `reflect.ValueOf(&i)`, which returns a pointer to `i`, of kind `Ptr`. The switch case for `Ptr` calls `Elem` on this value, which returns a `Value` representing the *variable* `i` itself, of kind `Interface`. A `Value` obtained indirectly, like this one, may represent any value at all, including interfaces. The `display` function calls itself recursively and this time, it prints separate components for the interface's dynamic type and value.

As currently implemented, `Display` will never terminate if it encounters a cycle in the object graph, such as this linked list that eats its own tail:

```
// a struct that points to itself
type Cycle struct{ Value int; Tail *Cycle }
var c Cycle
c = Cycle{42, &c}
Display("c", c)
```

`Display` prints this ever-growing expansion:

```
Display c (display.Cycle):
c.Value = 42
(*c.Tail).Value = 42
(*(*c.Tail).Tail).Value = 42
(*(*(*c.Tail).Tail).Tail).Value = 42
...ad infinitum...
```

Many Go programs contain at least some cyclic data. Making `Display` robust against such cycles is tricky, requiring additional bookkeeping to record the set of references that have been followed so far; it is costly too. A general solution requires `unsafe` language features, as we will see in [Section 13.3](#part0124.html#id-exampledeepequivalence).

Cycles pose less of a problem for `fmt.Sprint` because it rarely tries to print the complete structure. For example, when it encounters a pointer, it breaks the recursion by printing the pointer's numeric value. It can get stuck trying to print a slice or map that contains itself as an element, but such rare cases do not warrant the considerable extra trouble of handling cycles.

### Exercise 12.1

Extend `Display` so that it can display maps whose keys are structs or arrays.

### Exercise 12.2

Make `display` safe to use on cyclic data structures by bounding the number of steps it takes before abandoning the recursion. (In [Section 13.3](#part0124.html#id-exampledeepequivalence), we'll see another way to detect cycles.)

## 12.4 Example: Encoding S-Expressions

`Display` is a debugging routine for displaying structured data, but it's not far short of being able to encode or `marshal` arbitrary Go objects as messages in a portable notation suitable for inter-process communication.
