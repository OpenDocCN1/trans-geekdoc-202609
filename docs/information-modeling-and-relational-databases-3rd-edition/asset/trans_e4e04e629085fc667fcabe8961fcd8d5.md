

这涵盖了 SQL 中最重要的标量运算符和函数。其他标量函数的讨论可参见章节注释中引用的参考文献。

## 练习 12.9

- 1. 本题引用了练习 12.8 中使用的 Diet 数据库。表架构为：Eater( person, weight, gender)、Eats( person, foodName) 和 Food( foodName, foodClass)。为以下各项编写 SQL 查询：
  - (a) 体重超过 100kg 的男性有多少人？
  - (b) 有多少种不同的体重？
  - (c) 男性的体重总和是多少？
  - (d) 女性的平均体重是多少？
  - (e) 吃牛肉的人中体重最重的是多少？
  - (f) 对接下来的两个问题，各给出两个等价解，一个使用函数，另一个使用 "all" 或 "some" 量词。
  - (g) 哪些女性比每个男性都轻？
  - (h) 列出体重至少等于一个男性的那些女性的姓名和体重。

- 2. 图中所示的 Log 表由一家五金店用来记录原木详情。其模式为 Log( code, diameter, len, mass, cost_price, retail_price)。原木的直径、长度（此处称为“len”）、质量和价格分别以 cm、m、kg 和 $ 为单位。用 SQL 表述以下内容。

| code | diameter | len | mass | cost_price | retail_price |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 2A | 15 | 2 | 10 | 4.00 | 7.00 |
| 3B | 20 | 3 | 20 | 6.00 | 9.50 |
| 5C | 20 | 5 | 30 | 9.00 | 13.00 |
| 5D | 20 | 5 | 25 | 8.00 | 2.00 |

  - (a) 列出所有原木的绝对加价（即零售价–成本价）。
  - (b) 列出每个原木的体积（立方米），列标题为“Volume (cubic m)”。体积公式为 V=πD²L/4，π 近似为 3.14。每个体积表示为固定点数，截断至三位小数。
  - (c) 列出长度为 5 m 的原木的密度（即质量/体积），单位为 kg/m³。使用适当的标题，并将每个密度显示为截断至两位小数的固定点数。
  - (d) 哪个原木的相对加价最高（使用比率 R.P./C.P.）？
  - (e) 哪个原木的长径比低于平均值？在输出中包含该比率（无量纲，两位小数）。

- 3. 图书馆使用以下数据库模式来记录图书详情。作者通过姓名标识，图书通过其国际标准书号（ISBN）标识。示例数据如下。

```
Book   ( isbn, title, publisher, yrPublished, nrCopies )
           ^
WrittenBy( isbn, authorName )
           :
Author   ( authorName, gender, nationality )
```

| isbn | title | publisher | yrPublished | nrCopies |
|---|---|---|---|---|
| 101 | Databases | Possum | 1985 | 4 |
| 202 | SQL Primer | Hall | 1984 | 4 |
| 246 | Databases | West | 1980 | 1 |
| 345 | dBase III | West | 1986 | 1 |
| 400 | Modula 2 | Possum | 1986 | 4 |
| 444 | Advanced SQL | Hall | 1986 | 2 |
| 500 | Informatics | Hall | 1986 | 2 |

用 SQL 表述以下查询。

  - (a) 澳大利亚男性作者有哪些？
  - (b) 列出 1984-1986 年期间出版的图书标题，按标题排序。（解释“dBase III”在结果中的位置。）
  - (c) 列出标题中包含“SQL”的所有图书的详细信息，按最近出版的先后顺序显示。
  - (d) 谁写了一本名为“Databases”并在 1980 年出版的图书？
  - (e) 列出至少有一位澳大利亚作者的所有图书的 ISBN 和标题。
  - (f) 列出由 Hall 在 1986 年出版的名为“Informatics”的任何图书的作者姓名和国籍。
  - (g) 列出澳大利亚男性作者和美国女性作者的姓名，并附上合适的描述符，澳大利亚男性作者排在前面。

| isbn | authorName |
|---|---|
| 101 | Brown J |
| 101 | Collins T |
| 202 | Adams A |
| 246 | Smith JB |
| 345 | Jones S |
| 400 | Smith JA |
| 444 | Adams A |
| 500 | Brown J |
| 500 | Smith JA |

| authorName | gender | nationality |
|---|---|---|
| Adams A | F | Aussie |
| Brown J | M | Aussie |
| Collins T | M | Kiwi |
| Jones S | F | American |
| Smith JA | M | Aussie |
| Smith JB | M | American |

- 4. 为本节讨论的 Pupil 表指定以下 SQL 查询。
  - (a) 在单个列中列出女学生的姓名，姓氏在前，后跟逗号、空格和名，例如，“Adams, Ann”。
  - (b) 列出学生总数以及已知 IQ 的学生人数。
  - (c) 列出每个已知 IQ 的学生的 pupilNr、surname、firstname 和 gender，将性别指定为名称（“Female”或“Male”）而非代码（“F”或“M”）。

## 12.10 SQL：分组

有时，我们希望将表的行划分为若干个 *groups*，并显示适用于每个整体组的属性。SQL 提供了一个 **group by** 子句，可包含在 **select** 语句中以检索此类分组数据。*每个 group 是一组具有 **group by** 子句中列出的分组条件相同值的行。最终查询结果最多为每个组包含一行。*

图 12.56 说明了按列 *a* 分组的情况。这里有三个 groups，每个 *a* 值对应一个。结果可能包含 *a* 的某个组属性或函数，在此描绘为 *f(a)*。

![](img/1344db3eba3d550e6edb009556fcd95c_646_0.png)

图 12.56 将具有相同列 a 值的行划分为 groups。

由于最终结果仅为每个组包含一行，因此 **select** 列表只能包含组属性。

换句话说，对于每个组，每个 **select** 项目只有一个值。为确保这一点，每个组属性必须是分组条件（用于分组的列名）、函数调用（例如 **count (*)**）、常量，或由这些项组成的表达式（例如 2 * groupcol）。SQL 中 **group by** 查询的基本语法如下：

```
select group-property1, ...
from ...
[where ...]
group by group-criterion1, ...
```

表 12.14 将用于帮助解释上述大部分概念。关系模式为 *Particle (particleName, family, charge, mass)*。为了帮助可视化按 family 分组，行已按 family 排序，并在 groups 之间添加了空行。每个粒子的电荷以基电荷为单位给出。基电荷是质子的电荷，等于 1.6 × 10⁻¹⁹ C。电子的质量为 9.1 × 10⁻³¹ kg。每个粒子的质量表示为电子质量的倍数。

## 表 12.14 某些原子粒子。

*Particle:*

| particleName | family | charge | mass |
| :--- | :--- | :--- | :--- |
| neutrino | lepton | 0 | 0 |
| mu neutrino | lepton | 0 | 0 |
| electron | lepton | -1 | 1 |
| mu - | lepton | -1 | 207 |
| pi 0 | meson | 0 | 264 |
| pi + | meson | 1 | 273 |
| pi - | meson | -1 | 273 |
| K + | meson | 1 | 966 |
| K - | meson | -1 | 966 |
| K 0 | meson | 0 | 974 |
| eta | meson | 0 | 1074 |
| proton | baryon | 1 | 1836 |
| neutron | baryon | 0 | 1839 |
| lambda | baryon | 0 | 2183 |
| sigma + | baryon | 1 | 2328 |
| sigma 0 | baryon | 0 | 2334 |
| sigma - | baryon | -1 | 2343 |
| xi - | baryon | -1 | 2585 |
| xi 0 | baryon | 0 | 2573 |

考虑以下查询：列出各 family 以及每个 family 中的粒子数量。可按如下所示用 SQL 表述。在本节中，结果表的列标题下方用短划线下划线（这在大多数 SQL 中很常见）。

```
select family, count(*)
from Particle
group by family
```

| family | count(*) |
| :--- | :--- |
| baryon | 8 |
| lepton | 4 |
| meson | 7 |

在此，**group by** 子句表示粒子要被 *grouped* 为 families（即，具有相同 family 名称的粒子被放在同一个 group 中）。然后，对每个 **group** 整体应用 **select** 列表中的 *items*。

如果使用 **count (*)**，则返回 group 中的行数。在此情况下，我们有 8 个 baryon、4 个 lepton 和 7 个 meson。如果 **select** 列表中使用的是列名以外的表达式，某些 SQL 会将表达式用作结果中的列标题（如这里所示），而另一些（包括 SQL Server）则会省略列标题。通常最好在表达式后使用 **as** 子句来提供自己的标题。

