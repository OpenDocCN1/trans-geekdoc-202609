# Chapter 6. Object-Oriented Programming

```
type shape struct{ fill color.Color }
func newShape(fill color.Color) shape {
  if fill == nil // We Silently treat a nil color as black
    fill = color.Black
  }
  return shape{fill}
}
func (shape) Fill() color.Color { return shape.fill }
func (shape *shape) SetFill(fill color.Color) {
  if fill == nil // We Silently treat a nil color as black
    fill = color.Black
  }
  shape.fill = fill
}
```

This simple type is unexported so it is only accessible inside the shapes package. This means that no shape value can be created outside the package.

In the hierarchical shape1 shapes type does not fulfill any of the interfaces because it does not have a Draw() method. But in the compositional shape2 shapes package it fulfills the Filler interface.
In the code as it stands, only the Circle type (which we will cover in a moment) directly embeds a theory. So, we could have incorporated the color.Color value into the Circle type and make the color getter and setter *Circles instead of shapes, and eliminated the shape type altogether. However, we prefer to keep the shape type because it gives us the flexibility to add shape interfaces and types that might be based directly on the shape type (i.e., to have a color), rather than on the Circle type (e.g., they don't have a notion of radius). This flexibility will come in handy in one of the exercises.

```
type Circle struct {
  shape
  radius int
}
```

```
func NewCircle(fill color.Color, radius int) *Circle {
  return &Circle(newShape(fill), saneRadius(radius))
}
```

```
func (circle *Circle) Radius() int {
  return circle.radius
}
```

```
func (circle *Circle) SetRadius(radius int) {
  circle.radius = saneRadius(radius)
}
```