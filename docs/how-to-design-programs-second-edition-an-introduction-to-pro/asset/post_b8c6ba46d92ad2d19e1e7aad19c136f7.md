

but you may use any colors. Observe how the chameleon changes colors to blend in as it crosses the border between two colors.

Have some Italian pizza when you're done.

Note When you watch the animation carefully, you see the chameleon riding on a white rectangle. If you know how to use image editing software, modify the picture so that the white rectangle is invisible. Then the chameleon will really blend in.

## 6 Itemizations and Structures

The preceding two chapters introduce two ways of formulating data definitions. Those that employ itemization (enumeration and intervals) are used to create small collections from large ones. Those that use structures combine multiple collections. Since the development of data representations is the starting point for proper program design, it cannot surprise you that programmers frequently want to itemize data definitions that involve structures or to use structures to combine itemized data.

Recall the imaginary space invader game from chapter 5.9 in the preceding chapter. Thus far, it involves one UFO, descending from space, and one tank on the ground, moving horizontally. Our data representation uses a structure with two fields: one for the data representation of the UFO and another one for the data representation of the tank. Naturally, players will want a tank that can fire off a missile. All of a sudden, we can think of a second kind of state that contains three independently moving objects: the UFO, the tank, and the missile. Thus we have two distinct structures: one for representing two independently moving objects and another one for the third. Since a world state may now be one of these two structures, it is natural to use an itemization to describe all possible states:

- 1. the state of the world is a structure with two fields, or
- 2. the state of the world is a structure with three fields.

As far as our domain is concerned—the actual game—the first kind of state represents the time before the tank has launched its sole missile and the second one the time after the missile has been fired.

> No worries, the next part of the book is about firing as many missiles as you want, without reloading.

This chapter introduces the basic idea of itemizing data definitions that involve structures. Because we have all the other ingredients we need, we start straight with itemizing structures. After that, we discuss some examples, including world programs that benefit from our new power. The last section is about errors in programming.

### 6.1 Designing with Itemizations, Again

Let's start with a refined problem statement for our space invader game from chapter 5.6.

**Sample Problem** Design a game program using the 2htdp/universe library for playing a simple space invader game. The player is in control of a tank (a small rectangle) that must defend our planet (the bottom of the canvas) from a UFO (see chapter 4.4 for one possibility) that descends from the top of the canvas to the bottom. In order to stop the UFO from landing, the player may fire a single missile (a triangle smaller than the tank) by hitting the space bar. In response, the missile emerges from the tank. If the UFO collides with the missile, the player wins; otherwise the UFO lands and the player loses.

Here are some details concerning the three game objects and their movements. First, the tank moves a constant speed along the bottom of the canvas, though the player may use the left arrow key and the right arrow key to change directions. Second, the UFO descends at a constant velocity but makes small random jumps to the left or right. Third, once fired, the missile ascends along a straight vertical line at a constant speed at least twice as fast as the UFO descends. Finally, the UFO and the missile collide if their reference points are close enough, for whatever you think “close enough” means.

The following two subsections use this sample problem as a running example, so study it well and solve the following exercise before you continue. Doing so will help you understand the problem in enough depth.

**Exercise 94.** Draw some sketches of what the game scenery looks like at various stages. Use the sketches to determine the constant and the variable pieces of the game. For the former, develop physical and graphical constants that describe the dimensions of the world (canvas) and its objects. Also develop some background scenery. Finally, create your initial scene from the constants for the tank, the UFO, and the background.

**Defining Itemizations** The first step in our design recipe calls for the development of data definitions. One purpose of a data definition is to describe the construction of data that represents the state of the world; another is to describe all possible pieces of data that the event-handling functions of the world program may consume. Since we haven’t seen itemizations that include structures, this first subsection introduces this idea. While this probably won’t surprise you, pay close attention.

> > For this space invader game, we could get away with one structure type definition of three fields where the third field contains #false until the missile is fired, and a Posn for the missile’s coordinates thereafter. See below.

As argued in the introduction to this chapter, the space invader game with a missile-firing tank requires a data representation for two different kinds of game states. We choose two structure type definitions:

```
(define-struct aim [ufo tank])
```

```
(define-struct fired [ufo tank missile])
```

The first one is for the time period when the player is trying to get the tank in position for a shot, and the second one is for representing states after the missile is fired. Before we can formulate a data definition for the complete game state, however, we need data representations for the tank, the UFO, and the missile.

Assuming constant definitions for such physical constants as WIDTH and HEIGHT, which are the subject of exercise 94, we formulate the data definitions like this:

```
; A UFO is a Posn.
; interpretation (make-posn x y) is the UFO's location
; (using the top-down, left-to-right convention)

(define-struct tank [loc vel])
; A Tank is a structure:
; (make-tank Number Number).
; interpretation (make-tank x dx) specifies the position:
; (x, HEIGHT) and the tank's speed: dx pixels/tick

; A Missile is a Posn.
; interpretation (make-posn x y) is the missile's place
```

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

- Here is an instance that describes the tank maneuvering into position to fire the missile:

```
(make-aim (make-posn 20 10) (make-tank 28 -3))
```

- This one is just like the previous one but the missile has been fired:

```
(make-fired (make-posn 20 10)
  (make-tank 28 -3)
  (make-posn 28 (- HEIGHT TANK-HEIGHT )))
```

Of course, the capitalized names refer to the physical constants that you defined.

