# 304
Chapter 6. Object-Oriented Programming

The omap.Map.Find() method returns the value of the item with the given key
as an interface{} and return true, nil and false if there is no such item. The omap.
Map.Delete() method deletes the item with the given key and returns true—or
sely does nothing if there is no such item, and returns false.

If we want to store keys of a custom type we can do so by creating the Map with
tomap.Map.New() function and supplying it with a suitable lest method.
For example, here is an implementation of a very simple custom type.

```
type Point struct{X, Y int}
func (point Point) String() string {
	return fmt.Sprintf("{%%d, %%d}", point.X, point.Y)
}
```

Now we will see how to create an ordered map that stores *Points as keys and
dist distance from the origin as values.

In the following snippet we have created an empty map and it can a less
function for comparing *Point keys. Then we have created a slice of *Points and
pulated the map from the points. And finally, we have used the omap.Map.Do()
method to print the map's keys and values in key order.

```
distanceForPoint := omap.Map.New(func(a, b interface{}) bool {
	alpha, beta := a.(*Point), b.(*Point)
	if a.X != b.X {
		return alpha.Y < beta.Y
	}
})
points := []*Point{{3, 1}, {1, 2}, {2, 3}, {1, 3}, {3, 2}, {2, 1}, {2, 2}}
for _, point := range points {
	distance := math.Hypot(float64(point.X), float64(point.Y))
	distanceForPoint.Insert(point, distance)
}
distanceForPoint.Do(func(key, value interface{}) {
	fmt.Printf("%%v -> %%.2v\\n", key, value)
})
```

+   (1, 2) -> 2.2
(1, 3) -> 3.2
(2, 1) -> 2.2
(2, 2) -> 2.8
(2, 3) -> 3.6
(3, 1) -> 3.2
(3, 2) -> 3.6