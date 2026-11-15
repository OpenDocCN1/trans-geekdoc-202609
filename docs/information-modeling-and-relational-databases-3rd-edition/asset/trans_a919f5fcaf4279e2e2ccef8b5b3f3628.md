

组件的顺序，并且只关注总体效果。因此，即使添加操作被指定在删除操作之前，也会以相同的结果被接受。

请注意，CIP 不能仅接受复合事务的一部分：这是“全部或不做”的情况。这里有几个更简单的交互示例：

```
add: Person ‘Linda’ lives in Country ‘AU’.           Accepted.
add: Person ‘Selena’ lives in Country ‘AU’.         Accepted.
add: Person ‘Terry’ is a parent of Person ‘Linda’.  Accepted.
add: Person ‘Terry’ is a parent of Person ‘Selena’. Accepted.
nrChildren of Person ‘Terry’?                       2.
list each Person who is a brother of Person ‘Paul’. Terry.
list each Person who lives in Country ‘AU’.         Linda
                                                    Paul
                                                    Selena
list each Person who is an uncle of Person ‘Selena’. No Person.
add: Person ‘Paul’ is a brother of Person ‘Terry’.  Accepted.
list each Person who is an uncle of Person ‘Selena’. Paul.
list each Person who is an aunt of Person ‘Selena’.  Rejected. Unknown fact type.
```

现在假设 UoD 通过添加以下约束而更改：

### C6 每个人都出生于某一年。

我们当前的数据库无法满足此约束。假设我们从空数据库重新开始，尝试添加以下事实。CIP 将如何响应？

```
add: Person ‘Bernard’ is a brother of Person ‘John’.
```

此更新请求被拒绝。它违反了两个约束（C1 和 C6），因为数据库中列出的所有人都必须同时记录其国家和出生年份。第 5 章使用术语“强制性角色”来描述此类约束。

通常，约束列出的顺序无关紧要。但是，如果更新请求违反多个约束，此顺序可能决定在 CIP 配置为最多报告一个违规时，报告哪个约束被违反。在此情况下，CIP 将对先前的请求作出如下响应：“Rejected. C1 violated”。如果 CIP 配置为报告所有约束违规，则将改为响应“Rejected. C1, C6 violated”。作为练习，请自行确认，在添加 C6 后，以下更新请求的处理结果如所示：

```
add: Person ‘Ken’ lives in Country ‘GB’.             Rejected. C6 violated.
begin
  add: Person ‘Ken’ lives in Country ‘GB’.
  add: Person ‘Ken’ was born in Year 1960.
end                                                   Accepted.
add: Person ‘Ken’ was born in Year 1959.              Rejected. C3 violated.
```

```
begin
    del: Person 'Ken' was born in Year 1960.
    add: Person 'Ken' was born in Year 1959.
    add: Person 'Erik' lives in Country 'NL'.
    add: Person 'Erik' was born in Year 1970.
    add: Person 'Ken' is a brother of Person 'Erik'.
end                          Accepted.
```

CIP 使用概念模式来监督数据库的更新并响应问题。请将概念模式的设计师视为“立法者”，将模式本身视为包含 UoD 法律或基本规则的“法典”。CIP 是“执法者”，因为它确保当用户尝试更新数据库时遵守这些法律。像任何友好的警察一样，CIP 也随时应要求提供信息。

每当我们与人或信息系统沟通时，脑中都会有一个特定的 UoD。通常，这涉及真实宇宙的一小部分，例如某个特定企业。在罕见情况下，我们可能会选择虚构的 UoD（例如，由漫画角色居住的世界），或者为我们正在撰写的小说而构建的奇幻世界。虚构的世界可能在逻辑上可能，也可能不可能。

您通常可以依靠自己的直觉来判断什么在逻辑上是可能的。例如，月亮呈绿色的世界是可能的，但月亮同时全身绿色和全身红色的世界是不可能的。可能的世界被称为 *一致的*，而不可能的世界称为 *不一致的*。

作为人类，我们的脑海中携带着海量信息。在我们个人的信念网络中，某处很可能潜伏着一些逻辑矛盾。在大多数情况下，我们的信念网络在全球范围内是否不一致并不重要。然而，在推理特定 UoD 时，一致性是必不可少的。很容易证明，一旦接受逻辑不一致，就可以从中推导出任何东西（包括废话）——这是“垃圾进，垃圾出”（GIGO）原则的极端案例。

基本上有两种垃圾：逻辑垃圾和事实垃圾。不一致的设计包含逻辑垃圾。例如，我们可能会声明两个相互矛盾的约束。一种受 CASE 工具支持并强制执行元规则的良好设计方法可以帮助避免此类问题。通过对数据库强制执行约束，可以防止许多事实错误。例如，声明的约束“每个人最多在一个国家出生”防止我们为某人分配多个出生国家。

即使模式是一致的，并且 CIP 检查数据库与此世界设计一致，仍然有可能向数据库中添加虚假数据。例如，如果我们告诉 CIP 爱因斯坦出生在法国，它可能会接受，尽管爱因斯坦实际上出生在德国。如果我们希望知识库在事实上保持正确，确保我们输入数据库的所有句子都表达实际为真的命题，仍然是我们的责任。

以下练习旨在练习本节讨论的概念，并介绍一些稍后将正式处理的其他约束类型。

## 练习 2.2

- 1. (a) 假设概念模式已存储，CIP 的两个主要功能是什么？
- (b) 概念模式的三个主要组成部分是什么？
- (c) “CIP 将拒绝任何其组件更新操作与概念模式不一致的复合事务”。正确或错误？

- 2. 假设存储了以下概念模式。约束适用于每个数据库状态。C1 表示数据库中提及的每个人都必须记录其健身评级。C3 说明可能的健身值为 1 到 10 的整数。C4 表示没有人可以被记录为多种运动的专家，C5 表示只有当某人也被记录为在同一种运动中参与时，才能记录其为该运动的专家。

参考方案：Person.(Firstname); Sport.(Name); FitnessRating.(Nr)

基本事实类型：
- F1 Person 具有 FitnessRating。
- F2 Person 参与 Sport。
- F3 Person 是 Sport 的专家。

约束：
- C1 每个 Person 都有某个 FitnessRating。
- C2 每个 Person 最多有一个 FitnessRating。
- C3 FitnessRating 的可能值为 1 到 10。
- C4 每个 Person 最多是某个 Sport 的专家。
- C5 每个作为某个 Sport 专家的 Person 也参与该 Sport。

推导规则：
- D1 如果 Person 参与 Sport 'judo' 或 Person 参与 Sport 'karatedo'，则 Person 是武术家。
- D2 Sport 的 nrPlayers = 参与该 Sport 的每个 Person 的计数。

数据库最初为空。用户现在尝试以下一系列更新和查询。对于每个更新，如果更新被接受（基于数据库的累积状态），请圈出字母。在拒绝的情况下，提供原因（例如，说明违反了模式的哪一部分）。对于查询，提供 CIP 的适当响应。

- (a) add: Person 'Ann' 具有 FitnessRating 9。
- (b) add: Person 'Fred' 参与 Sport 'tennis'。
- (c) add: Person 'Bob' 具有 FitnessRating 7。
- (d) add: Person 'Ann' 具有 FitnessRating 8。
- (e) add: Person 'Chris' 具有 FitnessRating 7。
- (f) add: Person 'Fred' 具有 FitnessRating 15。
- (g) add: Person 'Ann' 参与 Sport 'judo'。

