# 6.5. Examples

```
func main() {
	a := fuzzylook.New(0) // Safe to ignore error value when using
	b := fuzzylook.New(.25) // known valid values; must check if using
	c := fuzzylook.New(.75) // variables though.
	d := c.Copy()
	if err := d.Set(1); err != nil {
		fmt.Println(err)
}
	process(a, b, c, d)
	s := []*fuzzool.FuzzyBool{a, b, c, d}
	fmt.Println(s)
}

func process(a, b, c, d *fuzzyBool.FuzzyBool) {
	fmt.Println("Not: \ a.Not(), b.Not(), c.Not())
	fmt.Println("Not Not: \ a.Not().Not(), b.Not().Not(), c.Not().Not(), d.Not())
\td.Not().Not())
	fmt.Printf("And(.25)-", a.And(b), " .25.And(.75,1)-", b.And(c), d, "\n")
		" .75.And(1)-", c.And(d), "\n")	fmt.Printf("Or(.25)-", a.Or(b), " .25.Or(.75)-", b.Or(c), d, "\n")
		" .75.Or(1)-", c.Or(.75,1), d.Or(n\), "\n")
	fmt.Println("Bool: < a, c = a, c: > a.Less(c), a.Equal(c), c.Less(a))
	fmt.Println("Bool: \ a.Bool(), b.Bool(), c.Bool(), d.Bool())
	fmt.Println("Float: \ a.Float(), b.Float(), d.Float())
n
```

Original: 0% 25% 75% 100%
Not: 100% 75% 25% 0%
Not Not: 0% 25% 75% 100%
And(.25)-25 .25.And(.75)-75 .75.And(1)-75 0.And(.25,.75)-100
Or(.25)-25 .25.Or(.75)-75 .75.Or(1)-100 0.Or(.25,.75,1)-100
a < c, a = c, a: false true true
Bool: false true true
Float: 0 0.25 0.75 1
[ 0% 25% 75% 100%]

The custom type is called FuzzyBool. We will start by looking at the type definition, and then the construction. And we will finish by looking at the methods.

```
type FuzzyBool struct { value float32 }
```

The FuzzyBool is based on a struct that contains a single float32. The value is unprotected so anyone who imports the fuzzybool package must use the construction function (which we have New()), in accordance with Go