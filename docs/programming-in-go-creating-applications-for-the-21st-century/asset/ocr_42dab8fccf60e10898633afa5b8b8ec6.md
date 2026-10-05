# 412
Chapter 9. Packages

the package, and again godoc will provide a link to the “Packages” link. (We discussed godoc in the sidebar “The Go Documentation”, 8 ◀)

What constitutes good documentation is a contentious matter, so in this subsub-section we will concern ourselves purely with the mechanics of documenting Go packages.

By default exported types, classes, constants, and variables are shown by godoc, so all of these should be documented. Documentation is written directly in source code files.

```
// Package omap implements // Keys and values may be of any type, but all keys must be comparable
// using the less function that is passed to the omap.New()
// function, or the less function provided by the omap.New*()
// construction functions.
package omap
```

For a package, the comment immediately preceding the package statement is used as the package's description, with the first line (up to the first period if there is one, or to the newline) as a one-line summary. This is an example taken from the omap package (file qrac.eu/omap/omap.go—this package was covered in Chapter 6, §6.5.3, 302 ◀)

```
// Map is a key-ordered map.
// The zero value is an invalid map! Use one of the construction functions
// (e.g., New())), to create a map for a specific type.
type Map struct {
```

The documentation for the exported type must be written immediately before the type statement and should always indicate whether the type's zero value is valid.

```
// New returns an empty Map that uses the given less than function to
// compare keys. For example:
// type Point { X, Y int
// pointMap := omap.New(a, b interface{}) bool {
// 	alpha, beta := a.(Point), b.(Point)
// 	if alpha.X != beta.X {
// 		return alpha.X < beta.X
// 		return alpha.Y < beta.Y
// //}
func New(less func(interface{}, interface{}) bool) *Map {
```