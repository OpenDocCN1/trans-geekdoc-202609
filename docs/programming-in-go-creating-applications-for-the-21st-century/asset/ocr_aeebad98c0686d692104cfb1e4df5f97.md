# 5.6. Custom Functions

```
value := function(x, xs...)
cache[key] = value
return value
```

The Memoize function we have used here is very basic. It takes a memoizeFunction as argument (with the signature func(int, ...int) interface{}) and returns a function with the same signature.

We use a map to cache computed results with string keys and interface{} values. The map is captured by the anonymous function (closure) that the Memoize() returns. The key is made up of all the integer arguments joined together in a single comma-separated string. (Go maps require keys that fully defined == != operators meet this requirement, but slices do not) §4.3,164 Once the key has been computed we see if there is a corresponding key-value pair in the map—if there we don't need to recompute anything and can simply return the cached value. Otherwise we perform the computation by calling the function that we were given to memoize with the integer argument or arguments. Then we cache the result in the map so that we will never need to recompute these particular arguments, and finally, return the computed value.

Memoization is useful for relatively expensive pure functions (whether or not they are recursive) that are called lots of times with the same arguments. For example, if we were converting large numbers of integers into roman numerals and lots of the numbers were repeated it might make sense to use the Memoize function to avoid repeated computations. Naturally, it is best to time expensive operations (e.g., by using the time package or a profiler) to see if memoization (or any other potential optimization) is worthwhile.

```
var RomanDecimal memoizeFunction

func init() {
	ecimals := []int{1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1}
	romans := []string{"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"}
	RomanDecimal := Memoize(func(x int, xs ...int) interface{} {
		if x < 0 || x > 3999 {
			panic("RomanDecimal only handles integers [0, 3999]")
		}
	var buffer bytes.Buffer
	for i, decimal := range decimals {
		remainder := x / decimal
		x %= decimal
		if remainder > 0 {
	\}
```