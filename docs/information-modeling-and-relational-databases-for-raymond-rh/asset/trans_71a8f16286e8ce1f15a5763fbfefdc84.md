
# 环谓词 *R* 是*传递的*当且仅当，对于每个个体 *x*、*y* 和 *z*（不必互异），如果 *xRy* 和 *yRz*，那么 *xRz* 也成立。例如，祖先关系是传递的，因为如果一个人是另一个人的祖先，而第二个人是第三个人的祖先，那么第一个人就是第三个人的祖先。

忽略转世因素，祖先谓词实际上是非循环的（一个对象永远不可能通过应用一个或多个祖先事实而循环回到自身）。与 ORM 不同，OWL 不支持非循环约束。然而，OWL 确实允许通过将对象属性表述为传递的来声明其为传递的。在 Manchester 语法中，我们将“Transitive”声明为一个特征来实现这一点。例如，`isanAncestorOf` 谓词可以被声明为传递的，如下所示。为保持完整性，该谓词的非对称性质也被声明了。

```
Class: Person
ObjectProperty: isanAncestorOf
  Domain: Person
  Range: Person
  Characteristics: Transitive, Asymmetric
```

在 OWL 中，将祖先谓词声明为传递的并不要求必须断言其所有实例。例如，如果你将谓词声明为传递的，并断言 Ann 是 Bill 的祖先，Bill 是 Chris 的祖先，那么 OWL 推理器可以推断出 Ann 是 Chris 的祖先。

## OWL 2 中的枚举类型

回顾一下，OWL 允许你通过指定已声明的类或数据类型上的操作来定义一个新类或数据类型的*内涵*（即含义）。指定一个项目成为类型成员的必要且充分条件的类型定义，被称为该类型的*内涵定义*。例如，假设引用的类型（`Student`、`Employee`、`GradeNr`、`FailGradeNr`）已预先声明，则 `StudentEmployee` 和 `PassGradeNr` 的内涵定义可以在 Manchester 语法中声明如下：

```
Class: StudentEmployee
  EquivalentTo: Student and Employee
Datatype: PassGradeNr
  EquivalentTo: GradeNr and not FailGradeNr
```

一个类型所有可能实例的集合被称为该类型的*外延*。如果一个类或数据范围由一个已知的、有限的项目集合组成，它可以通过*枚举*（即列出）这些项目来定义。例如，虽然 `EvenDigit` 可以内涵地定义为 {*x* | *x* 是能被 2 整除的数字}，但它也可以外延地定义为 {0, 2, 4, 6, 8} 的成员。通过枚举其外延来定义的类型被称为*枚举类型*，其定义被称为*外延定义*。在 Manchester 语法中，使用常规的集合符号来指定外延，用大括号作为集合定界符，用逗号作为元素分隔符，例如：

```
Class: Weekday
  EquivalentTo: { Monday, Tuesday, Wednesday, Thursday, Friday }
Datatype: EvenDigit
  EquivalentTo: {0, 2, 4, 6, 8}
```

## 谓词上的“值”限制

OWL 松散地使用术语“*值*”，意指个体实体或字面值。基于此理解，一个命名类或（未命名）类表达式可以被定义为某个谓词的主语，其范围被限制为包含以下三种选项之一：(1) 某个特定值；(2) 来自指定类或数据范围的某个值；(3) 仅来自指定类或数据范围的值。我们依次考察这些情况。

在 Manchester 语法中，通过二元关系 *R* 与值 *v* 相关联的所有元素的集合简单地表示为“*R* value *v*”。作为选项 (1) 的示例，如果我们将 `Gender` 视为包含两个个体（male 和 female）的枚举类，以下 OWL 代码将 `MalePerson` 定义为性别为 male 的人的类。

```
ObjectProperty: Person hasGender
  Domain: Person
  Range: Gender
Class: Gender
  EquivalentTo: { male, female }
Class: MalePerson
  EquivalentTo: Person and hasGender value male
```

在 Manchester 语法中，通过 *R* 与指定子范围 *D* 中的某个值相关联的所有元素的集合简单地表示为“*R* some *D*”。作为选项 (2) 的示例，以下 OWL 代码将 `CarDriver` 定义为开车的人的类。

```
ObjectProperty: drives
  Domain: Person
  Range: Vehicle
Class: Car
  SubclassOf: Vehicle
Class: Driver
  EquivalentTo: Person and drives some Car
```

在 Manchester 语法中，（如果有的话）仅通过 *R* 与指定子范围 *D* 中的值相关联的所有元素的集合简单地表示为“*R* only *D*”。作为选项 (3) 的示例，给定前面对 `drives` 谓词和 `Car` 子类的声明，以下 OWL 代码将 `CarOnlyDriver` 定义为仅驾驶属于汽车的车辆的人的类。此子类型包括那些根本不驾驶任何车辆的人。

```
Class: CarOnlyDriver
  EquivalentTo: Person and drives only Car
```

## OWL 2 中的属性链

OWL 2 允许你通过将两个或多个对象属性事实按链式组合，从而推导出一个新的对象属性事实，其中一个事实（最后一个事实除外）的客体位置上的实体也是下一个事实的主语。在关系数据库工作中，这对应于在两个基本关系之间执行等值连接，然后投影到链中的第一个和最后一个属性上。在 OWL 中，等值连接操作被称为*组合*操作，组合两个或多个谓词的表达式被称为*属性链*。

为了说明这一概念，考虑一个业务领域，其中每个人最多在一个城市出生（例如，有些人可能出生在村庄），而每个城市确切位于一个国家。使用 Manchester 语法在 OWL 中指定此模式的一种方法如下：

```
ObjectProperty: wasBornInCity
  Domain: Person
  Range: City
  Characteristics: Functional
ObjectProperty: isLocatedInCountry
  Domain: City
  Range: Country
Class: Person
  SubClassOf: wasBornInCity max 1
Class: City
  SubClassOf: isLocatedInCountry exactly 1
```

现在，假设我们也想知道人们出生在哪个国家。在 ORM 中，我们可以添加半派生事实类型 Person was born in Country，允许断言某些实例，并使用派生规则 Person was born in Country **if** Person was born in **some** Country **that** is located in **that** Country 来推导其他实例。

在 OWL 2 中，我们可以通过将 `wasBornInCountry` 谓词声明为由组合 `wasBornInCity` 和 `isLocatedInCountry` 谓词形成的属性链在首尾投影所得谓词的子属性，来指定派生规则。在 Manchester 语法中，属性链使用符号“o”作为链中相邻谓词之间的*组合运算符*，并列在“SubPropertyChain:”标题之后。我们当前的示例可以通过添加以下 OWL 代码在 Manchester 语法中指定：

```
ObjectProperty: wasBornInCountry
  Domain: Person
  Range: Country
  SubPropertyChain: wasBornInCity o isLocatedInCountry
```

子属性声明只是一个适用于任何满足模型的简单蕴含。OWL 不关心如何实际实现蕴含的选择。属性链可以组合同一谓词的多次出现。例如，祖父母事实可以通过组合两个父母事实来推导，如下所示。

```
ObjectProperty: isaGrandparentOf
  SubPropertyChain: isaParentOf o isaParentOf
```

如果父母事实的知识是不完整的，我们可能希望允许简单地断言某些祖父母事实，方法是添加以下声明。

```
ObjectProperty: isaGrandparentOf
  Domain: Person
  Range: Person
```
