# 6.5. Examples

A reasonable rule of thumb is to create methods that take receiver values for immutable types, and methods that take pointers for mutable types. For mutable types, having some methods take values and others take pointers is perfectly possible—but can be inconvenient in practice.) It is also best to use pointers for large struct types (e.g., those with two or more fields), to keep cost of passing them to a single pointer.

```
func float32ForValue(value interface{}) { (float32, err error) {
	witch value := value.(type) { // shadow variable
	case float32:
		fuzzy = value
	case float64:
		fuzzy = float32(value)
	case int:
		fuzzy = float32(value)
	case bool:
		fuzzy = 0
		if value {
			fuzzy = 1
	}
		default:
		return 0, fmt.Errorf("float32ForValue(): %v is not a " +
		"number or Boolean", value)
	}
	if fuzzy < 0 {
		fuzzy = 0
	 else if fuzzy > 1 {
		fuzzy = 1
\}
	return fuzzy, nil
}
```

This exported helper function is used by the New() and Set() methods to convert a value into a float32 in the range [0.,1]. Handling the different types is easily accomplished by using a type switch ($5.2.2.2, 17).

If the function is called with a value of an invalid type we return a non-nil error. This gives the caller responsibility for checking the return value and responding appropriately if an error has occurred. The caller can panic on error and cause the application to crash with a traceback, or could handle the problem itself. It is often better for low-level functions like this to return an error when they hit a problem because they don’t know enough about the program’s logic to know how or to handle it, and to push the problem up to the caller which should be in a better position to know what to do.