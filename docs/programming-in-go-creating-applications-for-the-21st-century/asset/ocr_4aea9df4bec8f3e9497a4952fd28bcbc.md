# 4.3.4. Key-Ordered Map Iteration

When producing data for human consumption we often need to present the data in some recognizable order. Here is an example that shows how to output the populationForCity map in alphabetical (strictly speaking, Unicode code point) order of city.

```
cities := make([]string, 0, len(populationForCity))
for city := range populationForCity {
    cities = append(cities, city)
}
sort.Strings(cities)
for _, city := range cities {
    fmt.Printf("-%10s %8d\n", city, populationForCity[city])
}
```

| | |
|---|---|
| Beijing | 11290000 |
| Istanbul | 12610000 |
| Karachi | 11620000 |
| Mumbai | 12900000 |

We are creating a slice of type []string with zero length (i.e., empty), but with enough capacity to hold all of the map's keys. We then iterate over the map retrieving only the keys (since we have used just one variable, rather than the two needed to retrieve each city key-value pair), and appending each city in turn to the cities slice. Next, we sort the slice, and then iterate over the slice (using the int index by the blank identifier), looking up the corresponding city's population at each iteration.

The algorithm shown here—create an empty slice large enough to hold all of the map's keys, add all the map's keys to the slice, sort the slice, and iterate over the slice to produce ordered output—can be applied generally for key-ordered map iteration.

An alternative to the approach taken here is to use an ordered data structure in the first place—for example, an ordered map. We will see an example of this in a later chapter ($6.5.3, ➤ 302).

Value ordering is also possible, for example, by doing a map inversion, and we will see in the next subsection.

# 4.3.5. Map Inversion

We can easily invert a map whose values are unique—and whose type is acceptable for map keys. Here is an example.

```
cityForPopulation := make(map[int]string, len(populationForCity))
```