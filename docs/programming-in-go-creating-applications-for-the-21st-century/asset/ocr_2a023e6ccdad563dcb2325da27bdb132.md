```
return (*ints)[i] < (*ints)[j]
func (ints *IntHeap) Swap(i, j int) {
    (*ints)[i], (*ints)[j] = (*ints)[j], (*ints)[i]
}
func (ints *IntHeap) Len() int {
    return len(*ints)
}
func (ints *IntHeap) Pop() interface{} {
    x := (*ints)[ints.Len()-1]
    *ints = (*ints)[:ints.Len()-1]
    return x
}
func (ints *IntHeap) Push(x interface{}) {
    *ints = append(*ints, x.(int))
}
```

This implementation is sufficient for many situations. We could make the code slightly nicer to read by specifying the type as type IntHeap struct { ints []int }, since then we could refer to its ints rather than *ints inside the methods.

The Container/list package provides a doubly linked list. Items added to the list are added as interface{} values. Items retrieved from the list have type list.Element, with the original accessible value as list.Element.Value.

```
items := list.New()
for _, x := range strings.Split("ABCDEFG", "") {
    items.PushFront(x)
}
items.PushBack(9)
for element := items.Front(); element != nil; element = element.Next() {
    switch value := element.Value(type) {
    case string:
        fmt.Printf("%s ", value)
    case int:
        fmt.Printf("%d ", value)
    }
}
fmt.Println(items) // prints: H G F E D B A 9
```

In this example we push eight single-letter strings onto the front of a new list and then push an int onto the end. We iterate over the list's elements and print each element's value. We didn't really need the type switch since