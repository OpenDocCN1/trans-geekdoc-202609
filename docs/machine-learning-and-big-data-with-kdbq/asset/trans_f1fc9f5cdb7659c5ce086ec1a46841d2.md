

# 树 489

```
enlist[r],$98<h>type r::quant.trees.growTree[xy;r] raze @[rr;
  where 99h=type each r;enlist];rr
]}each r::quant.trees.chooseSplit[xy;treeinput]
```

我们可以学习一棵树：对于初始划分中的每条记录，我们迭代到纯节点（叶子节点）或达到指定的最大深度（`maxdepth` 键）。当我们到达叶子节点时，返回一个扁平化的结果，然后对下一个划分记录进行递归，直到没有剩余记录为止。扁平化的树应包含所有路径以及一个带有所有索引 $i$ 的父节点的树状结构。提供的函数作为输入，包含预测器的索引、它的索引 $i$ 和 $j$、增益（gain）以及四个传递的四个参数：

```
-quant.trees.learnTree[:params]
// 用于学习树的参数字典
// m 随机选择的特征数量，默认为所有特征
// maxdepth 树的最大深度，如果未达到纯节点，默认
// 100
params[m]: [$m in key params;m;count params`]
params[maxdepth]: [$maxdepth in key params;params`maxdepth;100];
r0: ofinfoains xij`jofain bitmap`X appliedrule`rulepath
classes`m`maxdepth
params,
infoains xij`jofain bitmap`appliedrule`rulepath(!(();ON;0N;0n
  ;count [params`y]wB;::(());));
tree: enlist[r0];
[$98<>type r::quant.trees.growTree;r0:dc`x`y`classes`m
  maxdepth`r
raze @[r,99h=type each r;enlist];
r;
tree: update p:(x'-_l) rulepath from tree;
  :'ip`path xcols update path:(x scan)each till x}p,i:i from tree;
);
```

现在我们将为拟合（或学习）树树所需的参数创建一个字典：

```
dataset!();
daset[x]:value flip delete from iris;
daset[y]:[distinct[x?] iris[`class];
params:dataset,`rule classes!(asc distinct dataset`y);
```

查看您的特征：

```
flip params`x
```

```
5.1 3.5 1.4 0.2
4.9 3 1.4 0.2
4.7 3.2 1.3 0.2
4.6 3.1 1.5 0.2
5 3.6 1.4 0.2
5.4 3.9 1.7 0.4
5 3.4 1.5 0.2
4.4 2.9 1.4 0.2
```

# 490

# 机器学习

```
4.9 3.1 1.5 0.1
5.4 3.7 1.5 0.2
4.8 3.4 1.6 0.2
4.8 3 1.4 0.1
4.3 1.1 0.1
5.8 4 1.2 0.2
5.7 4.4 1.5 0.4
..
```

以及我们预测变量的分类：

```
distinct params`y

0 1 2
```

并以表格形式可视化：

```
flip @[`x`y`params;x;flip]`
```

| x | y |
|---|---|
| 5.1 3.5 1.4 0.2 | |
| 4.9 | 1.4 0.2 | |
| 4.7 3.2 1.3 0.2 | |
| 4.6 3.1 1.5 0.2 | |
| 5 3.6 1.4 0.2 | |
| 5.4 3.9 1.7 0.4 | |
| 5 3.4 1.5 0.2 | |
| 4.4 2.9 1.4 0.2 | |

| 4.9 3.1 1.5 0.1 | |
| 5.4 3.7 1.5 0.2 | |
| 4.8 3.4 1.6 0.2 | |
| 4.8 3 1.4 0.1 | |
| 4.3 1.1 0.1 | |
| 5.8 4 1.2 0.2 | |
| 5.7 4.4 1.5 0.4 | |
..

当我们**生长 (learn)** 一棵树时，我们可以看到返回的 `tree`包含了 `params`，这些是探索每个节点非常有用的中间步骤：

# 492 机器学习

我们可以返回一个只包含叶子节点的子树 $T'$：

```
quant.trees.leaves:[[tree
// tree decision tree
// select from tree where i in til[count p]except p
};
```

其中 $p$ 是该节点的父节点，我们选择所有不是父节点的节点：

```
quant.trees.leaves
```

| i p path | infogains |
|---|---|---|
| | xi | infogain bitma.. |
| 1 0 1 0 | *s0* 0 1 2 3.10.557327 0.267914 0.9182958 0.9182958 2 |
| 5 4 5 32 0 | *s0* 0 1 2 3.10.444276 0.0378185 0.234482 0.146043 3 |
| 6 4 6 3 2 0 | *s0* 0 1 2 3.10.444276 0.0378185 0.234482 0.146043 3 |
| 8 7 7 3 2 0 | *s0* 0 1 2 3.10.191703 0.252692 0.252692 0.459147 3 |
| 10 9 7 3 2 0 | *s0* 0 1 2 3.10.918298 0.252692 0.9182958 0.252692 3 |
| 11 9 7 3 2 0 | *s0* 0 1 2 3.10.918298 0.252692 0.9182958 0.252692 3 |
| 14 13 14 13 2 0 | *s0* 0 1 2 3.10.918298 0.252692 0.9182958 0.252692 3 |
| 15 13 15 12 2 0 | *s0* 0 1 2 3.10.918298 0.252692 0.9182958 0.252692 3 |
| 16 12 16 12 2 0 0 | |

我们可以检查 `tree` 的字段，例如带有关联规则的完整规则路径：

```
select i,p,path,xi,j,rule from tree
x path xi j
-- --
0 0 ()
1 0 1 2 .9
2 0 2 .9
3 2 0 .7
4 4 3 2 .9
5 4 3 2 .6
6 4 3 2 .6
7 7 3 2 .9
8 7 3 2 .5
9 7 3 2 .5
10 9 7 3 2 .6
11 9 7 3 2 .6
12 12 2 0 0 .7
13 13 12 2 0 0 .8
14 13 12 2 0 0 .9
15 13 15 12 2 0 0 .0
16 12 16 12 2 0
```quant.trees.learn

meta tree

| c | t a |
|---|---|
| i | |
| p | |
| path | |

infogains | xi
infogain | f
bitmap | appliedrule
rulepath

