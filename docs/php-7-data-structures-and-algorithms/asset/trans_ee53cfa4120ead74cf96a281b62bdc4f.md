
# 理解动态规划

## 速度放大算法

```php
function velocityMagnifier(array $jobs) {
    $n = count($jobs);

    usort($jobs, function($opt1, $opt2) {
        return $opt1['velocity'] < $opt2['velocity'];
    });

    $dMax = max(array_column($jobs, "deadline"));

    $slot = array_fill(1, $dMax, -1);
    $filledTimeSlot = 0;

    for ($i = 0; $i < $n; $i++) {
        $k = min($dMax, $jobs[$i]['deadline']);
        while ($k >= 1) {
            if ($slot[$k] == -1) {
                $slot[$k] = $i;
                $filledTimeSlot++;
                break;
            }
            $k--;
        }

        if ($filledTimeSlot == $dMax) {
            break;
        }
    }

    echo("Stories to Complete: ");
    for ($i = 1; $i <= $dMax; $i++) {
        echo $jobs[$slot[$i]]['id'];

        if ($i < $dMax) {
            echo "\t";
        }
    }

    $maxVelocity = 0;
    for ($i = 1; $i <= $dMax; $i++) {
        $maxVelocity += $jobs[$slot[$i]]['velocity'];
    }
    echo "\nMax Velocity: " . $maxVelocity;
}
```

在这里，我们获取作业列表（用户故事 ID、截止日期和速度），用于寻找最大速度及其对应的用户故事 ID。首先，我们使用自定义用户排序函数 `usort()` 对 `jobs` 数组进行排序，并根据速度以降序排列数组。之后，我们从截止日期列计算可用的最大时隙数量。然后我们将 `slot` 数组初始化为 `-1`，以此作为已用时隙的标记。下一个代码块遍历每个用户故事，为其寻找一个合适的时隙。如果可用时隙已填满，我们不再继续。现在，让我们使用以下代码块运行这段代码：

```php
$jobs = [
    ["id" => "S1", "deadline" => 2, "velocity" => 95],
    ["id" => "S2", "deadline" => 1, "velocity" => 32],
    ["id" => "S3", "deadline" => 2, "velocity" => 47],
    ["id" => "S4", "deadline" => 1, "velocity" => 42],
    ["id" => "S5", "deadline" => 3, "velocity" => 28],
    ["id" => "S6", "deadline" => 4, "velocity" => 64]
];

velocityMagnifier($jobs);
```

这将在命令行中产生以下输出：

```
Stories to Complete: S3    S1    S5    S6

Max Velocity: 234
```

贪心算法有助于解决局部最优问题，例如作业调度、网络流量控制、图算法等。然而，要获得全局最优解，我们需要关注算法的另一个方面，即**动态规划**。

---

## 读累了记得休息一会哦~

**公众号：古德猫宁李**

*   电子书搜索下载
*   书单分享
*   书友学习交流

**网站：** [沉金书屋 https://www.chenjin5.com](https://www.chenjin5.com)

*   电子书搜索下载
*   电子书打包资源分享
*   学习资源分享

---

# 理解动态规划

动态规划是一种通过将复杂问题分解为较小的子问题并求解这些子问题来解决复杂问题的方法。我们累积子问题的解以找到全局解。动态规划的优点在于，我们通过存储子问题的结果来减少子问题的重复计算。动态规划是一种非常著名的优化方法。动态算法的应用遍布编程世界的各个角落。动态规划可以解决诸如找零钱、寻找最长公共子序列、寻找最长递增子序列、DNA 字符串排序等问题。贪心算法与动态规划的核心区别在于，动态规划始终倾向于**全局最优解**。

如果一个问题具有**最优子结构**或**重叠子问题**，我们就可以用动态规划来解决它。最优子结构意味着实际问题的最优解可以通过其子问题的最优解的组合来求得。换句话说，如果一个问题对于规模 `n` 是最优的，那么它对于任何小于 `n` 或大于 `n` 的规模也是最优的。重叠子问题表明较小的子问题会被反复求解，因为它们相互重叠。斐波那契数列是重叠子问题的一个绝佳例子。因此，在此处使用基本递归毫无帮助。动态规划对每个子问题仅求解一次，不再尝试进一步求解。这可以通过**自顶向下**方法或**自底向上**方法来实现。

在自顶向下方法中，我们从较大的问题开始，递归地求解较小的子问题。然而，我们必须使用**备忘录**技术来存储子问题的结果，以免将来重复计算该子问题。在自底向上方法中，我们首先求解最小的子问题，然后转向其他较小的子问题。通常，自底向上方法使用多维数组以表格形式存储子问题的结果。

现在，我们将探索动态规划世界中的一些示例。其中一些可能听起来非常熟悉，源自我们日常的编程问题。我们将从著名的背包问题开始。

## 0-1 背包问题

背包是一种带肩带的袋子，通常由士兵携带，以便在旅途中携带必需品或贵重物品。每个物品都有其价值和确定的重量。因此，士兵必须在其最大承重限制内挑选最有价值的物品，因为他们无法将所有东西都装进包里。术语 `0/1` 意味着我们要么拿走该物品，要么留下它。我们不能部分拿取物品。这被称为著名的 0-1 背包问题。我们将采用自底向上方法来解决 0-1 背包问题。以下是解决方案的伪代码：

```
Procedure knapsack(n, W, w1,...,wN, v1,...,vN)

for w = 0 to W
    M[0, w] = 0

for i = 1 to n
    for w = 0 to W
        if wi > w :
            M[i, w] = M[i-1, w]
        else :
            M[i, w] = max(M[i-1, w], vi + M[i-1, w-wi])

return M[n, W]

end procedure
```

例如，如果我们有五个物品 `[1,2,3,4,5]`，它们的重量分别为 10、20、30、40、50，最大允许重量为 10，使用自底向上方法将产生以下表格：

![Image00091.jpg](Image00091.jpg)

正如我们所见，我们自底向上地构建表格，从一个物品和一个重量开始，逐渐增加到我们期望的重量，并通过选择最佳物品来最大化价值总数。最后，右下角的最后一个单元格就是 0-1 背包问题的预期结果。以下是实现代码及运行函数的代码：

```php
function knapSack(int $maxWeight, array $weights, array $values, int $n) {
    $DP = [];
    for ($i = 0; $i <= $n; $i++) {
        for ($w = 0; $w <= $maxWeight; $w++) {
            if ($i == 0 || $w == 0)
                $DP[$i][$w] = 0;
            else if ($weights[$i - 1] <= $w)
                $DP[$i][$w] = max($values[$i-1] + $DP[$i - 1][$w - $weights[$i-1]], $DP[$i - 1][$w]);
            else
                $DP[$i][$w] = $DP[$i - 1][$w];
        }
    }
    return $DP[$n][$maxWeight];
}

$values = [10, 20, 30, 40, 50];
$weights = [1, 2, 3, 4, 5];
$maxWeight = 10;
$n = count($values);
echo knapSack($maxWeight, $weights, $values, $n);
```

这将在命令行中显示 `100`，这与前面表格中的预期结果相符。该算法的复杂度为 `O(n * W)`，其中 `n` 是物品数量，`W` 是目标重量。

## 寻找最长公共子序列 (LCS)
