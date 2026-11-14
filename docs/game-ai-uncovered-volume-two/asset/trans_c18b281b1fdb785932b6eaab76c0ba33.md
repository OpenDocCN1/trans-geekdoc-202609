
代码清单 21.2：PlanNode 中的 IsGoal 函数，使用整数类型。
```
function CurrentNode.IsGoal with CurrentNode is C has
input: PlanNode with OtherNode is O
output: Boolean with true if w of O is same as w of C and Cw(s, v) >= Ow(s, v)
with: w is World State pair(state is s, value is v)
for each pair(s, v) in w of O do
if Ow(s) != Cw(s) return false
else if Cw(s, v) < Ow(s, v) return false
return true
```

GetNeighbours 函数是 SB-GOAP 的核心，因为动作在此确定其是否可以在世界状态上“工作”。如果是，它会创建带有前置条件和效果的新世界状态，作用于当前帧。代码清单 21.3 展示了针对布尔类型的检查算法。

```
Code Listing 21.3: The GetNeighbours function, using Boolean type.
function CurrentNode.GetNeighbours with CurrentNode is C has
input: PlanRequest with Request is R
output: Array<PlanNode> with Neighbours is N
where Niw := Cw and Niw(s, v) := Ve(s, v); e E Ai in A
with: Niw = Cw World State pair(state is s, value is v) of NI, NI is new PlanNode
where preconditions are p and effects are e of An | {Ai} is Action in R
where p(s, v) = Cw(s, v), Cw is World State pair(state is s, value is v) of C
where Nia is Ai in NI led to Cw
N := Ø
for each A in R do
for each pair(s, v) in p of Ai do
for each pair(s, v) in w of C do
if p(s, v) = Cw(s, v) then
new NI
Niw := Ai
NIw := Cw
for each pair(s, v) in e of Ai do
Niw(s, v) := e(s, v)
return N
```

代码清单 21.3 还展示了如何创建包含 WorldState 的新 PlanNode，基于已处理的当前节点的世界状态（如果动作符合当前节点世界状态的前置条件）。任何新状态或现有状态都会使用 PlanRequest 中每个动作的效果进行更新。

代码清单 21.4：ComputeCost 函数，使用布尔类型。

```
function CurrentNode.ComputeCost with CurrentNode is C has
    input: PlanRequest with Request is R, PlanNode with OtherNode is O
    output: Float with Cost is T
    where T := (if (Ca != 0) -> TCa else 0) + sum(Ta)
    with: TCa is cost of A led to Cw or 0 if no A led to Cw,
          preconditions are p of An | {Ai} is action in R
          where p(s, v) = Ow(s, v) and Ai = Oa
          where TaI is cost of Ai
          where Oa is Ai led to Ow, Ow is World State pair(state is s, value is v) of O
          where Ca is Ai led to Cw, Cw is World State pair(state is s, value is v) of C
          T := if (Ca()=0) -> TCa else 0
      for each A in R do
        for each pair(s, v) in p of Ai do
          for each pair(s, v) in w of O do
            if p(s, v) = Ow(s, v) and Oa = Ai
              T := T + TaI
return T
```

代码清单 21.4 中所示的 ComputeCost 函数在每个正在展开的邻近节点上发生。因为由 GetNeighbours 函数（代码清单 21.3）生成的节点同时包含世界状态和导致该状态的动作，ComputeCost 函数可以利用这些信息来确定成本。最后要探讨的函数是用于估算成本的函数。EstimateCost 在代码清单 21.5 中显示，用于估算从当前节点到目标节点的成本。对于两个节点之间任何不相同的世界状态，它都返回成本 1。

```
Code Listing 21.5: The EstimateCost function, using Boolean type.

function CurrentNode.EstimateCost with CurrentNode is C has
    input: PlanNode with OtherNode is O
    output: Float with HeuristicCost is H
    where H := (if (Cw with HeuristicCost is v) => 1 else 0
          : w is World State pair(state is s, value is v)
    H := 0
    for each pair(s, v) in w of C do
        for each pair(s, v) in w of O do
            if Cw(s, v) != Ow(s, v)
                H := H + 1
return H
```

## 21.4 平衡计划

SB-GOAP 的第二个核心概念是平衡，或者更准确地说，是动作的自平衡。由于 SB-GOAP 与 A* 有着深层联系，通过调整动作的成本，你可以影响规划过程的结果。但你为什么要这样做呢？你可能希望调整成本，因为“最优”计划并不总是“最优”，尤其是从游戏设计角度来看。如前所述，计划可以在单帧内计算出来，但实际执行（由代理人执行）每个动作可能需要几秒钟甚至几分钟才能完成，在这段时间里，代理人可能会遇到任何情况。

这意味着，朝着某个目标的计划在纸面上可能是最优的，但在当前环境/上下文中可能不是最优的。此外，针对同一目标反复出现的“最优”计划可能会破坏玩家的沉浸感。

当发布计划时，SB-GOAP 不会直接使用动作关联的成本。它将其添加到另一种称为“挂载”成本的成本中。“挂载”成本类似于导航网格的障碍物成本：打补丁时，新生成的导航网格的成本会因障碍物成本而改变。实现细节可能各异，但你得到的是一个被修改的、增加的成本，SB-GOAP 将“挂载”成本乘以乘数后，加到动作成本上。

表 21.1 列出了一些可能的动作，以及代理人用来构建完成目标计划时使用的 ID、乘数和“挂载”成本。

| 动作 | 代理/代理组/代理类型与成本乘数对 | “挂载”成本 |
| :--- | :--- | :--- |
| 砍伐树木 | {[ID:0, M:0], [ID:3, M:0.4], [ID:7, M:0.8], [ID…, M:…]} | 8 |
| 采矿 | {[ID:1, M:0.4], [ID:3, M:0.2], [ID:7, M:1], [ID…, M:…]} | 8 |
| 炼矿 | {[ID:1, M:0.7], [ID:2, M:0.6], [ID:3, M:0.5], [ID…, M:…]} | 5 |
| 加工木材 | {[ID:0, M:0.1], [ID:1, M:0.9], [ID:9, M:0.1], [ID…, M:…]} | 5 |
| 制造斧头 | {[ID:3, M:0.2], [ID:6, M:0.5], [ID:8, M:0.3], [ID…, M:…]} | 10 |
| 出售斧头 | {[ID:1, M:0.5], [ID:3, M:0.2], [ID:5, M:0.2], [ID…, M:…]} | 10 |
| 偷取黄金 | {[ID:0, M:0], [ID:3, M:0], [ID:7, M:0.1], [ID…, M:…]} | 20 |

当代理人发布计划时，传递给 PlanRequest 的动作成本 (C) 是动作的默认成本 (c) 加上乘数 (m) 乘以“挂载” (h) 成本：C = m * h + c。以图 21.3 中的示例动作为例，ID 为 6 的代理人正在评估“制造斧头”，其默认成本为 3.0，乘数为 0.5，“挂载”成本为 10.0，因此此时的实际动作成本为：

```
C = m * h + c = 0.5 * 10 + 3.0 = 8.0
```

该代理人可以在表 21.1 的“制造斧头”行中找到，即配对列表中的第二对。

表 21.1 的最后一行有一个名为“偷取黄金”的动作，它是积累黄金的有效动作，但如果此类动作的默认成本远高于计划中其他成本之和，则不太可能被触发，即使它没有前置条件且效果为“拥有黄金”（即目标状态）。

之所以这样，是因为你不希望平民偷取黄金，因此该动作的成本被相应设置。但如果你希望平民开始偷窃怎么办？无需为平民制作新的自定义动作，也不需要配合 SB-GOAP 使用另一个系统，你只需调整成本即可。

![](img/f4a4f6e4de5338a867590c30638990cf_198_0.png)

### 图 21.4 动作、成本和可能的解决方案。

图 21.4 描绘了一份代理人为获得黄金（目标）所考虑的动作列表。代理人要获得黄金，在这些动作中只有两种可能的解决方案，一种总成本为 10，另一种总成本为 15。“偷取黄金”动作明确要求所有前置条件均为 false（这并非强制性），否则代理人可能会在砍完树或采完矿后立刻偷取黄金。

首先，查看图 21.4 中的第一个解决方案。动作顺序将严格基于前置条件和效果。这一点很重要，因为 SB-GOAP 不仅可以根据某些“负面”因素平衡动作，还可以根据某些谓词进行平衡。例如，在发布计划前，可以检查代理人是否在露天采矿（例如森林中的岩石上），这使得代理人先采矿后砍伐树木很合理。然后，进行木材加工和炼矿。检查玩家到木材和熔炉的距离将帮助 SB-GOAP 决定行动计划。假设 P0 是代理人位置，P1 是木材中心区域，P2 是熔炉，它们分别如下：

```
$P_0 = (5,5,10), P_1 = (7,7,11), P_2 = (9,9,8)$
```
