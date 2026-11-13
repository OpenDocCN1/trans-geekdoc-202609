cannibal rows across; two cannibals row across; one missionary and one cannibal go; one missionary crosses; or two missionaries do. These possibilities are represented with five arrows going from the initial state to five intermediate states.

![](bbox=[0.23, 0.21, 0.77, 0.41])

# Figure 190: Creating a game tree

For each of these five intermediate states, you can play the same game again. In figure 190 you see how the game continues for the middle (third) one of the new states. Because there are only two people on the right river bank, you see three possibilities: a cannibal goes back, a missionary goes back, or both do. Hence three arrows connect the middle state to the three states on the right side of the tree. If you keep drawing this tree of possibilities in a systematic manner, you eventually discover the final state.

A second look at figure 190 reveals two problems with this naive approach to generating the tree of possibilities. The first one is the dashed arrow that connects the middle state on the right to the initial state. It indicates that rowing back the two people from the right to the left gets the puzzle back to its initial state, meaning you're starting over, which is obviously undesirable. The second problem concerns those states with a star in the top-right corner. In both cases, there are more white-circle cannibals than black-circle missionaries on the left river bank, meaning the cannibals would eat the missionaries. Again, the goal is to avoid such states, making these moves undesirable.

One way to turn this puzzle into a program is to design a function that