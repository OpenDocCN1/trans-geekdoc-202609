

在许多版本的 SQL 中，使用 **group by** 会导致默认排序，相当于匹配的 **order by** 子句（例如，在这种情况下为 **order by family**）。但是，这不是 SQL 标准的一部分。**group by** 子句的语法是：

```
group by col-name [, ...]
```

同一组的成员必须在 **group by** 子句中指定的所有列上具有匹配的值。

下一个示例将粒子分组，使其具有相同的家族名称和相同的电荷。

```
select family, charge, count(*) as tally
from Particle
group by family, charge
order by family, charge
```

| 家族 | 电荷 | 计数 |
| :--- | :--- | :--- |
| 重子 | -1 | 2 |
| 重子 | 0 | 4 |
| 重子 | 1 | 2 |
| 轻子 | -1 | 2 |
| 轻子 | 0 | 2 |
| 介子 | -1 | 2 |
| 介子 | 0 | 3 |
| 介子 | 1 | 2 |

如果使用多个列进行分组，则指定这些列的顺序与结果内容无关。这是因为必须形成相同的组集。例如，如果按属性 a、b 或 b、a 进行分组，则值为 a=a1、b=b1 的组与值为 b=b1、a=a1 的组相同，以此类推。

但是，如果行顺序基于组顺序，则结果中行的顺序可能不同。例如，以下查询返回与前一个查询相同的行，但顺序不同。您可以调整 **order by** 子句以更改顺序：

```
select family, charge, count(*) as tally
from Particle
group by charge, family
order by charge, family
```

| 家族 | 电荷 | 计数 |
| :--- | :--- | :--- |
| 重子 | -1 | 2 |
| 轻子 | -1 | 2 |
| 介子 | -1 | 2 |
| 重子 | 0 | 4 |
| 轻子 | 0 | 2 |
| 介子 | 0 | 3 |
| 重子 | 1 | 2 |
| 介子 | 1 | 2 |

如果 **select** 列表中的函数调用用作排序条件，则应该为它引入别名，以便可以在 **order by** 子句中按名称引用它。例如，以下查询列出每个家族及其最轻粒子的质量，并按该最小质量排序。作为不希望的替代方案，可以按其在 **select** 列表中的位置引用它（例如，**order by 2**）。

```sql
select family, min (mass) as minMass
from Particle
group by family
order by minMass
```

| 家族 | minMass |
| :--- | :--- |
| 轻子 | 0 |
| 介子 | 264 |
| 重子 | 1836 |

使用 group by 子句意味着 `select` 列表中的项目将应用于每个组整体，每组只返回一个值。因此，`select` 列表中提到的任何列必须是分组列，或者必须作为内置函数的参数出现在其中（例如，前述查询中的 family 和 mass）。因此，在进行分组时，将未分组的列作为 `select` 列表中的完整项包含在内是没有意义的，而且事实上是非法的。例如：

```sql
select family, mass from Particle  -- Error!
group by family
```

因为同一家族可能包含质量不同的几个粒子，这个请求很荒谬（我们应该选择哪个质量？）。不过，我们可以使用内置函数（例如 `min (mass)` 或 `avg (mass)`）来获取与质量相关的单个分组值，就像我们在前一个查询中所做的那样。

虽然 `select` 列表不得包含任何未分组的列，但按未在 `select` 列表中提及的列进行分组是合法的。例如，以下查询列出每个家族的最小质量，但不列出名称。

```sql
select min (mass) as minMass
from Particle
group by family
```

| minMass |
| :--- |
| 0 |
| 264 |
| 1836 |

在 `select` 语句中，可以包含 `where` 子句，以便在形成组和应用函数之前过滤掉不需要的行。合理的是，`where` 子句必须放在 `group by` 子句之前。例如，以下查询列出每个家族及其未带电粒子的平均质量。为了适应诸如 SQL Server 等会对平均值进行截断的方言，质量已通过乘以 1.0 强制转换为实数，并使用 `cast` 函数仅显示小数点后两位数字。注意，将标量函数应用于袋函数是合法的，例如 `cast (avg (...))`。但是，将袋函数应用于袋函数是非法的，例如 `min (avg (...))`。

```sql
select family, cast (avg (1.0*mass) as decimal (6,2)) as avgUnchargedMass
from Particle
where charge = 0
group by family
```

| 家族 | avgUnchargedMass |
| :--- | :--- |
| 重子 | 2232.25 |
| 轻子 | 0.00 |
| 介子 | 770.65 |

有时，我们希望只关注满足特定条件的组。就像 **where** 子句可用于对单个行施加搜索条件一样，**having** 子句可用于对单个组施加搜索条件。在这种情况下，**having** 子句必须紧跟在与其在逻辑上相关的 **group by** 子句之后。语法是：

```
group by col-name [, ...]
having group-condition
```

搜索条件的常规规则适用。条件中可以包含逻辑运算符和比较运算符。每个比较都将组的某个属性（例如 min (mass)）与常数或另一个组属性进行比较。（虽然罕见，但可以在没有关联 **group by** 子句的情况下包含 **having** 子句；在这种情况下，整个表被视为一个组。）作为简单示例，以下查询列出粒子数超过四个的家族以及每个家族的粒子数。虽然允许在 **having** 子句中使用别名（例如 tally）很有意义，但在许多 SQL（例如 SQL Server）中不允许这样做。

```
select family, count (*) as tally
from Particle
group by family
having count (*) > 4
```

| 家族 | 计数 |
|--------|-------|
| 重子 | 8 |
| 介子 | 7 |

下一个示例更难。为了帮助澄清其工作原理，已添加数字 1 到 6 以指示处理查询行的顺序。这些数字不是查询的一部分。请自行跟踪步骤，以确保您遵循此顺序。关于 **having** 子句，请注意带电轻子被包括在内（未带电且质量为零的轻子被 **where** 子句过滤掉），而带电重子被排除（它们的最大质量超过 2000）。

仅考虑带电粒子，按相同的家族名称形成组，其中组中最轻粒子的质量高于 0，组中最重粒子的质量低于 2000。列出每个组的家族名称、粒子数和最大质量，并按成员较多的组优先显示。

```
5 select family, count (*) as chargedTally, max(mass) as maxChargedMass
1 from Particle
2 where charge <> 0
3 group by family
4 having min (mass) > 0 and max (mass) < 2000
6 order by chargedTally desc
```

| 家族 | chargedTally | maxChargedMass |
|--------|--------------|----------------|
| 介子 | 4 | 966 |
| 轻子 | 2 | 207 |

分组的一个平凡用途只是避免重复。例如，以下查询可用作 select distinct family from Particle 的替代方案：

```
select family from Particle
group by family
```

| 家族 |
| --- |
| 重子 |
| 轻子 |
| 介子 |

现在假设我们发出以下查询。结果将是什么？

```
select family from Particle
group by family
having count (*) = 4
```

将此与前一个查询进行比较，您可能会觉得每个家族的计数将为 1，因此不会返回任何行（即结果是空集）。不！当 group by 子句执行其工作时，每个组仍然包含其所有成员（它们当然都具有相同的组值）。having 子句现在会过滤掉不满足其搜索条件的那些组。最后，select 列表决定列出哪些组属性。组首先被排序为三个家族，其中两个家族被排除（重子和介子），最后只列出剩余组（四个轻子）的家族名称“轻子”。

作为分组的进一步应用，让我们考虑如何处理简单关系除法的情况。图 12.57 显示了一个 SQL 查询，用于以前在图 12.27 中通过关系除法处理的示例。在这里，列名“language”被双引号括起来，因为它是保留字。

虽然 SQL 没有提供关系除法运算符，但我们通过如所示的分组来实现相同的效果。第一个子查询生成（“英语”、“法语”），因此 where 子句在形成组之前过滤掉荷兰语和西班牙语行。

| 国家 | 语言 |
| --- | --- |
| 澳大利亚 | 英语 |
| 比利时 | 荷兰语 |
| 比利时 | 法语 |
| 加拿大 | 英语 |
| 加拿大 | 法语 |
| 古巴 | 西班牙语 |
| 多米尼卡 | 英语 |
| 多米尼卡 | 法语 |

哪些国家会说加拿大所说的所有语言？

```
select country from Speaks
where "language" in
(select "language" from Speaks
where country = 'Canada')
group by country
having count (*) =
(select count(*) from Speaks
where country = 'Canada')
```

| 国家 |
| --- |
| 加拿大 |
| 多米尼卡 |

图 12.57 分组可用于执行关系除法。

