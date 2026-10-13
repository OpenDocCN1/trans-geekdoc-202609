
*   ```
    add: Person ‘Norma’ lives in Country ‘AU’.
    ```

*   ```
    end                                                                                                                                         Accepted.
    ```

CIP 接受事务当且仅当其整体效果与概念模式一致。用户将此复合事务作为两个基本更新的序列输入。在这里先指定删除操作再指定添加操作更自然。然而，CIP 将任何复合事务视为更新的*集合*，忽略组件的顺序，只关注总效果。因此，即使先指定添加操作再指定删除操作，也会被接受并产生相同的结果。

请注意，CIP 不能只接受复合事务的一部分：这是“全有或全无”的情况。以下是更多简单的交互示例：

```
add: Person ‘Linda’ lives in Country ‘AU’.           Accepted.
add: Person ‘Selena’ lives in Country ‘AU’.         Accepted.
add: Person ‘Terry’ is a parent of Person ‘Linda’.     Accepted.
add: Person ‘Terry’ is a parent of Person ‘Selena’.    Accepted.
nrChildren of Person ‘Terry’?                   2.
list each Person who is a brother of Person ‘Paul’.   Terry.
list each Person who lives in Country ‘AU’.         Linda
                                                    Paul
                                                    Selena
list each Person who is an uncle of Person ‘Selena’.  No Person.
add: Person ‘Paul’ is a brother of Person ‘Terry’.     Accepted.
list each Person who is an uncle of Person ‘Selena’.  Paul.
list each Person who is an aunt of Person ‘Selena’.   Rejected. Unknown fact type.
```

现在假设通过添加以下约束来更改 UoD：

```
   C6      Each Person was born in some Year.
```

我们当前的数据库不满足此约束。假设我们从空数据库重新开始，尝试添加以下事实。CIP 会如何响应？

```
add: Person ‘Bernard’ is a brother of Person ‘John’.
```

此更新请求被拒绝。它违反了两个约束（C1 和 C6），因为数据库中列出的所有人都必须记录其国家和出生年份。第 5 章使用“强制角色”术语来描述此类约束。

通常，约束的列出顺序无关紧要。但是，如果更新请求违反了多个约束，该顺序可能决定报告哪个约束被违反（如果 CIP 配置为最多报告一个违规）。在这种情况下，CIP 对前一个请求的响应将是：“Rejected. C1 violated”。如果 CIP 配置为报告所有约束违规，它将改为响应“Rejected. C1, C6 violated”。作为练习，请说服自己，添加 C6 后，以下更新请求将按如下方式处理：

*   ```
    add: Person ‘Ken’ lives in Country ‘GB’.                                               Rejected. C6 violated.
    ```

*   ```
    begin
    ```

*   ```
    add: Person ‘Ken’ lives in Country ‘GB’.
    ```

*   ```
    add: Person ‘Ken’ was born in Year 1960.
    ```

*   ```
    end                                                                                                                                                Accepted.
    ```

*   ```
    add: Person ‘Ken’ was born in Year 1959.                                       Rejected. C3 violated.
    ```

*   ```
    begin
    ```

*   ```
    del: Person ‘Ken’ was born in Year 1960.
    ```

*   ```
    add: Person ‘Ken’ was born in Year 1959.
    ```

*   ```
    add: Person ‘Erik’ lives in Country ‘NL’.
    ```

*   ```
    add: Person ‘Erik’ was born in Year 1970.
    ```

*   ```
    add: Person ‘Ken’ is a brother of Person ‘Erik’.
    ```

*   ```
    end                                                                                                                                                                Accepted.
    ```

CIP 利用概念模式来监督数据库更新并响应查询。可以将概念模式的设计者视为“立法者”，将模式本身视为包含 UoD 法律或基本规则的“法典”。CIP 是“执法者”，因为它确保每当用户尝试更新数据库时都遵守这些法律。就像任何友好的警察一样，CIP 也会根据请求提供信息。

每当我们与一个人或一个信息系统进行交流时，心中都会有一个特定的 UoD。通常，这涉及现实世界的某一小部分，例如某个特定的业务。在极少数情况下，我们可能会选择一个虚构的 UoD（例如，由漫画人物组成的世界），或者可能是我们为正在撰写的小说发明的一个幻想世界。虚构世界在逻辑上可能是可能的，也可能是不可能的。

你通常可以依靠自己的直觉来判断什么在逻辑上是可能的。例如，一个月亮呈绿色的世界是可能的，但一个月亮同时全绿且全红的世界则是不可能的。一个可能的世界被称为*一致的*，而一个不可能的世界则是*不一致的*。

作为人类，我们在脑海中携带着大量的信息。极有可能在我们个人的信念网络中某处潜伏着一些逻辑矛盾。在大多数情况下，我们的信念网络在全局上是否不一致并不重要。然而，在对特定 UoD 进行推理时，一致性至关重要。很容易证明，一旦你接受了一个逻辑不一致性，就可以从中推导出任何东西（包括垃圾）——这是垃圾进垃圾出（GIGO）原则的一个极端例子。

基本上有两类垃圾：逻辑垃圾和事实垃圾。不一致的设计包含逻辑垃圾。例如，我们可能会声明两个相互矛盾的约束。由强制执行元规则的 CASE 工具支持的良好设计方法有助于避免此类问题。通过强制执行数据库上的约束，可以防止许多事实错误。例如，声明的约束“每个 Person 至多出生在一个 Country”可以防止我们为一个人分配多个出生国家。

即使模式是一致的，且 CIP 检查数据库与此世界设计一致，仍然有可能向数据库中添加虚假数据。例如，如果我们告诉 CIP 爱因斯坦出生在法国，它可能会接受，尽管爱因斯坦实际上出生在德国。如果我们希望知识库保持事实上的正确性，我们仍有责任确保我们录入数据库的所有句子所表达的命题实际上都是真的。

以下练习提供了对本节讨论概念的练习，并介绍了一些稍后将正式处理的进一步约束类型。

### 练习 2.2

1.  (a) 假设概念模式已存储，CIP 的两个主要功能是什么？

    (b) 概念模式的三个主要组成部分是什么？

    (c) “如果复合事务的任何组成更新操作与概念模式不一致，CIP 将拒绝该复合事务”。对还是错？

2.  假设存储了以下概念模式。约束适用于每个数据库状态。C1 意味着数据库中提到的每个人必须记录其体能评级。C3 规定可能的体能值为 1 到 10 的整数。C4 意味着没有人可以被记录为在多于一项运动上是专家，C5 规定只有当某人也被记录为从事同一项运动时，才能被记录为在该运动上是专家。

*   ```
    参考模式:     Person(.Firstname); Sport(.Name); FitnessRating(.Nr)
    ```

*   ```
     基础事实类型:                  F1       Person has FitnessRating.
    ```

*   ```
                                                                F2       Person plays Sport.
    ```

*   ```
                                                                F3       Person is expert at Sport.
    ```

*   ```
    约束:                           C1       Each Person has some FitnessRating.
    ```

*   ```
                                                                C2       Each Person has at most one FitnessRating.
    ```

*   ```
                                                                C3       The possible values of FitnessRating are 1 to 10.
    ```

*   ```
                                                                C4       Each Person is expert at at most one Sport.
    ```

*   ```
                                                                C5       Each Person who is expert at some Sport also plays that Sport.
    ```

*   ```
     推导规则:                D1       Person is a martial artist if
    ```

*   ```
                                                                                                Person plays Sport ‘judo’ or Person plays Sport ‘karatedo’.
    ```

*   ```
                                                                D2       nrPlayers of Sport = count each Person who plays that Sport.
    ```

数据库最初为空。用户现在尝试以下更新和查询序列。对于每个更新，如果根据数据库的累积状态接受该更新，请圈出字母。在拒绝的情况下，提供理由（例如，说明违反了模式的哪一部分）。对于查询，提供 CIP 的适当响应。

*   (a)

    ```
    add: Person ‘Ann’ has FitnessRating 9.
    ```

*   (b)

    ```
    add: Person ‘Fred’ plays Sport ‘tennis’.
    ```

*   (c)

    ```
    add: Person ‘Bob’ has FitnessRating 7.
    ```

*   (d)

    ```
    add: Person ‘Ann’ has FitnessRating 8.
    ```

*   (e)

    ```
    add: Person ‘Chris’ has FitnessRating 7.
    ```

*   (f)

    ```
    add: Person ‘Fred’ has FitnessRating 15.
    ```

*   (g)

    ```
    add: Person ‘Ann’ plays Sport ‘judo’.
    ```

*   (h)

    ```
    add: Person ‘Bob’ is expert at Sport ‘soccer’.
    ```

*   (i)

    ```
    add: Person ‘Ann’ is expert at Sport ‘judo’.
    ```

*   (j)

    ```
    add: Person ‘Ann’ programs in Language ‘SQL’.
    ```

*   (k)

    ```
    add: Person ‘Ann’ plays Sport ‘soccer’.
    ```

*   (l)

    ```
    add: Person ‘Chris’ plays Sport ‘karatedo’.
    ```

*   (m)

    ```
    del: Person ‘Chris’ has FitnessRating 7.
    ```

*   (n)

    ```
    begin
    add: Person ‘Bob’ has FitnessRating 8;
    del: Person ‘Bob’ has FitnessRating 7.
    end
    ```

*   (o)

    ```
    add: Person ‘Ann’ is expert at Sport ‘soccer’.
    ```

*   (p)

    ```
    add: Person ‘Bob’ plays Sport ‘soccer’.
    ```

*   (q)

    ```
    Person ‘Ann’ plays Sport ‘judo’?
    ```

*   (r)

    ```
    list each Person who plays Sport ‘karatedo’.
    ```

*   (s)

    ```
    nrPlayers of Sport ‘soccer’?
    ```

*   (t)

    ```
    list each Person who is a martial artist.
    ```

*   (u)

    ```
    list possible values of FitnessRating.
    ```

*   (v)

    ```
    what is the meaning of life?
    ```

3.  在以下模式中，约束适用于数据库，不一定适用于现实世界。虽然每个学生都有婚姻状况，但记录它是可选的（例如，一些学生可能希望保持婚姻状况私密）。约束 C1 结合了两个较弱的约束，因为“恰好一个”意味着“至少一个（即一些），且至多一个”。

*   ```
    参考模式: Student(.Firstname); Degree(.Code); MaritalStatus(.Name)
    ```

*   ```
    基础事实类型:       F1     Student is enrolled in Degree
    ```

*   ```
                                                      F2     Student has MaritalStatus
    ```

### 约束条件

*   **C1**：每个 Student 恰好注册在一个 Degree 中。

*   **C2**：每个 Student 至多有一个 MaritalStatus。

*   **C3**：MaritalStatus 的可能值为 ‘single’、‘married’、‘widowed’、‘divorced’。

*   **C4**：MaritalStatus 状态转换：（“1” = “允许”）

![u02-01-9780443237904](img/u02-01-9780443237904.jpg)

数据库初始为空。用户尝试执行以下更新和查询序列。对于每个更新，如果接受则圈出字母；如果拒绝，则给出理由。假设问题合法并提供适当的答案。

1.  **(a)**
