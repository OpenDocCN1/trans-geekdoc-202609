Each of these data definitions describes nothing but a structure, either a newly defined one, tank, or a built-in data collection, Posn. Concerning the latter, it may surprise you a little bit that Posns are used to represent two distinct aspects of the world. Then again, we have used numbers (and strings and Boolean values) to represent many different kinds of information in the real world, so reusing a collection of structures such as Posn isn’t a big deal.

Now we are in a position to formulate the data definitions for the state of the space invader game:

```
; A SIGS is one of:
; -- (make-aim UFO Tank)
; -- (make-fired UFO Tank Missile)
; interpretation represents the complete state of a
; space invader game
```

The shape of the data definition is that of an itemization. Each clause, however, describes the content of a structure type, just like the data definition for structure types we have seen so far. Still, this data definition shows that not every data definition comes with exactly one structure type definition; here one data definition involves two distinct structure type definitions.

The meaning of such a data definition is also straightforward. It introduces the name SIGS for the collection of all those structure instances that you can create according to the definition. So let us create some:

+   Here is an instance that describes the tank maneuvering into position to fire the missile:

```
(make-aim (make-posn 20 10) (make-tank 28 -3))
```

+   This one is just like the previous one but the missile has been fired:

```
(make-fired (make-posn 20 10)
  (make-tank 28 -3)
  (make-posn 28 (- HEIGHT TANK-HEIGHT )))
```

Of course, the capitalized names refer to the physical constants that you defined.