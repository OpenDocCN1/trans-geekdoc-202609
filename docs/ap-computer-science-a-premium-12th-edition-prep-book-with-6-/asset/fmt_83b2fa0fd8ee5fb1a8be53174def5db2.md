
## 9
A program evaluates binary arithmetic expressions that are read from an input file. All of the operands are integers, and the only operators are `+`, `-`, `*`, and `/`. In writing the program, the programmer forgot to include a test that checks whether the right-hand operand in a division expression equals zero. When will this oversight be detected by the computer?

(A) At compile time
(B) While editing the program
(C) As soon as the data from the input file is read
(D) During evaluation of the expressions
(E) When at least one incorrect value for the expressions is output

## 10
A programmer plans to write a program that simulates various games. In the program, there is a `Player` class that has a `getMove` method. Method `getMove` returns an `int` value to simulate a move in a game.

Which of the games described below are suitable candidates for using the `getMove` method as specified above?

I. **High-Low Guessing Game**: The computer thinks of a number and the player who guesses it with the least number of guesses wins. After each guess, the computer tells whether its number is higher or lower than the player’s guess.

II. **Chips**: Start with a pile of chips. Each player, in turn, removes some number of chips, but not all of them. The winner is the one who removes the final chip.

III. **Tic-Tac-Toe**: Two players alternate placing “X” or “O” on a 3×3 grid. The first player to get three in a row, where a row can be horizontal, vertical, or diagonal, wins.

(A) I only
(B) II only
(C) III only
(D) I and II only
(E) I, II, and III

## 11
Which best describes the precondition of a method? It is an assertion that

(A) describes precisely the conditions that must be true at the time the method is called.
(B) initializes the parameters of the method.
(C) describes the effect of the method on its postcondition.
(D) explains what the method does.
(E) states what the initial values of the local variables in the method must be.

## 12
Consider the following code fragment.

![images](images/f207-01.jpg)

For this algorithm, which of the following initial setups for `a1`, `a2`, and `a3` will cause

(1) the least number of computer operations (best case) and
(2) the greatest number of computer operations (worst case)?

(A) (1) largest value in `a1` or `a2`
    (2) largest value in `a3`
(B) (1) largest value in `a2` or `a3`
    (2) largest value in `a1`
(C) (1) smallest value in `a1`
    (2) largest value in `a2`
(D) (1) largest value in `a2`
    (2) smallest value in `a3`
(E) (1) smallest value in `a1` or `a2`
    (2) largest value in `a3`

## 13
Refer to the following code segment.

![images](images/f207-02.jpg)

What is the precondition for the `while` loop?

(A) `k` ≥ `N`, `sum = 1.0`
(B) `sum = 1 + 2 + 3 + ... + k`
(C) `k < N`, `sum = 1.0`
(D) `N` ≥ `1`, `k = 1`, `sum = 1.0`
(E) `mean = sum / N`

## 14
The sequence of Fibonacci numbers is 1, 1, 2, 3, 5, 8, 13, 21, .... The first two Fibonacci numbers are each 1. Each subsequent number is obtained by adding the previous two. Consider this method.

![images](images/f207-08.jpg)

Which of the following is a correct `/*` ***assertion*** `*/` about the loop variable `i`?

(A) `1` ≤ `i` ≤ `n`
(B) `0` ≤ `i` ≤ `n`
(C) `3` ≤ `i` ≤ `n`
(D) `3` < `i` ≤ `n`
(E) `3` < `i` < `n+1`

## 15
Refer to the following method.

![images](images/f208-01.jpg)

What is the postcondition for method `mystery`?

(A) `total` = *a* + *b*
(B) `total` = *a^b*
(C) `total` = *b^a*
(D) `total` = *a* ∗ *b*
(E) `total` = *a*/*b*

## 16
A program is to be written that prints an invoice for a small store. A copy of the invoice will be given to the customer and will display:

- A list of items purchased.
- The quantity, unit price, and total price for each item.
- The amount due.

Three candidate classes for this program are `Invoice`, `Item`, and `ItemList`, where an `Item` is a single item purchased and `ItemList` is the list of all items purchased. Which class is a reasonable choice to be responsible for the `amountDue` method, which returns the amount the customer must pay?

I. `Item`
II. `ItemList`
III. `Invoice`

(A) I only
(B) III only
(C) I and II only
(D) II and III only
(E) I, II, and III

## 17
Which is a false statement about classes in object-oriented program design?

(A) If a class `C1` has an instance variable whose type is another class, `C2`, then `C1` *has-a* `C2`.
(B) If a class `C1` is associated with another class, `C2`, then `C1` depends on `C2` for its implementation.
(C) If classes `C1` and `C2` are related such that `C1` *is-a* `C2`, then `C2` *has-a* `C1`.
(D) If class `C1` is independent, then none of its methods will have parameters that are objects of other classes.
(E) Classes that have common methods do not necessarily define an inheritance relationship.

## 18
A Java program maintains a large database of vehicles and parts for a car dealership. Some of the classes in the program are `Vehicle`, `Car`, `Truck`, `Tire`, `Circle`, `SteeringWheel`, and `AirBag`. The declarations below show the relationships between classes. Which is a poor choice?

![images](images/f209-01.jpg)

## 19
A Java programmer has completed a preliminary design for a large program. The programmer has developed a list of classes, determined the methods for each class, established the relationships between classes, and written an outline for each class. Which class(es) should be implemented first?

(A) Any superclasses
(B) Any subclasses
(C) All collaborator classes (classes that will be used to implement other classes)
(D) The class that represents the dominant object in the program
(E) All independent classes (classes that have no references to other classes)

## 20
Use the program description below for Questions 20–22.

A program is to be written that simulates bumper cars in a video game. The cars move on a square grid and are located on grid points (*x*, *y*), where *x* and *y* are integers between −20 and 20. A bumper car moves in a random direction, either left, right, up, or down. If it reaches a boundary (i.e., *x* or *y* is ±20), then it reverses direction. If it is about to collide with another bumper car, it reverses direction. Your program should be able to add bumper cars and run the simulation. One step of the simulation allows each car in the grid to move. After a bumper car has reversed direction twice, its turn is over and the next car gets to move.

To identify classes in the program, the nouns in the specification are listed:

program, bumper car, grid, grid point, integer, direction, boundary, simulation

How many nouns in the list should immediately be discarded because they are unsuitable as classes for the program?

(A) 0
(B) 1
(C) 2
(D) 3
(E) 4

## 21
A programmer decides to include the following classes in the program. Refer to them for Questions 21 and 22.

- `Simulation` will run the simulation.
- `Display` will show the state of the game.
- `BumperCar` will know its identification number, position in the grid, and current direction when moving.
- `GridPoint` will be a position in the grid. It will be represented by two integer fields, `x_coord` and `y_coord`.
- `Grid` will keep track of all bumper cars in the game, the number of cars, and their positions in the grid. It will update the grid each time a car moves. It will be implemented with a two-dimensional array of `BumperCar`.

Which operation should not be the responsibility of the `GridPoint` class?

![images](images/f209-02.jpg)

## 22
