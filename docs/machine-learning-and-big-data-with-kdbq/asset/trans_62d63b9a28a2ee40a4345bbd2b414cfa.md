

# 通向 AI - 蒙特卡洛树搜索

```python
.quantQ.mcts.runMCTS[:bucket]
// 决定先走一步还是对抗
$0=count[`treeMCTS`]
// 随机结束游戏

```
bucketTMP:(quantQ.mcts.oneTurnRun)/([{=x`isWinner`];`moveState
    ->isWinner)
    (bucket[`movesState`]);0)
tabTMP:bucket[`treeMCTS`]:tDTMP(`index:1);gameTree: enlist enlist
    bucketTMP[`movesState`]
    [count[`movesState`];isWinner:bucketTMP[`isWinner`)]];
// 继续构建树
```

// 创建本地 bucket 并添加特征
bucketTMP:
// indexInTree 定义了游戏的哪部分存储在 bucket 中
bucketTMP(`indexInTree`):0;
// treeDepth 计数本地迭代，用于在
// 遍历现有树时跟踪
bucketTMP(`treeDepthCounter`):0;
// isWinner 决定局部胜者
bucketTMP[`isWinner`]:0);

```python
// 运行 MCTS
bucketTMP:(quantQ.mcts.oneTurnRun)/([{=x`isWinner`]);bucketTMP
    :);
1+bucketTMP[`indexInTree`]);
```

```python
// 为更新后的游戏树提取变量
newGameTree:(count[bucket[`movesState`]])_bucketTMP[`movesState`]):til
isWinner:count[bucket[`indexInTree`]];
ewIndex:bucket[`treeMCTS`]+1);
// 更新现有的游戏树
bucketTMP:bucket[`treeMCTS`];
bucket[`treeMCTS`]:bucketTMP, ([]) index:newIndex;gameTree:
    elist
newGameTree:isWinner:isWinner)
```

```python
// 如果达到最大树的数量则停止
if(bucket[`numberOfRuns`]<count bucket[`treeMCTS`];bucket[`isWinner`]:1j
    -);
// 返回 bucket
bucket:
```

让我们关注函数中的几个元素。MCTS 算法的首次运行显式地作为随机播放运行。在没有先验信息的情况下，`oneTurn` 会一直迭代到结束。然后，通过将第一行添加到空表中，相应地更新 `treeMCTS` 表。这种方法允许我们从一个预训练的表开始，其中这一步会被跳过。对于第一次之后的迭代，将使用 `oneMCTSTurn` 函数。在该函数迭代结束后，通过分别提取 `newTree`、`newWinner` 和 `newIndex` 变量来更新 `treeMCTS` 表。为了将值追加到现有字典，我们通过本地临时变量来实现。最后，检查 MCT 迭代次数相对于 `numberOfRuns`。

让我们运行 `runMCTS` 迭代。首先，我们重置 bucket：

```python
bucket:(`moveStateIsWinnernumberOfRunstreeMCTS`)!($);01j;treeMCTS;sqrt 2);
```

并运行一次 MCTS 迭代：

```python
bucket.qantQ.runMCTS[bucket];nbucket
```

```python
`moveStateIsWinnernumberOfRunstreeMCTS`)!($symbol);01j;flip (indexgameTreeIswinner!)!(enlist 15,enlist b1;enlist b1;1j);1.4414214
```

其中 `treeMCTS` 表被填充了。让我们看看更多 MCTS 迭代的输出：

```python
`moveStateIsWinnernumberOfRunstreeMCTS`)!($symbol);01j;flip (indexgameTreeIswinner!)!(1j, 2j,(enlist b1;enlist a2;1j);1.4414214)
`moveStateIsWinnernumberOfRunstreeMCTS`)!($symbol);01j;flip (indexgameTreeIswinner!)!(1j, 2j, 3j,(enlist b1;enlist a2;b2);1j, 1j);1.4414214
`moveStateIsWinnernumberOfRunstreeMCTS`)!($symbol);01j;flip (indexgameTreeIswinner!)!(1j, 2j, 3j, 4j,(enlist a2;enlist b2,enlist c2;enlist b3;enlist c1;enlist a1;enlist a3;a1;b1;a2;a3;a2;b1;a2;b2;c3;b3;a2;c1;b3;c2;a2;b3) a3)j, 1j, 1j, 1j, 1j, 1j, 1j, 2j, 3j, 2j, 2j);1.4414214
```

游戏树是这样构建的。让我们跳到后续迭代以及 19 次迭代后创建的更新字典：

```python
`moveStateIsWinnernumberOfRunstreeMCTS`)!($symbol);01j;flip (indexgameTreeIswinner!)!(1j, 2j, 3j,(enlist b1;enlist a2;b2);1j, 1);11,11,1111111111111411121)
`moveStateIsWinnernumberOfRunstreeMCTS`)!($symbol);01j;flip (indexgameTreeIswinner!)!(1j, 2j, 3j, 4j,(enlist a2;enlist b2,enlist c2;enlist b3;enlist c1;enlist a1;enlist a3;a1;b1;a2;a3;a2;b1;a2;b2;c3;b3;a2;c1;b3;c2;a2;b3) a3)j, 1j, 1j, 1j, 1j, 1j, 1j, 2j, 3j, 2j, 2j);1.4414214
```
（注：此处原文中存在部分乱码或重复字符，翻译已根据上下文逻辑处理）

游戏树通过以下方式构建。让我们跳到后续迭代以及 19 次迭代后创建的更新字典：

```python
`moveStateIsWinnernumberOfRunstreeMCTS`)!($symbol);01j;flip (indexgameTreeIswinner!)!(1j, 2j, 3j, 4j,(enlist a2;enlist b2,enlist c2;enlist b3;enlist c1;enlist 1j, 1j, 1j, 1j, 1j, 1j, 1j, 2j, 3j, 2j, 2j);1.4414214
```
（注：原文中此处存在部分乱码，翻译已根据上下文逻辑处理）

让我们关注 `bucket(`treeMCTS`)`：

```python
| index | gameTree | isWinner |
| :--- | :--- | :--- |
| 1 | a3 | 1 |
| 2 | b1 | 3 |
| 3 | c2 | 3 |
| 4 | b2 | 2 |
| 5 | c3 | 3 |
| 6 | a1 | 1 |
| 7 | a2 | 1 |
| 8 | b3 | 2 |
| 9 | ct | 1 |
| 10 | a1a2 | 1 |
| 11 | a2c3 | 2 |
| 12 | a3b2 | 2 |
| 13 | b1a2 | 2 |
| 14 | c1a1 | 1 |
| 15 | c2a2 | 3 |
| 16 | c3a3 | 1 |
| 17 | a1c3 | 3 |
| 18 | ctc3 | 2 |
| 19 | a2c3 | 2 |
| 20 | c3a1 | 1 |

在 MCTS 运行结束，

