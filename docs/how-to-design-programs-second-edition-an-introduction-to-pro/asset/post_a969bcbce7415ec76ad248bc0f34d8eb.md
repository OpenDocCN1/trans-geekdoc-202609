
open to closed, suggests the use of clock ticks. For the other arrows, we could use either key presses or mouse clicks. Let’s use three keystrokes: "u" for unlocking the door, "1" for locking it, and the space bar " " for pushing it open. The right-hand-side diagram of figure 28 expresses these choices graphically; it translates the state-machine diagram from the world of information into the world of data in BSL.

![](img/19fbe4068996ced0ce42cec7fb82a834_193_0.png)

## Figure 28: A transition diagram for a door with an automatic closer

Once we have decided to use the passing of time for one action and key presses for the others, we must design functions that render the current state of the world—represented as DoorState—and that transform it into the next state of the world. And that, of course, amounts to a wish list of big-bang functions:

- door-closer, which closes the door during one tick;
- door-action, which acts on it in response to pressing a key; and
- door-render, which translates the current state into an image.

Stop! Formulate appropriate signatures.

We start with door-closer. Since door-closer acts as the on-tick handler, we get its signature from our choice of DoorState as the collection of world states:

```
; DoorState -> DoorState
```

```
; closes an open door over the period of one tick
(define (door-closer state-of-door) state-of-door)
```

Making up examples is trivial when the world can only be in one of three states. Here we use a table to express the basic idea, just like in some of the mathematical examples given above:

| given state | desired state |
| --- | --- |
| LOCKED | LOCKED |
| CLOSED | CLOSED |
| OPEN | CLOSED |

Stop! Express these examples as BSL tests.
The template step demands a conditional with three clauses:

```
(define (door-closer state-of-door)
  (cond
    [(string=? LOCKED state-of-door) LOCKED]
    [(string=? CLOSED state-of-door) CLOSED]
    [(string=? OPEN state-of-door) CLOSED])))
```

Don't forget to run your tests.
The second function, door-action, takes care of the remaining three arrows of the diagram. Functions that deal with keyboard events consume both a world and a key event, meaning the signature is as follows:

```
; DoorState KeyEvent -> DoorState
; turns key event k into an action on state s
(define (door-action s k)
  s)
```

We once again present the examples in tabular form:

| given state | given key event | desired state |
| --- | --- | --- |
| LOCKED | "u" | CLOSED |
| CLOSED | "1" | LOCKED |
| CLOSED | " " | OPEN |
| OPEN | - | OPEN |

The examples combine information from our drawing with the choices we made about mapping actions to keyboard events. Unlike the table of examples for traffic light, this table is incomplete. Think of some other examples; then consider why our table suffices.

From here, it is straightforward to create a complete design:

```
(check-expect (door-action LOCKED "u") CLOSED)
(check-expect (door-action CLOSED "1") LOCKED)
(check-expect (door-action CLOSED " ") OPEN)
(check-expect (door-action OPEN "a") OPEN)
(check-expect (door-action CLOSED "a") CLOSED)

(define (door-action s k)
  (cond
    [(and (string=? LOCKED s) (string=? "1" k))
     CLOSED]
    [(and (string=? CLOSED s) (string=? "1" k))
     LOCKED]
    [(and (string=? CLOSED s) (string=? " " k))
     OPEN]
    [else s]))
```

Note the use of and to combine two conditions: one concerning the current state of the door and the other concerning the given key event.

Lastly, we need to render the state of the world as a scene:

```
; DoorState -> Image
; translates the state s into a large text image
(check-expect (door-render CLOSED)
             (text CLOSED 40 "red"))
(define (door-render s)
  (text s 40 "red"))
```

This simplistic function uses large text. Here is how we run it all:

```
; DoorState -> DoorState
; simulates a door with an automatic door closer
(define (door-simulation initial-state)
  (big-bang initial-state
            [on-tick door-closer]
            [on-key door-action]
            [to-draw door-render]))
```

Now it is time for you to collect the pieces and run them in DrRacket to see whether it all works.

**Exercise** 62. During a door simulation the “open” state is barely visible. Modify door-simulation so that the clock ticks once every three seconds. Rerun the simulation.

## 5 Adding Structure

Suppose you want to design a world program that simulates a ball bouncing back and forth on a straight vertical line between the floor and ceiling of some imaginary, perfect room. Assume that it always moves two pixels per clock tick. If you follow the design recipe, your first goal is to develop a data representation for what changes over time. Here, the ball’s position and its direction change over time, but that’s two values while big-bang keeps track of just one. Thus the question arises how one piece of data can represent two changing quantities of information.

Here is another scenario that raises the same question. Your cell phone is mostly a few million lines of code wrapped in plastic. Among other things, it administrates your contacts. Each contact comes with a name, a phone number, an email address, and perhaps some other information. When you have lots of contacts, each single contact is best represented as a single piece of data; otherwise the various pieces could get mixed up by accident.

> Mathematicians know tricks that “merge” two numbers into a single number such that it is possible to retrieve the original ones. Programmers consider these kinds of tricks evil because they obscure a program’s true intentions.

Because of such programming problems, every programming language provides some mechanism to combine several pieces of data into a single piece of compound data and ways to retrieve the constituent values when needed. This chapter introduces BSL’s mechanics, so-called structure type definitions, and how to design programs that work on compound data.

### 5.1 From Positions to posn Structures

A position on a world canvas is uniquely identified by two pieces of data: the distance from the left margin and the distance from the top margin. The first is called an x-coordinate and the second one is the y-coordinate.

DrRacket, which is basically a BSL program, represents such positions with posn structures. A posn structure combines two numbers into a single value. We can create a posn structure with the operation make-posn, which consumes two numbers and makes a posn. For example,

```
(make-posn 3 4)
```

is an expression that creates a posn structure whose x-coordinate is 3 and whose y-coordinate is 4.

A posn structure has the same status as a number or a Boolean or a string. In particular, both primitive operations and functions may consume and produce structures. Also, a program can name a posn structure:

```
(define one-posn (make-posn 8 6))
```

Stop! Describe one-posn in terms of coordinates.

Before doing anything else, let’s take a look at the laws of computation for posn structures. That way, we can both create functions that process posn structures and predict what they compute.

### 5.2 Computing with posns

While functions and the laws of functions are completely familiar from pre-algebra, posn structures appear to be a new idea. Then again, the concept of a posn ought to look like the Cartesian points or positions in the plane you may have encountered before.

Selecting a Cartesian point’s pieces is also a familiar process. For example, when a teacher says, “take a look at the graph of figure 29 and tell me what $p_x$ and $p_y$ are,” you are likely to answer 31 and 26, respectively, because you know that you need to read off the values where the vertical and horizontal lines that radiate out from p hit the axes.

![](img/19fbe4068996ced0ce42cec7fb82a834_199_0.png)

## Figure 29: A Cartesian point

We thank Neil Toronto for the plot library.

We can express this idea in BSL. Assume you add

```
(define p (make-posn 31 26))
```

to the definitions area, click RUN, and perform these interactions:

```
> (posn-x p)
31
> (posn-y p)
26
```
