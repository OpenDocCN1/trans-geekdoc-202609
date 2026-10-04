# 3.3.1 Iteration

To iterate a map we would require the collection of keys. Fortunately, the range built-in function offers a simple solution to iterate through all the key-value pair of any map. The rules explained for slices apply in the case of maps. For every iteration range returns the current key and value.

Example 3.8: map iteration using range.

```
package main

import "fmt"

func main() {
	sales := map[string]int{
	"Jan": 34345,
	"Feb": 11823,
	"Mar": 8838,
	"Apr": 32,
}

	fmt.Println("Month\tSales")
	for month, sale := range sales {
	fmt.Printf("%s\t%d\n", month, sale)
}
}
```

> The function range does not guarantee the same order for consecutive iterations.

# 3.4 SUMMARY

This Chapter shows how to declare, manipulate, and iterate through arrays, slices, and maps. These three native structures are extremely versatile and widely used in any Go program. The next Chapter exposes the tools Go offers to define their own data structures.