
# This chapter will cover:

*   What is an interface and how does it differ from a struct.
*   How to add behaviour.
*   Implement an interface.
*   Type assertions.
*   Changing a value.

## Interface

To describe what an interface is, let’s start by talking about structs and how they are different from an interface.

With structs, we can define properties we want a concept to have, like for example a car:

``` 
1 type Car struct { 
2   make string 
3   model string 
4 }
```

An interface is meant to communicate something different, a behaviour. Instead of describing the car itself, as a struct does, it describes what a car can do.

## Interface - describing a behaviour

Now that we’ve described how an interface differs from a struct, let’s talk about the motivation for using an interface. There are a couple of good reasons for when to use an interface:

*   **Adding behaviour**. When you want your types to have a behaviour, that’s when you want an interface

*   **Communicate via contract**. Often, when you call other code, you want to reveal as little of your concrete implementation as possible. Instead of saying, here’s a car, you might want to say, here’s something that can run. It enables your code to be flexible and you don’t have to implement specific code for each type but can instead write code that deals with a certain behaviour.

### Define an interface

To define an interface, you need the keywords `type` and `interface` and you need a set of methods, one or many that a type should implement. Here’s an example interface:

``` 
1 type Describable interface { 
2   describe() string 
3 }
```

Here’s another example:

``` 
1 type Point struct { 
2   x int 
3   y int 
4 } 
5 
6 type Shape interface { 
7   area() int 
8   location() Point 
9 }
```

## Implement an interface

Everything that’s a type can implement an interface. More than one type can implement the same interface. Let’s look at how a type `Rectangle` can implement the `Shape` interface:

``` 
 1 type Rectangle struct { 
 2   x int 
 3   y int 
 4 } 
 5 
 6 func (r Rectangle) area() int { 
 7   return r.x * r.y 
 8 } 
 9 
10 func (r Rectangle) location() Point { 
11   return P{ x: r.x, y: r.y } 
12 }
```

So, what’s going on here? Let’s look at the first method `area()`:

``` 
1 func (r Rectangle) area() int { 
2   return r.x * r.y 
3 }
```

It looks like a regular function but there’s this `(r Rectangle)` right before the function name. That’s a signal to Go that you are implementing a certain function on the type `Rectangle`. There’s also a second implementation for `location()`.

By implementing both these methods, `Rectangle` has now fully implemented the `Shape` interface.

### Pass an interface

Ok, so we’ve fully implemented an interface, what does it allow me to do? Well, there are two things you can do:

*   **Call properties and behaviour**. At this point, you are ready to create an instance and call both properties and methods (its new behaviour):

    ``` 
    1  var rectangle Rectangle = Rectangle{x: 5, y: 2} 
    2  fmt.Println(rectangle.area()) // prints 10 
    ```

    Great, our `Rectangle` type has both the properties `x` and `y` as well as the behaviour from `Shape`.

*   **Pass an interface**. Imagine you wanted to pass the behaviour to a function to make it flexible:

    ``` 
    1  func printArea(shape Shape) { 
    2    fmt.Println(shape.area()) 
    3  }
    ```

    To make that happen, lets change slightly how we construct our `Rectangle instance`:

    ``` 
    1  var shape Shape = Rectangle{x: 5, y: 2} 
    2  printArea(rectangle) // prints 10 
    ```

### Implement `Square`

To see the power in what we just created, let’s create another struct `Square` and have it implement `Shape`:

``` 
 1 type Square struct { 
 2   side int 
 3 } 
 4 
 5 func (s Square) area() int { 
 6   return s.square * s.square 
 7 } 
 8 func (s Square) location() Point { 
10   return Point{x: s.side, y: s.side} 
11 } 
12 
13 func main() { 
14   var shape Shape = Rectangle{x: 5, y: 2} 
15   var shape2 Shape = Square{side: 5} 
16   printArea(shape) // prints 10 
17   printArea(shape2) // prints 25 
18 }
```

The power lies in the fact that `printArea()` doesn’t have to deal with the internals of `Rectangle` or `Shape`, it just needs the parameter to implement `Shape`, a behaviour.

### Full code

Here’s the full code:

``` 
 1 package main 
 2 
 3 import "fmt" 
 4 
 5 type Rectangle struct { 
 6  x int 
 7  y int 
 8 } 
 9 
10 type Point struct { 
11  x int 
12  y int 
13 } 
14 
15 type Square struct { 
16  side int 
17 } 
18 
19 type Shape interface { 
20  area() int 
21  location() Point 
22 } 
23 
24 func printArea(shape Shape) { 
25  fmt.Println(shape.area()) 
26 } 
27 
28 func (r Rectangle) area() int { 
29  return r.x * r.y 
30 } 
31 
32 func (r Rectangle) location() Point { 
33  return Point{x: r.x, y: r.y} 
34 } 
35 
36 func (s Square) area() int { 
37  return s.side * s.side 
38 } 
39 
40 func (s Square) location() Point { 
41  return Point{x: s.side, y: s.side} 
42 } 
43 
44 func main() { 
45  var shape Shape = Rectangle{x: 5, y: 2} 
46  var shape2 Shape = Square{side: 5} 
47  printArea(shape)  // prints 10 
48  printArea(shape2) // prints 25 
49 }
```

## Type assertions

So far, a `Rectangle` or `Square` implements the `Shape` interface

Let’s have a closer look at this code:

``` 
1 var shape Shape = Rectangle{x: 5, y: 2} 
2 var shape2 Shape = Square{side: 5} 
3 printArea(shape)  // prints 10 
4 printArea(shape2) // prints 25 
```

We’ve said for `shape` and `shape2` to be of type `Shape`. That’s great for being sent to the `printArea()` method. What if we need to access a `Rectangle` property on `shape`, can we? Let’s try:

``` 
1 var shape Shape = Rectangle{x: 5, y: 2} 
2 fmt.Println(shape.x) // shape.x undefined (type Shape has no field or method x) 
```

Ok, not working, we need to find a way to reach the underlying fields. We can use something called *type assertion* like so:

``` 
1 var shape Shape = Rectangle{x: 5, y: 2} 
2 fmt.Println(shape.(Rectangle).x) // 5 
```

Ok, that works, so `.(<type>)` works, if the underlying type is the correct type.

## Change a value

So, one thing about our approach so far is that we have implemented interfaces with methods that read data from the underlying struct instances. What if we want to change data, can we do that?

Let’s look at an example:

``` 
 1 package main 
 2 import "fmt" 
 3 
 4 type Car struct { 
 5  speed int 
 6  model string 
 7  make string 
 8 } 
 9 
10 type Runnable interface { 
11  run() 
12 } 
13 
14 func (c Car) run() { 
15  c.speed = 10 
16 } 
17 
18 func main() { 
19   c := Car{make: "Ferrari", model: "F40", speed: 0} 
20   c.run() 
21   fmt.Println(c.speed) // ? 
22 } 
```

Running this code, it returns `0`. So, looking at our `run()` method:

``` 
1 func (c Car) run() { 
2  c.speed = 10 
3 } 
```

shouldn’t this work? Well, no, because you are not changing the instance. For that, you need to send a reference.

A slight alteration to the `run()` method, with `*`:

``` 
1 func (c *Car) run() { 
2  c.speed = 10 
3 } 
```

and your code now does what it’s supposed to.

## Assignment

Start with the following code:

``` 
 1 package main 
 2 
 3 type Point struct { 
 4  x float32 
 5  y float32 
 6 } 
 7 
 8 type Vehicle struct { 
 9  velocity float32 
10  Point 
11 } 
12 
13 func main() { 
14  v := Vehicle{ 
15   velocity: 0, 
16   Point: Point{ 
17    x: 0, 
18    y: 0, 
19   }, 
20  } 
21  v.fly() 
22  fmt.Println(v.velocity) 
23  v.land() 
24  fmt.Println(v.velocity) 
25 }
```

Implement the following interface:

``` 
1 type Spaceship interface { 
2  fly() 
3  land() 
4  position() Point 
5 }
```

The output from running the program should be:

```
1 10
2 0
```

## Solution
