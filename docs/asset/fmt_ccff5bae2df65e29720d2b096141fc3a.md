
## 第 10 章 解析树 (Parse Trees)

解析树是 q 语言的一种重要内部结构。它们是嵌套列表——函数及其参数的集合，可以在需要时执行并以 `(func;arg1;arg2...)` 的形式表示。它们反映了 q 的 λ 演算哲学。此类函数的每个参数都可以是一个函数，任何 q 查询都可以表示为一系列嵌套函数。这些函数在被调用时可以被求值，并且可以根据其参数的类型进行不同的重载。

### 10.1 定义

解析树是一个列表，其第一个元素是函数，其余项是它的参数。这种结构可以是递归的，因此参数本身可以是函数；因此，解析树是 q 的内部表示。标记（Tokens）是 q 对常量和变量的内部表示。（等等，让我重读一遍。）

标记是 q 对常量和变量的内部表示。我们处理解析树时有两个关键运算符：`eval` 和 `parse`。

#### 10.1.1 求值

`eval` 将树本身作为参数，并返回求值后树对应的值。除非显式通过作为参数传递 `eval`，否则树本身不会被求值。让我们从一个基础示例开始：

```
parseTree1: (;:x;1j);
```

# 解析树 (167)

解析树是一个混合列表：

```
type parseTree1
Ø
```

列表的第一个元素是 `:`，即赋值运算符。列表的其它元素是赋值运算符的参数。此时我们可以推测 `parseTree1` 代表了 q 将 `1j` 赋值给变量 `x` 的内部表示。我们可以通过 `eval` 来验证它：

```
eval parseTree1
1
```

为了验证变量 `x` 是否被赋值了值，我们只需运行：

```
x
1
```

求值 `parseTree1` 确实为变量 `x` 赋值了值。变量是通过引用调用的，这使得解析树的构建更加灵活，因为引用本身可以是代码中动态赋值的变量。我们可以考虑想要创建以下变量列表的情况：`x1=1, x2=2, x3=3...`。我们可以这样构造第 k 项：

```
k:4;
name:"$x", string k;
eval (;name;k);
x4
4
```

我们可以将其嵌入创建一个变量的函数中：

```
parseTreeFunc1::[k]
eval ($x", string k);
};
```

该函数比之前的示例表示更简洁。我们可以测试它：

```
as
parseTreeFunc1[10];nx10
10
```

作为我们对基本解析树理解的证明，让我们尝试为以下语句构造一个与之前类似的解析树：

```
1 + 2 * 3
7
```

该语句是由两个更基础的语句组合成的：由于 q 从右向左解析，因此首先评估 `2*3`，然后输出结果变为语句 `1 + outputOffFirstStatement` 的第二个参数。我们将其写为解析树：

```
firstStatement:(;2;3);
```

```
secondStatement:(*;1;firstStatement);
```

我们现在求值

```
eval secondStatement;
```

此时，有必要引入值函数（value function）。该函数被高度重载，因为其功能取决于传入参数的类型。具体来说：

- 符号 - 它返回它的值；
- 枚举类型 - 它返回符号列表；
- 字典 - 它返回它的值；
- 函数 - 返回函数元数据列表，例如字节码、参数、局部变量、全局变量、常量和定义，正如我们在第 5 章和 `.quantQ.debug.meta` 函数中看到的那；
- 基本类型 - 它返回它的整数代码；例如：

```
value (+)
```

```
value (-)
```

```
value (%)
```

```
value value
```

19

- 字符串 - 它评估字符串的内容；

```
str:"cos acos -1"
```

## 解析树

我们可以对其进行求值：

```
value str
-1
```

- 列表格式为 `(func;arg1;arg2;...)` - 它执行函数 `func` 并带有参数 `arg1,arg2,...`

我们看到最后一种情况在定义上与解析树相似，且 `value` 和 `eval` 都可以评估同一个表达式。尽管如此，存在细微的，这两个函数的功能略有不同：`eval` 会评估一个构造正确的解析树。`value` 会执行一个函数和参数列表并返回其结果，同时执行上述列表中描述的其他实用程序。
因此我们得到：

```
value "1+2" / value the expression 3
eval "1+2" / 评估常量字符串，仅返回常量字符串
```

```
eval (+;1;2) / 计算解析树
3
value (;;somevar;2)
2
```

```
somevar
'somevar / variable doesnt exist
[0] somevar
^
eval (;;`somevar;2)
2
somevar
2
```

### 10.1.2 解析树的创建

我们可以使用 `parse` 获取语句的解析树：

```
parse str
(cos;(acos(-1j)))
```

```
eval parse str
-1f
```

这在创建函数式选择语句时作为辅助非常有用，我们稍后会进行说明。

### 10.1.3 只读评估

只读评估通过 `revel` 函数执行，其签名与 `eval` 相同。`revel` 动词远程访问实例并运行 `eval` 时，模拟使用选项 `-b` 启动 q 的效果。通过使用 `revel` 评估解析树，实例将阻塞任何尝试修改全局变量的传入消息。

例如，假设我们有一个端口号为 5000 的进程。我们打开该端口的句柄：

```
z: hopen 5000
```

我们在已打开的进程上定义一个变量：

```
z "a:1"
```

我们已经见过这等同于

```
z "eval(;;aa;1)"
```
1
```

如果我们改用 `revel`，命令将失败：

```
z "revel(;;aa;1)"
```

'noupdate: `aa

[[] z "revel(;;aa;1)"

AA
```

在使用像 qPad 这样的 IDE 时也会获得相同的错误，因为它连接到 q 实例。在 qPad 中运行相同的代码：

```
revel(;;aa;1)
```

```
ERROR: 'noupdate: `a
```

## 解析树

上述概念的一种常见工程实现方法是将 `revel` 结合内部消息处理器 `.z.pg` 使用，该处理器在作为服务器的 q 进程中处理传入的消息。我们可以实现这个一元函数的版本（它会自动为同步请求调用），我们的实现可以始终使用 `revel` 评估传入的消息，确保没有客户端可以修改服务端全局变量。

### 10.2 函数式查询

q 函数式查询——`select`、`update`、`delete` 函数允许我们聚合数据、计算统计数据并取消变量。这些查询的函数版本允许我们使用动态参数，例如列名。我们基于本章的示例进行构建。查询的函数式方法是：

```
select from tab
```

| a | b |
|---|---|
| 0 | 1 |
| 1 | 1 |
| 2 | 1 |
| 3 | 1 |
| 4 | 1 |
| 5 | 1 |
| 6 | 1 |
| 7 | 1 |
| 8 | 1 |
| 9 | 1 |

查询的函数式结果为：

```
select from tab
```

| a | b |
|---|---|
| 0 | 1 |
| 1 | 1 |
| 2 | 1 |
| 3 | 1 |
| 4 | 1 |
| 5 | 1 |
| 6 | 1 |
| 7 | 1 |
| 8 | 1 |
| 9 | 1 |

# 解析树

当从函数内部调用函数式查询时，它会将 `tab` 视为全局变量。在这种情况下，我们必须引用函数内部的局部变量，因此我们按值传递名称。我们可以如下说明这一点：让我们从一个哑函数调用函数式 select，我们首先通过引用传递表，然后通过值传递表。在调用函数式 select 之前，我们定义了一个与全局变量 `tab` 同名的本地表。

按引用传递表时，调用返回全局定义的表：

```
tab: ([][] aa:til 5);
?:[`tab`();0b;)
()
```

| a | b | c |
|---|---|---|
| 0 | 9 | 1 |
| 1 | 8 | 1 |
| 2 | 7 | 1 |
| 3 | 6 | 1 |
| 4 | 5 | 1 |
| 5 | 4 | 1 |
| 6 | 3 | 1 |
| 7 | 2 | 1 |
| 8 | 1 | 1 |
| 9 | 0 | 1 |

另一方面，当我们按值传递参数时，我们引用本地定义的表：

```
tab: ([][] d:til 5);
?:[`tab`();0b;)
()
```

| d |
|---|
| 0 |
| 1 |
| 2 |
| 3 |
| 4 |

我们可以通过标准 select 来确认这种差异：

```
tab: ([][] d:til 5);
:select from tab
()
```

# 176 # 数据操作

让我们来说几个如何使用函数式 select 的示例，因为这是一个强大的概念。如果我们想将 qSQL select 查询转换为其函数式对应项，我们建议按照以下步骤进行：

- 将原始查询拆解为原子部分。我们可以通过逐步构建查询来实现这一点。
- 在原子化的元素上应用 `parse` 函数。简化查询的解析树显示了完整查询的组件是如何转换的。
- 不需要将每个函数都解析为纯函数形式。我们可以保持像 `xbar` 这样的函数的原始形式，而不是将其转换为 k 版本。这使得查询更易获取、更容易理解。
- 由于列名是以符号按引用解析的，我们需要能够区分引用列名或符号常量：我们通过在符号常量上使用 `enlist` 来做到，正如我们在下面的示例中所看到的。

以下是函数式查询的示例。所有查询都返回 `1b`。我们鼓励读者自行运行它们并查看输出结果。

```
?[tab;);();()] ~ select from tab
```

```
?[tab;((<;b;8);(>;a;b));0b)] ~ select from tab where a>b
```

```
?[tab;((<;b;8);(+;a;c));(>;a;b));0b)] ~ select from tab where a>b, b8
```

```
?[tab;((within;b(1;6));(>;a;b));0b)] ~ select from tab where a>b, b
within (1;6)
```

```
?[tab;);();(enlist a!)!(enlist a)] ~ select a from tab
```

```
?[tab;);b;(enlist newA)!(enlist a)] ~ select newA:a from tab
```

```
?[tab;);0b;(enlist "newA")!(enlist a)] ~ select newA:a from tab
```

# 解析树

```
[`tab(););enlist(`newA)!(`;b`)) ~ select newA:a, b from tab
```

```
[`tab(););enlist(`newA)!(enlist (+;`b`)) ~ select newA:a+b from tab
```

```
[`tab(););enlist(`newA)!(enlist (cos;`a))` ~ select newA:cos from tab
```

tab: update d:count[i]?A`B`C from tab;
`tab;enlist (in;dlist `A);B);ob() ~ select from tab where d in `A`B

此查询没有返回内容，因为它包含了随机数生成器：
`tab(););enlist(`newA)!(enlist (?count[tab];1.0)) ~ select newA:count[tab]?1.0

然而，两个查询在功能上是相同的。让我们强调一下差异：
`tab(););enlist(`newA)!(enlist (?count[tab];1.0)) newA
805668

进一步，让我们关注表内的分组：
`tab(););enlist `a)!(enlist (sum;`a)) ~ select sum a from tab
```

```
`tab(););enlist `b)!enlist (_:`b;3j));(enlist `a)!(enlist (sum;`a])) ~ select sum a by floor[b[3]]
```

```
`tab();)(enlist `b)!enlist (_:`b;3j));(enlist `a)!(enlist (sum;`a])) ~ select sum a by floor[b[3]] from tab
```

```
`tab();)(`newB`newD)((_:`b;3j));(ceiling (`b;3j));(enlist `a)) ~
```

我们对函数式 select 的论述到此结束。一旦我们将表拆解为原子部分，构建函数式对应项就非常简单。根据我们的经验，构建函数式查询最大的障碍不是清楚查询的原子元素以及如何实现目标。在接下来的部分，我们将关注其他查询。

#### 10.2.2 函数式执行

与 qSQL select 相似的函数是 `exec` 函数。`select` 总是返回表，但如果只选择列，`exec` 将返回字典或向量。函数式对应项与 select 相同：

```
table;where;columns
```

其中这四个参数略有不同：

- table 是我们想要从中选择数据的表。表按引用或按值传递。
- where 包含了用于从树中选择的过滤标准。它的形式是解析树中的标准列表。列按引用传递。
- group 是对表进行分组的列名字典。键是新列名，而值由旧名称组成。名称按引用传递。
- columns 是要更新的列字典。键定义了新名称，例如 `a:`，而值对应语句的右侧。

以下是几个函数式查询的示例。所有查询都返回 `1b`。我们鼓励读者自行运行它们并查看输出结果。

```
?[tab;);();()] ~ select from tab
```

```
?[tab;((<;b;8);(>;a;b));0b)] ~ select from tab where a>b
```

```
?[tab;((<;b;8);(+;a;c));(>;a;b));0b)] ~ select from tab where a>b, b8
```

```
?[tab;((within;b(1;6));(>;a;b));0b)] ~ select from tab where a>b, b
within (1;6)
```

```
?[tab;);();(enlist a!)!(enlist a)] ~ select a from tab
```

```
?[tab;);b;(enlist newA)!(enlist a)] ~ select newA:a from tab
```

```
?[tab;);0b;(enlist "newA")!(enlist a)] ~ select newA:a from tab
```

# 解析树

```
[`tab(););enlist(`newA)!(`;b`)) ~ select newA:a, b from tab
```

```
[`tab(););enlist(`newA)!(enlist (+;`b`)) ~ select newA:a+b from tab
```

```
[`tab(););enlist(`newA)!(enlist (cos;`a))` ~ select newA:cos from tab
```

tab: update d:count[i]?A`B`C from tab;

`tab;enlist (in;dlist `A);B);ob() ~ select from tab where d in `A`B

此查询没有返回内容，因为它包含了随机数生成器：

`tab(););enlist(`newA)!(enlist (?count[tab];1.0)) ~ select newA:count[tab]?1.0

然而，两个查询在功能上是相同的。让我们强调一下差异：

`tab(););enlist(`newA)!(enlist (?count[tab];1.0)) newA

805668

进一步，让我们关注表内的分组：

`tab(););enlist `a)!(enlist (sum;`a)) ~ select sum a from tab
```

```
`tab(););enlist `b)!enlist (_:`b;3j));(enlist `a)!(enlist (sum;`a])) ~ select sum a by floor[b[3]]
```

```
`tab();)(enlist `b)!enlist (_:`b;3j));(enlist `a)!(enlist (sum;`a])) ~ select sum a by floor[b[3]] from tab
```

```
`tab();)(`newB`newD)((_:`b;3j));(ceiling (`b;3j));(enlist `a)) ~
```

我们对函数式 select 的论述到此结束。一旦我们将表拆解为原子部分，构建函数式对应项就非常简单。根据我们的经验，构建函数式查询最大的障碍不是清楚查询的原子元素以及如何实现目标。在接下来的部分，我们将关注其他查询。

#### 10.2.2 函数式执行

与 qSQL select 相似的函数是 `exec` 函数。`select` 总是返回表，但如果只选择列，`exec` 将返回字典或向量。函数式对应项与 select 相同：
```
