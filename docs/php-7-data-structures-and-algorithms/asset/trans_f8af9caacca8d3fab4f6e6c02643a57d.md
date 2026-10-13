

# 回溯算法解决谜题问题

回溯是一种递归算法策略，当未找到结果时我们进行回溯，并继续在其他可能的路径中搜索解决方案。回溯是解决许多著名问题的流行方法，特别是国际象棋、数独、填字游戏等。由于递归是回溯的关键组件，我们需要确保问题可以划分为子问题，并将递归应用于这些子问题。在本节中，我们将使用回溯算法解决最流行的游戏之一——数独。

## 序列比对算法

```php
function printSequence($grid, $s1, $s2, $j, $i) { 

    $sq1 = []; 

    $sq2 = []; 

    $sq3 = []; 



    do { 

        $t = $grid[$i - 1][$j]; 
        $d = $grid[$i - 1][$j - 1]; 
        $l = $grid[$i][$j - 1]; 
        $max = max($t, $d, $l); 



        switch ($max) { 

            case $d: 
                $j--; 
                $i--; 
                array_push($sq1, $s1[$j]); 
                array_push($sq2, $s2[$i]); 
                if ($s1[$j] == $s2[$i]) 
                    array_push($sq3, "|"); 
                else 
                    array_push($sq3, " "); 
                break; 



            case $t: 
                $i--; 
                array_push($sq1, GC); 
                array_push($sq2, $s2[$i]); 
                array_push($sq3, " "); 
                break; 



            case $l: 
                $j--; 
                array_push($sq1, $s1[$j]); 
                array_push($sq2, GC); 
                array_push($sq3, " "); 
                break; 

        } 
    } while ($i > 0 && $j > 0); 



    echo implode("", array_reverse($sq1)) . "\n"; 
    echo implode("", array_reverse($sq3)) . "\n"; 
    echo implode("", array_reverse($sq2)) . "\n"; 
} 
```

由于我们是从后向前逐步移动，因此使用 `array_push` 来保持比对顺序。然后，我们通过反转数组来打印它。该算法的复杂度为 `O(M * N)`。如果我们为两个字符串 `$X` 和 `$Y` 调用 `NWSquencing`，输出如下：

```
G-AATTCAGTTA

| | | | |  |

GGA-T-C-G--A
```

## 数独求解器实现

在数独中，我们有一个部分填充的盒子，包含大小为 3x3 的小宫格。游戏规则是在每个单元格中放置数字 1 到 9，其中相同的数字不能出现在同一行或同一列中。因此，在 9x9 的网格中，每个数字 1 到 9 在每行和每列中只会出现一次：

|   |   | 7 |   | 3 |   | 8 |   |   |
|---|---|---|---|---|---|---|---|---|
|   |   |   | 2 |   | 5 |   |   |   |
| 4 |   |   | 9 |   | 6 |   |   | 1 |
|   | 4 | 3 |   |   |   | 2 | 1 |   |
| 1 |   |   |   |   |   |   |   | 5 |
|   | 5 | 8 |   |   |   | 6 | 7 |   |
| 5 |   |   | 1 |   | 8 |   |   | 9 |
|   |   |   | 5 |   | 3 |   |   |   |
|   |   | 2 |   | 9 |   | 5 |   |   |

例如，在前面的数独棋盘中，第一列有 4、1、5，第一行有 7、3、8。因此，我们不能在左上角的第一个空单元格中使用这六个数字中的任何一个。所以，可能的数字可以是 2、6 和 9。我们不知道这三个数字中的哪一个能满足解决方案。我们可以选其中两个放入第一个单元格，然后开始寻找剩余空单元格的值。这将持续进行，直到所有单元格都填满，或者仍有办法在不违反游戏原则的情况下在空单元格中放置数字。如果无解，我们将回溯并回到 2，将其替换为下一个可能的选项 6，并以相同的递归方式为其他空单元格寻找数字。这将持续直到棋盘被解开。让我们编写一些递归代码来解决数独：

### 辅助函数

```php
define("N", 9); 
define("UNASSIGNED", 0); 



function FindUnassignedLocation(array &$grid, int &$row, int &$col): bool { 
    for ($row = 0; $row < N; $row++) 
        for ($col = 0; $col < N; $col++) 
            if ($grid[$row][$col] == UNASSIGNED) 
                return true; 
    return false; 
} 



function UsedInRow(array &$grid, int $row, int $num): bool { 
    return in_array($num, $grid[$row]); 
} 



function UsedInColumn(array &$grid, int $col, int $num): bool { 
    return in_array($num, array_column($grid, $col)); 
} 



function UsedInBox(array &$grid, int $boxStartRow, int $boxStartCol, int $num): bool { 
    for ($row = 0; $row < 3; $row++) 
        for ($col = 0; $col < 3; $col++) 
            if ($grid[$row + $boxStartRow][$col + $boxStartCol] == $num) 
                return true; 
    return false; 
} 



function isSafe(array $grid, int $row, int $col, int $num): bool { 
    return !UsedInRow($grid, $row, $num) && 
        !UsedInColumn($grid, $col, $num) && 
        !UsedInBox($grid, $row - $row % 3, $col - $col % 3, $num); 
} 
```

在这里，我们可以看到实现 `Sudoku` 函数所需的所有辅助函数。首先，我们定义了网格的最大尺寸以及未分配单元格的指示符，在本例中为 0。第一个函数用于在 9 x 9 网格中查找任意未分配的位置，从左上角的单元格开始，按行搜索空单元格。然后，我们有三个函数来检查某个数字是否已在特定行、列或 3 x 3 宫格中使用。如果该数字未在行、列或宫格中使用，我们就可以将其用作单元格的可能值，这就是为什么在 `isSafe` 函数检查中返回 true 的原因。如果在其中任一位置已被使用，该函数将返回 false。现在，我们准备好实现用于解决数独的递归函数了：

### 递归求解器

```php
function SolveSudoku(array &$grid): bool { 
    $row = $col = 0; 



    if (!FindUnassignedLocation($grid, $row, $col)) 
        return true; // 成功！没有空位 



    for ($num = 1; $num <= N; $num++) { 
        if (isSafe($grid, $row, $col, $num)) { 
            $grid[$row][$col] = $num; // 进行赋值 



            if (SolveSudoku($grid)) 
                return true;  // 如果成功则返回 



            $grid[$row][$col] = UNASSIGNED;  // 失败 
        } 
    } 
    return false; // 触发回溯 
} 



function printGrid(array $grid) { 
    foreach ($grid as $row) { 
        echo implode("", $row) . "\n"; 
    } 
}
```

`SolveSudoku` 函数不言自明。在这里，我们访问一个单元格，如果该单元格为空，则在单元格中放入一个临时数字（1 到 9 中的任意数字）。然后，我们检查该数字是否在行、列或 3 x 3 矩阵中重复。如果不冲突，我们保留该数字在单元格中，并移动到下一个空单元格。我们通过递归来实现这一点，以便在发生冲突时可以回溯并更改值。这将持续直到找到解决方案。我们还添加了一个 `printGrid` 函数，用于在命令行中打印给定的网格。现在让我们使用本示例中使用的样本数独矩阵运行代码：

### 执行示例

```php
$grid = [ 
    [0, 0, 7, 0, 3, 0, 8, 0, 0], 
    [0, 0, 0, 2, 0, 5, 0, 0, 0], 
    [4, 0, 0, 9, 0, 6, 0, 0, 1], 
    [0, 4, 3, 0, 0, 0, 2, 1, 0], 
    [1, 0, 0, 0, 0, 0, 0, 0, 5], 
    [0, 5, 8, 0, 0, 0, 6, 7, 0], 
    [5, 0, 0, 1, 0, 8, 0, 0, 9], 
    [0, 0, 0, 5, 0, 3, 0, 0, 0], 
    [0, 0, 2, 0, 9, 0, 5, 0, 0] 
]; 



if (SolveSudoku($grid) == true) 
    printGrid($grid); 
else 
    echo "No solution exists"; 
```

我们使用二维数组来表示数独矩阵。如果运行代码，它将在命令行中产生以下输出：

```
297431856
361285497
485976321
743659218
126847935
958312674
534128769
879563142
612794583
```

或者，如果我们以漂亮的数独矩阵形式呈现，它将如下所示：

| 2 | 9 | 7 | 4 | 3 | 1 | 8 | 5 | 6 |
|---|---|---|---|---|---|---|---|---|
| 3 | 6 | 1 | 2 | 8 | 5 | 4 | 9 | 7 |
| 4 | 8 | 5 | 9 | 7 | 6 | 3 | 2 | 1 |
| 7 | 4 | 3 | 6 | 5 | 9 | 2 | 1 | 8 |
| 1 | 2 | 6 | 8 | 4 | 7 | 9 | 3 | 5 |
| 9 | 5 | 8 | 3 | 1 | 2 | 6 | 7 | 4 |
| 5 | 3 | 4 | 1 | 2 | 8 | 7 | 6 | 9 |
| 8 | 7 | 9 | 5 | 6 | 3 | 1 | 4 | 2 |
| 6 | 1 | 2 | 7 | 9 | 4 | 5 | 8 | 3 |

