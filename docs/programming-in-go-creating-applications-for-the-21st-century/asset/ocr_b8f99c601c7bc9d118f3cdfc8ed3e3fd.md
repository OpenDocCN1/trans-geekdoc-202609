# Chapter 6. Object-Oriented Programming

While we consider passing in a value of an invalid type to be a programming error and therefore worthy of returning a non-nil error, we have chosen to treat out-of-range values more leniently, and simply clamp them to the nearest value.

```
func (fuzzy *FuzzyBool) String() string {
	return fmt.Sprintf("%0f%%", 100*fuzzy.value)
}
```

We have chosen the string representation of fuzzy Booleans to be the whole number percentages. (Recall that the "%0f" string format specifies a floating-point number with no decimal point or decimal digits and the "%%" format specifies a literal character. String formatting was covered earlier; $3.5, 93 ◄)

```
func (fuzzy *FuzzyBool) Set(value interface{}) (err error) {
	fuzzy.value, err = float32ForValue(value)
	return err
}
```

The presence of this method is what makes our fuzzy Booleans mutable. The method is very similar to the New() function, only here we work on an existing *FuzzyBool rather than creating a new one. If the returned error is not nil then the fuzzy Boolean's value will be invalid, so we expect our callers to check the return value.

```
func (fuzzy *FuzzyBool) Copy() *FuzzyBool {
	return &FuzzyBool{fuzzy.value}
}
```

For custom types that are passed around as pointers, it is often convenient to provide a Copy() method. Here, we create a new FuzzyBool, with the same value as that of the receiver, and return a pointer to it. There is no need to do any validation since we know that the receiver's value is valid. This assumes, of course, that the original had a nil error when it was created with New(), and similarly for any subsequent calls to the Set() method.

```
func (fuzzy *FuzzyBool) Not() *FuzzyBool {
	return &FuzzyBool{!fuzzy.value}
}
```

This is the first of the logical operator methods, and like all the methods, it works on a *FuzzyBool receiver.