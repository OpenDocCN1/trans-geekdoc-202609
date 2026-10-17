
在 Manchester 语法中，（如果有的话）仅通过 `R` 与指定子范围 `D` 中的值相关联的所有元素的集合简单地表示为“`R` only `D`”。作为选项 (3) 的示例，给定前面对 `drives` 谓词和 `Car` 子类的声明，以下 OWL 代码将 `CarOnlyDriver` 定义为仅驾驶属于汽车的车辆的人的类。此子类型包括那些根本不驾驶任何车辆的人。

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

由两个以上谓词出现组成的属性链也是被允许的。例如，以下声明允许从三个相关的父母事实推断出曾祖父母事实。例如，给定事实：爱德华七世是乔治五世的父母，乔治五世是乔治六世的父母，乔治六世是伊丽莎白二世的父母，我们可以推导出爱德华七世是伊丽莎白二世的曾祖父母这一事实。

```
ObjectProperty: isaGreatGrandparentOf
SubPropertyChain: isaParentOf o isaParentOf o isaParentOf
```

作为包含三个不同谓词的属性链示例，以下声明捕获了如下推导：如果一个人驾驶一辆由特定公司制造的车型的汽车，则该人驾驶由该公司制造的汽车。

```
ObjectProperty: drives
Domain: Person
Range: Car
ObjectProperty: isOfCarModel
Domain: Car
Range: CarModel
ObjectProperty: isMadeBy
Domain: Car
Range: CarModel
ObjectProperty: drivesCarMadeBy
SubPropertyChain: drives o isOfCarModel o isMadeBy
```

在处理属性链公理时，OWL 包含形式化限制以 `避免循环推理`，因为这可能导致可判定性问题。我们现在考虑一个例子。一般来说，叔叔要么是父母的兄弟，要么是姑姑/姨妈的丈夫。*血缘叔叔关系* 可以定义如下：给定人 *x* 和 *y*，如果 *x* 是 *y* 的父母的兄弟，则 *x* 是 *y* 的血缘叔叔。现在，假设我们也按如下方式定义兄弟关系：给定人 *x* 和 *y*，如果 *x* 是 *y* 的孩子的血缘叔叔，则 *x* 是 *y* 的兄弟。这些推导规则可以在 OWL 中按如下方式指定。

```
ObjectProperty: isaBirthUncleOf
SubPropertyChain: isaBrotherOf o isaParentOf
ObjectProperty: isaBrotherOf
SubPropertyChain: isaBirthUncleOf o isaChildOf
```

请注意，兄弟关系的推导规则调用了血缘叔叔关系谓词，而后者本身又依赖于兄弟关系。因此，这些推导规则组合在一起涉及一个恶性循环。在 OWL 中，这种属性链组合是非法的。

## OWL 本体与典型数据库的某些差异

在 OWL 2 中，命名个体由 IRI 标识。OWL 2 还允许未命名或 *匿名个体* （对应 RDF 中的空白节点），它们可以通过以下划线开头的本地 *nodeID* 在给定本体内被引用，例如 `_:x` 或 `_:p1`。以下示例断言了一位台湾女性总统的存在，使用 nodeID `_:p1` 来表示此人。

```
Individual: _:p1
Types: Woman
Facts: isPresidentOf Taiwan
```

在关系数据库中，个体通常由简单或复合名称标识，因此通常不支持像上述那样的存在性断言，尽管我们可以存储暗示它们的具体事实，例如蔡英文是女性且是台湾总统。

从逻辑角度来看，IRI 对应于个体常量，而非关系数据库中通常意义上的名称。为了说明 OWL 基于 IRI 的标识方案与数据库系统使用的基于值的标识方案有何不同，请考虑以下声明：

```
DataProperty: hasCountryCode
Domain: Country
Range: xsd:string
Class: Country
SubClassOf: hasCountryCode exactly 1
Individual: Australia
Types: Country
Facts: hasCountryCode "AU"
Individual: Germany
Types: Country
```

在这里，我们断言德国是一个国家，但没有为其显式提供国家代码。这在信息模型或关系数据库中是不允许的，因为我们声明的“每个国家都有一个国家代码”被实现为完整性约束，禁止没有国家代码的国家存在。

相反，OWL 允许这样做，因为“每个国家都有一个国家代码”这一声明 *仅被解释为一个命题，而非约束*。该命题可以形式化为逻辑公式 ∀*x*(Country *x* → ∃*y x* hasCountryCode *y*)。因为我们断言德国是一个国家，系统推断德国有一个国家代码，只是目前未知。这在 OWL 中是被允许的，OWL 采用开放世界语义并允许匿名个体。

还请注意，如果我们添加数据属性 `hasCountryName`，OWL 无法在 `hasCountryCode` 或 `hasCountryName` 关系中选择一个作为首选引用方案，因为主键和备选键之间的任何区别都丢失了。

`InverseFunctional` 声明适用于任何类型的个体（命名个体、匿名个体以及由存在量化隐含存在的个体）。然而，*HasKey 声明的唯一性方面仅适用于命名个体*（由 IRI 显式命名的个体）。假设我们以常规方式声明对象属性 `wasBornInCountry` 和数据属性 `hasCountryCode`，然后添加以下声明。

```
Class: Country
SubClassOf: hasCountryCode exactly 1
HasKey: hasCountryCode
```

我们现在可以断言朱莉娅·吉拉德（澳大利亚前总理）出生在某个国家代码为“GB”的国家，而无需知道该国家的名称，如下所示：

```
Individual: JuliaGillard
Facts: wasBornInCountry _:c1
Individual: _:c1
Facts: hasCountryCode “GB”
```

现在，假设我们发现英国的国家代码是“GB”（ISO 基于长名“The United Kingdom of Great Britain and Northern Ireland”选择的）。使用 `TheUK` 作为英国的直观 IRI，我们现在可以断言英国的国家代码是“GB”，如下所示：

```
Individual: TheUK
Facts: hasCountryCode "GB"
```

人们可能会期望可以正确推断出朱莉娅·吉拉德出生在英国这一事实，这可以表示为：

```
Individual: JuliaGillard
Facts: wasBornInCountry TheUK
```

然而，这个事实**并不成立**！这是因为 `Country` 的 `HasKey` 声明仅适用于命名个体（那些显式断言了 IRI 的个体），同时允许朱莉娅·吉拉德可能出生在许多未命名的国家中。

## OWL 中的否定事实和一元事实

类似于 OWL 对类和数据范围使用“not”作为补运算符的方式，OWL 允许你通过声明 *NegativePropertyAssertion* 来显式断言命题的 *否定*。Manchester 语法在个体的 Facts 槽中相关谓词对象对之前使用逻辑 **not** 运算符。考虑 ORM 事实类型“科学家出生于国家”。这纯粹用于记录哪位科学家出生在哪个国家。假设我们知道牛顿出生在英格兰，虽然我们不知道爱因斯坦出生在哪里，但我们知道他**不是**出生在英格兰。OWL 允许我们如下断言肯定事实和否定事实：

```
ObjectProperty: wasBornIn
Domain: Scientist
Range: Country
Characteristics: Functional
Individual: Newton
Facts: wasBornIn England
Individual: Einstein
Facts: not wasBornIn England
```

将这种方法与典型数据库的封闭世界方法进行对比，在后者中，任何未被断言也未被推导的事实都被假定为假。前面的例子否定了一个对象属性。数据属性可以用类似的方式否定。例如，将 IQ 视为数字，我们可以断言爱因斯坦的 IQ 不等于 100，如下所示：

```
DataProperty: hasIQ
Domain: Scientist
Range: xsd:nonNegativeInteger
Characteristics: Functional
Individual: Einstein
Facts: not hasIQ 100
```

OWL 采用开放世界假设，因此如果一个事实既未被断言也未被蕴含，则它是未知的。Hercule Poirot、Captain Hastings 和 Inspector Japp 是阿加莎·克里斯蒂小说中的人物。*Unary facts*（例如，Poirot smokes）及其*否定*（例如，Hastings does not smoke）在 OWL 中必须重新建模为二元关系，将主语关联到一个对象，该对象要么是布尔值（true 或 false），要么是具有两种可能性的状态值（例如，“Smoker”、“NonSmoker”）。

例如，以下 OWL 声明断言 Poirot 吸烟，Hastings 不吸烟，并将 Japp 是否吸烟留作*未知*。在 ORM 中，此示例将使用一元事实类型 Person smokes 在开放世界假设下并带有否定语义进行建模。

```
DataProperty: isaSmoker  Domain: Person  Range: xsd:boolean
Characteristics: Functional
Individual: Poirot  Facts: isaSmoker true
Individual: Hastings  Facts: isaSmoker false
Individual: Japp  Types: Person
```

### 外部唯一性约束的连接语义

具有*内连接*语义的外部唯一性约束可以在 OWL 中通过简单地在被引用类上使用复合 `HasKey` 属性来声明。回顾 Fig. 18.25，其中每个房间通过将其本地房间号与其建筑物相结合来标识，并使用了此 OWL 代码作为复合引用方案。

```
Class: Room
  SubClassOf: isInBuilding exactly 1
  SubClassOf: hasRoomNr exactly 1
  HasKey: isInBuilding, hasRoomNr
```

在 OWL 中捕获具有*外连接语义*的外部唯一性约束需要更多工作。通常，这将涉及*为不扮演相关可选角色的实例引入一个子类，然后为该子类声明一个 HasKey 属性*。为了确保 `HasKey` 声明生效，必须*为被引用实例包含 IRI*。

Fig. 18.28 再现了 Section 10.1 中的一个示例。该外部唯一性约束具有*外连接语义*，并附带一个条件：*外连接产生的空值被视为实际值*。因此，除了由其课程代码标识外，每个由部门开设的课程还可以由其课程标题和部门的组合来引用，例如 (Mechanics, PY) 和 (Mechanics, MA)。每个未由任何部门开设的课程可以由其代码或标题来标识。

![Fig. 18.28 (a) An external UC with outer join semantics; (b) the relational schema.](img/f18-28-9780443237904.jpg)

Fig. 18.28 (a) An external UC with outer join semantics; (b) the relational schema.

添加课程 NDC4，其标题与课程 ND3 相同均为 "Mechanics"，将违反外部唯一性约束。假设对象属性和数据属性以常规方式声明，该外部唯一性约束的外连接语义可以用 Manchester 语法捕获，如下所示。添加了子类 `NonDepartmentalCourse` 用于未由任何部门开设的课程，并为其声明 `hasCourseTitle` 为 `HasKey` 属性。

```
Class: Course
  SubClassOf: hasCourseTitle exactly 1 xsd:string, hasCourseCode exactly 1 xsd:string
  HasKey: hasCourseCode
Class: Department
  SubClassOf: hasDepartmentCode exactly 1 xsd:string
  HasKey: hasDepartmentCode
Class: NonDepartmentalCourse
  EquivalentTo: Course and (isOfferedBy max 0 Department)
  HasKey: hasCourseTitle
```

如果我们添加 Fig. 18.28 中所示的测试数据，这将违反非部门课程可由其标题标识的 `HasKey` 条件，因为两个非部门课程 NDC3 和 NDC4 将拥有相同的标题 "Mechanics"。

### ORM 到 OWL 的映射

最近的研究工作调查了从 ORM、UML 和 ER 中的概念模型到 OWL 以及其他基于描述逻辑的语言的映射。OWL 2 的直接形式语义基于描述逻辑 SROIQ (D)。ORM 的大部分内容可以干净地映射到这些描述逻辑，从而促进了基于 DL 的高效定理证明器用于 ORM 模式的一致性检查，以及与其他语义 Web 应用程序的互操作性。与 OWL 2 不同，ORM 具有整洁的一阶形式化，因此避免了关于类型作为实例的问题。然而，一些 ORM 结构和约束无法在 OWL 中捕获。这既有好处也有坏处。

从好的方面来看，ORM 能够以自然的方式捕获现实中几个常见于业务领域但无法在流行的描述逻辑中捕获的复杂方面。因此，ORM 能够实现典型业务领域的高保真建模。

从负面来看，ORM 表达能力太强，以至于其底层逻辑稍微超出了可判定的一阶逻辑片段。这使得难以高效地自动检查诸如模式可满足性等方面（例如，在包含数百万个约束的超大模式中，检查没有任何约束相互矛盾）。

这又是表达能力与可处理性之间权衡的另一个例子。语言越具表达力，就越难高效地验证用该语言表达的模型的逻辑一致性。因为我们应该确保模型准确反映其旨在建模的业务领域，所以似乎合理的做法是：在 ORM 等语言中捕获预期语义，在可能的情况下应用高效的自动检查，并对其余部分使用启发式技术。
