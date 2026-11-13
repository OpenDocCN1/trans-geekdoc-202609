# # 12.5 Feeding Worms

**Worm**—also known as *Snake*—is one of the oldest computer games. When the game starts, a worm and a piece of food appear. The worm is moving toward a wall. Don’t let it reach the wall; otherwise the game is over. Instead, use the arrow keys to control the worm’s movements.

The goal of the game is to have the worm eat as much food as possible. As the worm eats the food, it becomes longer; more and more segments appear. Once a piece of food is digested, another piece appears. The worm’s growth endangers the worm itself, though. As it grows long enough, it can run into itself and, if it does, the game is over, too.

Figure 79 displays a sequence of screen shots that illustrates how the game works in practice. On the left, you see the initial setting. The worm consists of a single red segment, its head. It is moving toward the food, which is displayed as a green disk. The screen shot in the center shows a situation when the worm is about to eat some food. In the right-most screen shot the worm has run into the right wall. The game is over; the player scored 11 points.

![](bbox=[0.235, 0.504, 0.765, 0.668])

The following exercises guide you through the design and implementation of a Worm game. Like chapter 10.2, these exercises illustrate how to tackle a nontrivial problem via iterative refinement. That is, you don’t design the entire interactive program all at once but in several stages, called *iterations*. Each iteration adds details and refines the program—until it satisfies you or your customer. If you aren’t satisfied with the outcome of the exercises, feel free to create variations.

+   **Exercise 215.** Design a world program that continually moves a one-segment worm and enables a player to control the movement of the worm with