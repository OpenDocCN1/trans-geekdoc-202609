# 5.6. Custom Functions

```
return i
}
return -1
}
```

The IntSlicer() function takes an []int to search and an int to find and passes these over the generic IndexSlicer() function. The IndexSlicer() function operates in terms of a Slicer value—the Slicer type is a custom interface that is met by any value that provides the Slicer methods Slicer.EqualTo() and Slicer.Len().

```
type Slicer interface {
EqualTo(i int, x interface{}) bool
Len() int
}
```

```
type IntSlice []int
func (slice IntSlice) EqualTo(i int, x interface{}) bool {
  return slice[i] == x.(int)
func (slice IntSlice) Len() int { return len(slice) }
```

The Slicer interface specifies the two methods we need to implement the generic IndexSlicer() function.
The IntSlice type is based on an []int (which is why the IntSlicer() function can convert the []int it is passed into an IntSlice without formality), and implements the two methods required to fulfill the Slicer interface. The IntSlice.EqualTo() method takes a slice index and a value and returns true if the item at the generic index is equal to the value. The Slicer interface specifies the value as a generic interface{} rather than an int so that the Slicer interface can be implemented by other slice types (e.g., FloatSlice and String), so we must convert the value to the actual type. In this case we can safely use an unchecked assertion because we know that the value ultimately comes from a call to the IntSlicer() function which has a corresponding argument.

We can implement other custom slice types that satisfy the Slicer interface and then be used with the generic IndexSlicer() function.

```
type StringSlice []string
func (slice StringSlice) EqualTo(i int, x interface{}) bool {
  return slice[i] == x.(string)
}
```