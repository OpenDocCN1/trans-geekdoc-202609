
将此示例与以下声明进行对比，后者基于官方 OWL 2 Primer 中的示例。此处，类 `Grandfather` 只是被断言，而非被定义。相反，它仅被约束为包含在（而非等同于）`Man` 和 `Parent` 类的交集中。并非所有作为父母的男性都是祖父。

```
Class: Grandfather SubClassOf: Man and Parent
```

回顾一下，集合 *A* 的*补集*是全集中不在集合 *A* 内的所有元素的集合。在 OWL 中，补集运算符可应用于类或数据范围，所得的复杂类表达式或数据范围表达式可用于任何可使用简单类或数据范围的地方。

一个类的补集包含不是该类成员的每个个体。在 Manchester 语法中，补集运算符显示为 `not`。例如，类 `NonHuman` 可定义为类 `Human` 的补集，如下所示：

```
Class: Human
Class: NonHuman EquivalentTo: not Human
```

下面 `NonDriver` 类的定义是另一个示例：

```
Class: Person
Class: Driver EquivalentTo: Person and drives min 1 Car
Class: NonDriver EquivalentTo: Person and not Driver
```

到目前为止的所有示例都使用了类。在 OWL 2 中，并集、交集和补集运算也可应用于数据范围。例如：

```
Datatype: StringOrInteger EquivalentTo: xsd:string or xsd:integer
Datatype: PassGradeNr EquivalentTo: GradeNr and not FailGradeNr
```

### 自反、非自反、对称、非对称和传递谓词

在 OWL 中，所有属性均为二元谓词。如果定义域和值域相同或兼容，则可比较主语和宾语实例。在 ORM 中，此类谓词称为*环谓词*，专门适用于它们（或更普遍地，兼容角色对）的约束称为*环约束*。

ORM 包含多种环约束的图形表示法，其中一些只是被简单定义（如非自反、非对称），而另一些则是递归定义的（如非循环、强非传递）。OWL 2 仅支持环谓词的以下五种限制：自反、非自反、对称、非对称和传递。其中，OWL 1 仅支持对称和传递。与 ORM 不同，OWL 仅允许将环谓词的限制应用于对象属性表达式，而不适用于数据属性表达式。

当且仅当关系 *R* 的定义域中的每个个体都与自身保持关系 *R* 时，该关系 *R* 为*自反*。如果定义域为 `owl:Thing`，唯一可能为自反的谓词是恒等关系“=”。

OWL 允许通过将对象属性表达式表征为*自反属性*来声明其为自反。在 Manchester 语法中，我们将“Reflexive”声明为一种特征。例如，如果每个人都知道自己，“knows”谓词可声明为自反，如下所示：

```
ObjectProperty: knows
Domain: Person
Range: Person
Characteristics: Reflexive
```

鉴于此，可进行以下推理：

*   ```
    Individual: Einstein
    ```

*   Types: Person → Individual: Einstein Facts: knows Einstein.

*   ```
    Individual: Terry
    ```

*   Facts: knows Tony → Individual: Terry Types: Person

*   Individual: Tony Types: Person

作为并集定义域的示例，以下 `isAsOldAs` 谓词的声明断言每个 `Person`、每个 `Cat` 和每个 `Dog` 都与自身年龄相同。

```
ObjectProperty: isAsOldAs
Domain: Person or Cat or Dog
Characteristics: Reflexive
```

当且仅当没有个体能与自身保持关系 *R* 时，环谓词 *R* 为*非自反*。例如，父母关系是非自反的，因为没有任何事物能成为其自身的父母。OWL 通过将对象属性表达式表征为*非自反属性*来声明其为非自反。在 Manchester 语法中，我们将“Irreflexive”声明为一种特征。例如，`isaParentOf` 谓词声明为非自反，如下所示。随后任何断言某人是其自身父母的行为都会导致 OWL 本体不一致。

```
Class: Person
ObjectProperty: isaParentOf
Domain: Person
Range: Person
Characteristics: Irreflexive
```

当且仅当 ∀*x*∀*y*(*xRy* → *yRx*) 时，环谓词 *R* 为*对称*；即对于每个个体 *x* 和 *y*（不必不同），若 *xRy* 则 *yRx* 也成立。例如，兄弟姐妹关系是对称的，因为如果一个人是另一个人的兄弟姐妹（兄/弟/姐/妹），则第二个人也是第一个人的兄弟姐妹。

OWL 通过将对象属性表达式表征为*对称属性*来声明其为对称。在 Manchester 语法中，我们将“Symmetric”声明为一种特征，例如，`isaSiblingOf` 可在 OWL 中声明为对称，如下所示。为完整起见，该谓词的非自反性质也被声明。

```
Class: Person
ObjectProperty: isaSiblingOf
Domain: Person
Range: Person
Characteristics: Symmetric, Irreflexive
```

在 OWL 中，若谓词被声明为对称，且我们断言了其事实实例，则可推断出其逆关系。例如，若我们添加以下声明：

```
Individual: Romulus
Facts: isaSiblingOf Remus
```

则可推断：

*   Individual: Remus Facts: isaSiblingOf Romulus.

在 ORM 中，将谓词约束为对称意味着断言的事实填充必须是对称的。例如，如果我们断言 Romulus 是 Remus 的兄弟姐妹，则必须同时断言 Remus 是 Romulus 的兄弟姐妹（两个事实均被存储）。然而在 OWL 中，你只需断言其中一个事实，另一个事实即可被推断。要在 ORM 中实现这一点，你需提供用于推断逆关系的推导规则，而非将事实类型约束为对称。

例如，在 ORM 中，你可将事实类型“Person is a sibling of Person”声明为*半派生*，意味着其部分实例可被断言，部分可被推导，并使用以下规则推导逆事实：Person[1] is a sibling of Person[2] **if** Person[2] is a sibling of Person[1]。在这种情况下，你会将兄弟姐妹事实类型约束为非自反，但不对称。

当且仅当对于每个个体 *x* 和 *y*（不必不同），若 *xRy* 则 *yRx* 不成立时，环谓词 *R* 为*非对称*。换言之，若关系成立，则其逆关系必不成立。例如，父母关系是非对称的，因为如果一个人是另一个人的父母，则第二个人不可能是第一个人的父母。

OWL 通过将对象属性表达式表征为*非对称属性*来声明其为非对称。在 Manchester 语法中，我们将“Asymmetric”声明为一种特征。例如，`isaParentOf` 谓词可在 OWL 中声明为非对称，如下所示。

```
Class: Person
ObjectProperty: isaParentOf
Domain: Person
Range: Person
Characteristics: Asymmetric
```

请注意，若谓词为非对称，则它自动也是非自反的（考虑 *x* = *y* 时非对称性的定义）。虽然非对称性蕴含非自反性，但反之不成立。例如，`isaSiblingOf` 是非自反的但非非对称。

若已声明上述非对称约束，且我们断言 Ann 是 Bill 的父母，则任何添加 Bill 是 Ann 的父母的事实的尝试都会导致 OWL 本体不一致。
