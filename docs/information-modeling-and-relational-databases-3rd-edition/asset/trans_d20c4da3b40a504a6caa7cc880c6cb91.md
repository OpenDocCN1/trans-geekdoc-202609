

## UML 术语表

本术语表列出了第 9 章中讨论的 UML 数据模型（类图）中使用的关键术语和符号。

- **聚合**：在整体-部分关系中是“整体”的类。
- **关联**：涉及两个或更多关联角色的关系类型。
- **关联类**：既是关联又是类的关联；ORM 中的对象化关联。
- **关联端**：对应 ORM 中的角色。
- **属性**：对象的属性；可以是单值或多值。
- **可变性**：属性或角色值可能的变化方式：无限制、只读、仅添加、仅删除。
- **类**：对象的类型（参见 ORM 实体类型）。
- **集合属性字符串**：对属性或关联角色的注释，指示要使用的集合类型。例如，{ordered}、{nonunique} 和 {ordered, nonunique} 分别指定有序集、包和序列。
- **组合**（_组合聚合_）：每个部分最多属于一个整体。
- **数据值**：标量常量；数据类型实例；自标识（参见 ORM 值）。
- **派生元素**：从其他属性或关联计算或推导出的属性或关联。
- **泛化**：从一个或多个类形成更一般的类（超类）。
- **链接**：关系实例——ORM 中的一个事实。
- **多重性**：同一对象在属性或关联中可能关联的实例数量。
- **对象**：通常可以改变其状态的事物；类的实例；由 oid 标识（参见 ORM 实体实例）。
- **Oid**：对象标识符；系统生成的用于引用对象的常量。
- **限定关联**：一个类通过限定符与另一个类关联的关联。
- **共享聚合**：一个部分可能属于多个整体。
- **特化**：从更一般的类形成一个或多个特定类（子类）。
- **状态**：对象在某一时点的属性。
- **子集约束**：限制一个关联的实例集是另一个关联的子集。
- **异或约束**：角色（关联端）之间的互斥或约束。

| 构造及示例 | 说明/注释 |
| :--- | :--- |
| **义务约束**<br>唯一性 ○<br>强制性 ○ ◎<br>子集、相等、排他 ⊆ ≡ ⊗<br>频率 ° f<br>非自反 ◌ 非循环 ◌<br>非对称 ◌ 非对称非传递 ◌<br>非传递 △ 非循环非传递 ◌<br>反对称 ◌ 对称 ◌<br>强非传递 △ 等等。<br>例如，[图：人是某人的父母] | 与真理约束不同，义务约束形状着色为蓝色而非紫色。大多数包含“o”表示“强制性”。义务环约束使用虚线。<br><br>在父母关系示例中，真理频率约束确保每个人最多有两个父母，真理环约束确保父母关系是非循环的，而义务环约束使得父母关系必须是强非传递的。 |
| **文本约束**<br>新受雇 [员工 (.Nr)] 被分配到¹ [项目 (.Name)]<br>¹ 每个新受雇的员工最多被分配一个项目。 | 没有图形表示的一阶约束可以在 FORML 2 语言中以文本形式表达。此示例使用脚注来捕获受限唯一性约束。 |
| **派生约束**<br>例如：<br>○ —<br>—<br>⊖<br>⊗<br>◌ | 派生约束着色为绿色。<br><br>此表示法在 Visio ORM 图形模板中受支持，但目前在 NORMA 中不受支持。 |

![](img/1344db3eba3d550e6edb009556fcd95c_1044_0.png)

![](img/1344db3eba3d550e6edb009556fcd95c_1044_1.png)

![](img/1344db3eba3d550e6edb009556fcd95c_1044_2.png)

![](img/1344db3eba3d550e6edb009556fcd95c_1044_3.png)

多重性：
- 0 个或更多
- 0..1 0 个或 1 个
- 1..* 1 个或更多
- 1 恰好 1 个
- n..m 至少 n 个且至多 m 个
- 默认属性多重性 = 1
- 默认关联角色多重性 = *

![](img/1344db3eba3d550e6edb009556fcd95c_1044_4.png)

![](img/1344db3eba3d550e6edb009556fcd95c_1045_0.png)

![](img/1344db3eba3d550e6edb009556fcd95c_1045_1.png)

![](img/1344db3eba3d550e6edb009556fcd95c_1045_2.png)

![](img/1344db3eba3d550e6edb009556fcd95c_1045_3.png)

![](img/1344db3eba3d550e6edb009556fcd95c_1045_4.png)

![](img/1344db3eba3d550e6edb009556fcd95c_1045_5.png)

![](img/1344db3eba3d550e6edb009556fcd95c_1045_6.png)

![](img/1344db3eba3d550e6edb009556fcd95c_1045_7.png)

![](img/1344db3eba3d550e6edb009556fcd95c_1045_8.png)

![](img/1344db3eba3d550e6edb009556fcd95c_1045_9.png)

本页故意留空

## ER 术语表

本术语表列出了第 8 章中讨论的 Barker ER 表示法、ER 的信息工程表示法和 IDEF1X 表示法中使用的关键符号。

### Barker ER 表示法

实体类型 A
属性
a1 .. a4

* a1
* a2
* a3
o a4

= 主标识符 [组件]
* = 强制性属性
o = 可选属性

A 通过关系 R1 与 B 相关

反向：
B 通过关系 R2 与 A 相关

强制性角色
______

可选角色
..........

多对一
>---------

关系 R 是 A 的识别方案的一部分

互斥弧

A 最多扮演
这些角色之一

A 恰好扮演
这些角色之一

A 被划分为 B 和 C

即：
B 和 C 是 A 的子类型
B 和 C 互斥
B 和 C 合起来穷尽 A

不可转让关系

### 信息工程表示法

实体类型 A
属性 a1 .. a3

| A |
|---|
| a1 |
| a2 |
| a3 |

![](img/1344db3eba3d550e6edb009556fcd95c_1048_0.png)

A 通过关系 R 与 B 相关

0 个或更多
0 个或 1 个
1 个或更多
恰好 1 个

例如：

![](img/1344db3eba3d550e6edb009556fcd95c_1048_1.png)

每个人恰好占用一个房间。
每个房间由 0 个或更多人占用。

互斲或

![](img/1344db3eba3d550e6edb009556fcd95c_1048_2.png)

每个 A 与 B 或 C 中恰好一个扮演 R

A 被划分为
子类型 B 和 C

| B |
|---|
| C |

或

![](img/1344db3eba3d550e6edb009556fcd95c_1048_3.png)

### IDEF1X 表示法

### 实体类型

A
[矩形]

标识符独立

B
[圆角矩形]

标识符依赖

| 员工 | | |
|---|---|---|
| empNr | ...... | 主键 |
| empName | | |
| ssn (AK1) | ...... | 备用键 |
| fax (O) | ...... | 可选 |
| roomNr (FK) | ...... | 外键 |

### 连接关系

●─────── 标识性

● - - - - 非标识性

●─────── 0 个或更多

● Z ──── 0 个或 1 个

● P ──── 1 个或更多

● n ──── 恰好 n 个

[子项: a (FK), b] ●── R ── [父项: a]

父项通过关系 R 与子项相关

[子项] ● - - - [父项]

每个子项恰好有一个父项

[子项] ● - - - ◇ [父项]

每个子项最多有一个父项

```
[A]
  ○
 / \
B   C
```

不完全、互斥子类型簇

```
[A]
  ◯
═══
 / \
B   C
```

完全、互斥子类型簇

本页故意留空

## 有用网站

https://www.elsevier.com/books-and-journals/book-companion/9780443237904.
本书的 Morgan Kaufmann 网站；包含在线附录。

### 面向事实的建模（一般）

- www.orm.net. Terry Halpin 的 ORM 网站。
- www.ormfoundation.org. ORM 基金会网站
- https://geverest.umn.edu/. Gordon Everest 的网站。包含指向 ORM 讲座的链接。
- https://everestdm.blogspot.com/. Gordon Everest 关于数据建模的博客。
- www.pna-group.com. PNA Group：面向事实建模的荷兰咨询公司。

### 面向事实的建模工具

- NORMA (ORM2 工具)。https://ormsolutions.com/ 或 https://sourceforge.net/projects/orm。有关安装和使用 NORMA 的详细信息，请参阅 www.orm.net 上的资源页面。
- NORMA Pro 具有多页关系模式和正式推导规则支持等附加功能。有关详细信息，请联系 Matt Curland，电子邮件 mcurland@live.com。
- 本书中大多数 ORM 模式图是使用 www.orm.net/ORM2_Draw2v25.zip 上提供的 Visio 图形模板和文件模板绘制的。这些文件是免费的，但需要标准版或专业版 Microsoft Visio 才能运行。
- CaseTalk (FCO-IM 工具)。https://www.casetalk.com。
- 基于 CogNIAM 的 iKnow 工具。www.pna-group.com。
- ActiveFacts (ORM 2 工具)。http://dataconstellation.com/ActiveFacts/。
- Boston。https://www.factengine.ai/。

### 业务规则、数据管理和数据架构框架

- www.brcommunity.com/index.php. 业务规则杂志。
- www.dama.org/. DAMA 国际组织。
- https://en.wikipedia.org/wiki/Zachman_Framework. Zachman 框架。
- https://zachman-feac.com. Zachman 国际组织和 FEAC 研究所。
- www.opengroup.org/togaf/. 开放组架构框架。
- http://committee.iso.org/sites/jtc1sc7/home/projects/flagship-standards/isoiec-10746.html. ISO RM-ODP 观点框架。

