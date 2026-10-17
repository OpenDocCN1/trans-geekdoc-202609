
更强的传播形式可以通过 `k`‑consistency 的概念来定义。若一个约束满足条件：对于任意 `k`−1 个变量以及对这些变量的任何一致赋值，则可以为第 `k` 个变量赋予一致值，则该约束满足 `k`‑consistency。1‑consistency 表示，给定空集合时，任何单个变量都可以使其取值域一致——这正是我们所说的节点一致性。2‑consistency 与弧一致性等价。对于二元约束网络，3‑consistency 等价于路径一致性。

---

### K-CONSISTENCY

---

若一个约束满足 `k`‑consistency 并且同时满足从 `k`‑1 到 1 的所有层次一致性，则称其为**强** `k`‑consistent。假设我们有一个包含 `n` 个节点的约束满足度（CSP），并使其达到强 `n`‑consistency（即 `k` = `n` 的强一致性），则可以按以下步骤求解：首先为 `X`[1] 选取一个一致的值。由于图是 2‑consistent，我们可以保证能为 `X`[2] 选取一致的值；因为是 3‑consistent，所以可以为 `X`[3] 选取一致的值，以此类推。对于每个变量 `X`[i]，只需在其取值域中遍历 `d` 个值，找到与 `X`[1]…`X`[*i*−1] 一致的值。我们保证在时间复杂度 `O`(`n`²`d`) 内找到解。显然，这并非免费午餐：任何用于建立 `n`‑consistency 的算法在最坏情况下的时间复杂度都是指数级的。更糟的是，`n`‑consistency 还要求指数级的空间复杂度。记忆问题甚至比时间问题更为严重。实际上，确定适当的一致性检查层级大多是经验性的科学。可以指出，实践中通常计算 2‑consistency，较少计算 3‑consistency。

---

### STRONGLY K-CONSISTENT

---

#### 6.2.5 Global constraints

请记住，**全局约束**是指涉及任意数量变量（但不一定是所有变量）的约束。全局约束在实际问题中非常常见，可以通过专门的算法处理，这些算法比前面描述的通用方法更高效。例如，`Alldiff` 约束要求涉及的所有变量取不同的值（如上文的字谜问题和数独拼图）。`Alldiff` 简单的不满足检测方法如下：如果约束中涉及 `m` 个变量，而它们总共只有 `n` 种可能的不同取值，且 `m` > `n`，则该约束不可满足。

基于此，我们可以采用如下简单的检测算法：首先删除约束中所有取值为 singleton（单元）的变量，并从其余变量的取值域中删除该值；重复此过程，直到不再出现 singleton 变量。若在任何阶段出现空域或剩余变量数超过可用域值数，则检测到不满足情况。

该方法可以检测到在赋值 {`WA` = `red`，`NSW` = `red`} 时的不满足（参见 Figure 6.1）。注意，`SA`、`NT`、`Q` 这三个变量实际上通过 `Alldiff` 约束相互关联，因为每对变量必须颜色不同。在部分赋值后，对 AC-3 进行传播后，每个变量的取值域被缩小到 {`green`, `blue`}。于是，三个变量只有两种颜色可选，导致 `Alldiff` 约束被违反。由此可见，针对高阶约束的简单一致性检测有时比对等价的二元约束集应用弧一致性更有效。更复杂的 `Alldiff` 推理算法（见 van Hoeve 和 Katriel, 2006）能够传播更多约束，但相应地计算成本更高。

另一个重要的高阶约束是**资源约束**（有时称为 atmost 约束）。例如，在调度问题中，令 `P`[1]…`P`[4] 表示分配到四个任务的资源数量。约束“总资源数不超过 10 人”可写作 `Atmost`(10, `P`[1], `P`[2], `P`[3], `P`[4])。我们可以通过检查当前取值域的最小值之和来快速发现不满足情况：例如，若每个变量的取值域为 {3, 4, 5, 6}，则 `Atmost` 约束无法满足。我们也可以通过删除不符合其他变量最小值的最大值来强制一致性：若每个变量的取值域为 {2, 3, 4, 5, 6}，则可以从每个域中删除 5 和 6。

---

### RESOURCE CONSTRAINT

---

对于大规模受限于整数值的问题（如需要在数百辆车中调度数千人），通常无法把每个变量的取值域表示为大集合并通过一致性检查逐步缩小。取而代之的是使用**域的上下界传播**（bounds propagation）。例如，在航空调度问题中，假设有两趟航班 `F`[1] 和 `F`[2]，其飞机容量分别为 165 和 385。初始的乘客数量取值域如下：

> ![equ](img/00153.jpg)

---

### BOUNDS PROPAGATION

---

现在假设还有一个约束：两趟航班合计必须携带 420 人，即 `F`[1] + `F`[2] = 420。通过传播边界约束，我们可以将取值域缩小到：

> ![equ](img/00154.jpg)

---

### BOUNDS CONSISTENT

---

## 6.2.6 Sudoku example

The popular `Sudoku` puzzle has introduced millions of people to constraint satisfaction problems, although they may not recognize it. A Sudoku board consists of 81 squares, some of which are initially filled with digits from 1 to 9. The puzzle is to fill in all the remaining squares such that no digit appears twice in any row, column, or 3 × 3 box (see Figure 6.4). A row, column, or box is called a `unit`.

The Sudoku puzzles that are printed in newspapers and puzzle books have the property that there is exactly one solution. Although some can be tricky to solve by hand, taking tens of minutes, even the hardest Sudoku problems yield to a CSP solver in less than 0.1 second.

A Sudoku puzzle can be considered a CSP with 81 variables, one for each square. We use the variable names `A1` through `A9` for the top row (left to right), down to `I1` through `I9` for the bottom row. The empty squares have the domain {1, 2, 3, 4, 5, 6, 7, 8, 9} and the prefilled squares have a domain consisting of a single value. In addition, there are 27 different

> ![image](img/00155.jpg)

> **Figure 6.4** (a) A Sudoku puzzle and (b) its solution.

`Alldiff` constraints: one for each row, column, and box of 9 squares.

> ![equ](img/00156.jpg)

Let us see how far arc consistency can take us. Assume that the `Alldiff` constraints have been expanded into binary constraints (such as `A1` ≠ `A2`) so that we can apply the AC-3 algorithm directly. Consider variable `E6` from Figure 6.4(a)—the empty square between the 2 and the 8 in the middle box. From the constraints in the box, we can remove not only 2 and 8 but also 1 and 7 from `E6`’s domain. From the constraints in its column, we can eliminate 5, 6, 2, 8, 9, and 3. That leaves `E6` with a domain of {4}; in other words, we know the answer for `E6`. Now consider variable `I6`—the square in the bottom middle box surrounded by 1, 3, and 3. Applying arc consistency in its column, we eliminate 5, 6, 2, 4 (since we now know `E6` must be 4), 8, 9, and 3. We eliminate 1 by arc consistency with `I5`, and we are left with only the value 7 in the domain of `I6`. Now there are 8 known values in column 6, so arc consistency can infer that `A6` must be 1. Inference continues along these lines, and eventually, AC-3 can solve the entire puzzle—all the variables have their domains reduced to a single value, as shown in Figure 6.4(b).

Of course, Sudoku would soon lose its appeal if every puzzle could be solved by a mechanical application of AC-3, and indeed AC-3 works only for the easiest Sudoku puzzles. Slightly harder ones can be solved by PC-2, but at a greater computational cost: there are 255,960 different path constraints to consider in a Sudoku puzzle. To solve the hardest puzzles and to make efficient progress, we will have to be more clever.

Indeed, the appeal of Sudoku puzzles for the human solver is the need to be resourceful in applying more complex inference strategies. Aficionados give them colorful names, such as “naked triples.” That strategy works as follows: in any unit (row, column or box), find three squares that each have a domain that contains the same three numbers or a subset of those numbers. For example, the three domains might be {1, 8}, {3, 8}, and {1, 3, 8}. From that we don’t know which square contains 1, 3, or 8, but we do know that the three numbers must be distributed among the three squares. Therefore we can remove 1, 3, and 8 from the domains of every *other* square in the unit.

It is interesting to note how far we can go without saying much that is specific to Sudoku. We do of course have to say that there are 81 variables, that their domains are the digits 1 to 9, and that there are 27 `Alldiff` constraints. But beyond that, all the strategies—arc consistency, path consistency, etc.—apply generally to all CSPs, not just to Sudoku problems. Even naked triples is really a strategy for enforcing consistency of `Alldiff` constraints and has nothing to do with Sudoku *per se*. This is the power of the CSP formalism: for each new problem area, we only need to define the problem in terms of constraints; then the general constraint-solving mechanisms can take over.

### 6.3 BACKTRACKING SEARCH FOR CSPS

Sudoku problems are designed to be solved by inference over constraints. But many other CSPs cannot be solved by inference alone; there comes a time when we must search for a solution. In this section we look at backtracking search algorithms that work on partial assignments; in the next section we look at local search algorithms over complete assignments.

We could apply a standard depth-limited search (from Chapter 3). A state would be a partial assignment, and an action would be adding `var = value` to the assignment. But for a CSP with `n` variables of domain size `d`, we quickly notice something terrible: the branching factor at the top level is `n*d` because any of `d` values can be assigned to any of `n` variables. At the next level, the branching factor is `(n - 1)*d`, and so on for `n` levels. We generate a tree with `n! * d^n` leaves, even though there are only `d^n` possible complete assignments!
