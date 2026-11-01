
# Grid World Problem

A grid world problem is a two-dimensional rectangular array of square cells in which agents can move from cell to cell. Typically the agent can move to any obstacle-free adjacent cell—horizontally or vertically and in some problems diagonally. Cells can contain objects, which the agent can pick up, push, or otherwise act upon; a wall or other impassible obstacle in a cell prevents an agent from moving into that cell. The vacuum world from [Section 2.1](#Chapter02-01.xhtml#sec2-1) can be formulated as a grid world problem as follows:

Grid world

**States:** A state of the world says which objects are in which cells. For the vacuum world, the objects are the agent and any dirt. In the simple two-cell version, the agent can be in either of the two cells, and each cell can either contain dirt or not, so there are `2 · 2 · 2 = 8` states (see [Figure 3.2](#Chapter03-02.xhtml#fig3-2)). In general, a vacuum environment with `n` cells has `n · 2^n` states.

**Initial state:** Any state can be designated as the initial state.

**Actions:** In the two-cell world we defined three actions: `Suck`, `Left`, and `Right`. In a two-dimensional multi-cell world we need more movement actions. We could add `Upward` and `Downward`, giving us four absolute movement actions, or we could switch to egocentric actions, defined relative to the viewpoint of the agent—for example, `Forward`, `Backward`, `TurnRight`, and `TurnLeft`.

**Transition model:** `Suck` removes any dirt from the agent’s cell; `Forward` moves the agent ahead one cell in the direction it is facing, unless it hits a wall, in which case the action has no effect. `Backward` moves the agent in the opposite direction, while `TurnRight` and `TurnLeft` change the direction it is facing by `90°`.

**Goal states:** The states in which every cell is clean.

**Action cost:** Each action costs `1`.

Description
A square labeled Start state has three rows and three columns. Row 1: Column 1, 7. Column 2, 2. Column 3, 4. Row 2: Column 1, 5. Column 2, blank. Column 3, 6. Row 3: Column 1, 8. Column 2, 3. Column 3, 1. Another square labeled Goal state has three rows and three columns. Row 1: Column 1, blank. Column 2, 1. Column 3, 2. Row 2: Column 1, 3. Column 2, 4. Column 3, 5. Row 3: Column 1, 6. Column 2, 7. Column 3, 8.

×![](images/Fig-21.jpg)

Figure 3.2 The state-space graph for the two-cell vacuum world. There are 8 states and three actions for each state: `L` = `Left`, `R` = `Right`, `S` = `Suck`.

## Sokoban Puzzle

Another type of grid world is the sokoban puzzle, in which the agent’s goal is to push a number of boxes, scattered about the grid, to designated storage locations. There can be at most one box per cell. When an agent moves forward into a cell containing a box and there is an empty cell on the other side of the box, then both the box and the agent move forward.

Sokoban puzzle

The agent can’t push a box into another box or a wall. For a world with `n` non-obstacle cells and `b` boxes, there are `n × n!/(b!(n – b)!)` states; for example on an `8 × 8` grid with a dozen boxes, there are over 200 trillion states.

## Sliding-tile Puzzle

In a sliding-tile puzzle, a number of tiles (sometimes called blocks or pieces) are arranged in a grid with one or more blank spaces so that some of the tiles can slide into the blank space. One variant is the Rush Hour puzzle, in which cars and trucks slide around a `6 × 6` grid in an attempt to free a car from the traffic jam. Perhaps the best-known variant is the 8-puzzle (see [Figure 3.3](#Chapter03-02.xhtml#fig3-3)), which consists of a `3 × 3` grid with eight numbered tiles and one blank space, and the 15-puzzle on a `4 × 4` grid. The object is to reach a specified goal state, such as the one shown on the right of the figure. The standard formulation of the 8 puzzle is as follows:

Sliding-tile puzzle
8-puzzle
15-puzzle

Description
Two squares with a common vertical side represent a state. Each square represents a cell. Eight states are arranged in three rows. Th top row contains two states, the middle row contains four states, and the bottom row contains two states. The first state of the top row has a vacuum cleaner and dirt in the left cell and dirt in the right cell. The second state of the top row has dirt in the left cell and a vacuum cleaner and dirt in the right cell. An arrow labeled L from the left cell of the first state loops back to the same cell. An arrow labeled R from the right cell of the first state points to the left cell of the second state. An arrow labeled L from the left cell of the second state points to the right cell of the first state. An arrow labeled R from the right cell of the second state loops back to the same cell. An arrow labeled S from the first state in the top row points to the first state in the middle row. The first state in the middle row has a vacuum cleaner in the left cell and dirt in the right cell. An arrow labeled L from the left cell of the first state loops back to the same cell. An arrow labeled S from the left cell of the first state points to the right cell of the same state. The second state in the middle row has an empty left cell and a vacuum cleaner and dirt in the right cell. An arrow labeled R from the right cell of the second state loops back to the same cell. An arrow labeled R from the right cell of the first state points to the left cell of the second state. An arrow labeled L from the left cell of the second state points to the right cell of the first state. The third state in the middle row has a vacuum cleaner and dirt in the left cell and an empty right cell. An arrow labeled L from the left cell of the third state loops back to the same cell. The fourth state in the middle row has dirt in the left cell and a vacuum cleaner in the right cell. An arrow labeled R from the right cell of the fourth state loops back to the same cell. An arrow labeled S from the left cell of the fourth state points to the right cell of the same state. An arrow labeled R from the right cell of the third state points to the left cell of the fourth state. An arrow labeled L from the left cell of the fourth state points to the right cell of the third state. An arrow labeled S from the second state in the top row points to the fourth state in the middle row. An arrow from the third state in the middle row points to the first state of the bottom row. The first state on the bottom row has a vacuum cleaner in the left cell and an empty right cell. An arrow labeled L from the left cell of the first state loops back to the same cell. An arrow labeled S from the left cell of the first state points to the right cell of the same state. The second state in the bottom row has an empty left cell and a vacuum cleaner in the right cell. An arrow labeled R from the right cell of the second state loops back to the same cell. An arrow labeled S from the left cell of the second state points to the right cell of the same state. An arrow labeled R from the right cell of the first state points to the left cell of the second state. An arrow labeled L from the left cell of the second state points to the right cell of the first state. An arrow labeled S from the second state in the middle row points to the second state in the third row.

×![](images/Fig-22.jpg)

Figure 3.3 A typical instance of the 8-puzzle.

**States:** A state description specifies the location of each of the tiles.

**Initial state:** Any state can be designated as the initial state. Note that a parity property partitions the state space—any given goal can be reached from exactly half of the possible initial states (see Exercise 3.PART).

**Actions:** While in the physical world it is a tile that slides, the simplest way of describing an action is to think of the blank space moving `Left`, `Right`, `Up`, or `Down`. If the blank is at an edge or corner then not all actions will be applicable.
