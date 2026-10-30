```
0 1 2
3 4 5
6 7 8
>>>
```

If you want to store these data for later use, you can represent the grid with a list structure. The following session places the data in a list and then outputs them in two-dimensional grid format:

```
>>> grid = list(range(9))
>>> index = 0
>>> for row in range(3):
    for column in range(3):
        print(grid[index], end = " ")
        index = index + 1
    print()
```

```
0 1 2
3 4 5
6 7 8
>>>
```

If it seems odd to model a two-dimensional structure with a linear structure like a list, you can define your own Grid class to represent a grid more directly. You access each datum in this structure by providing two index values: one for the row and one for the column. Unlike the coordinate system of turtle graphics, the position (0, 0) locates the datum in the upper-left corner of this structure. Thus, the datum in row 1, column 2 is at position (1, 2). The row index gets larger as you move down in the grid, and the column index gets larger as you move to the right.

The next session assumes that such a class is available in the grid module. You create a Grid object with the required numbers of rows and columns, and then you can load this object with data and print its contents:

```
>>> from grid import Grid
>>> datum = 0
>>> gryd = Grid(3, 3)      # Create a 3 by 3 Grid object
>>> for row in range(3):
    for column in range(3):
        gryd[row][column] = datum
        datum = datum + 1
```