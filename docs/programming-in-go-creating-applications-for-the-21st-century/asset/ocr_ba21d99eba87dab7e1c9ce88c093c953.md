# 6.5. Examples

Every key–value pair is added using the omap.Insert() method which accepts two interface{} values, that is, a key and a value of any types. (However, the key must be of a type that is compatible with the less function, so in this example keys must be strings.) The Insert() method returns true if a new item was inserted, and false if an item with the given key already existed (in case that item's value is replaced by the new given value—this is the same behavior as the built-in map type)

```
wordFor.Do(func(key, value interface{}) {
  fmt.Printf("%v-%v\n", key, value)
})
a~A
About~ABOUT
in~IN
Land~IN-LAND
Puttering~PUTTERING
Small~SMALL
```

The omap.Map.Do() method takes a function with the signature func(interface{}, interface{}) as argument and calls this function on every item in the ordered map—in key and the value as the arguments for each call. Here we have used the Do() method to print all of the WordFor's keys and values.

In addition to inserting items and calling a method on all the map's items, we can also query how many items are in the map, search for items, and delete items.

```
fmt.Println("length before deleting:", wordFor.Len())
, containsSmall := wordFor.Find("small")
fmt.Println("contains small:", containsSmall)
for _, key := range [string]struct("big", "medium", "small") {
  fmt.Printf("%t ", wordFor.Delete(key))
}
, containsSmall = wordFor.Find("small")
fmt.Println("length after deleting: ", wordFor.Len())
fmt.Println("contains small:", containsSmall)

length before deleting: 6
contains small: true
false true
length after deleting: 5
contains small: false
```

The omap.Map.Len() method returns the number of items in the ordered map.