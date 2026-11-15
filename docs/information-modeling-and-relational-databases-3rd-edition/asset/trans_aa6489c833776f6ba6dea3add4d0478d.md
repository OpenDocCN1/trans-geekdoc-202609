

**对象化：** 将关系视为对象；也称为嵌套。严格来说，ORM 2 中的对象化区分了由对象化形成的对象和原始关系，因此涉及情境性而非命题性名词化。

**对象-角色建模（ORM）：** 概念建模方法，通过对象扮演角色来描绘业务领域；它提供图形和文本语言，用于口头化和查询信息以及各种设计和转换过程。

**人口：** 数据库特定状态下存在的实例集合。

**谓语：** 带有对象空位的命题，例如，“... 为 ... 工作”。

**原始对象类型：** 不是另一个对象类型子类型的对象类型。

**引用：** 用作引用或标识对象（或提供部分标识）的首选方式的关系。

**引用模式：** 单个值引用实体的模式或方式；用于缩写简单引用方案，例如 (Code)、(kg)。

**引用角色：** 引用中的角色（存在性事实）。也称为存在性角色。

**关系：** 涉及一个或多个对象的属性或关联。

**刚性子类型：** 其实例在整个生命周期内必须保留在该类型中的子类型（例如，Person）。

**Rmap：** 关系映射过程。

**角色：** 对象在关系中扮演的部分（一元、二元、三元等）。

**角色子类型：** 其实例在生命周期内可能离开该类型的子类型（例如，Child）。

**半派生事实类型：** 事实类型，其中某些实例可从其他实例推导而来，而其他实例则可能仅被断言。

**半派生子类型：** 子类型，其中某些实例可使用推导规则推导而来，而其他实例则可能仅被断言。

**子类型：** 正确包含在另一个对象类型中的对象类型（例如，Woman 是 Person 的子类型）。

**类型：** 可能实例的集合。

**唯一性约束（UC）：** 约束所覆盖的角色或角色序列中不允许重复；对单个谓语的唯一性约束是内部 UC，而对不同谓语中角色的唯一性约束是外部 UC。

**话语域（UoD）：** 业务领域（我们想要讨论的世界方面）。

**值：** 由常量标识的不可变对象。在本书中，值要么是字符串，要么是数字；有时称为标签。

以下符号术语表涵盖了 ORM 2 中的主要图形符号。它基于归 Terry Halpin 所有的标准 ORM 2 符号术语表，并经许可使用。

| 构造和示例 | 描述/注释 |
| :--- | :--- |
| **实体类型**<br>Country or Country or Country | 命名软矩形、命名硬矩形或命名椭圆。软矩形形状是默认值。 |
| **值类型**<br>CountryCode or CountryCode or CountryCode | 命名、虚线软矩形（或硬矩形或椭圆）。 |
| **具有常用引用模式的实体类型**<br>Country(.Code) Course(.Code) Company(.Name) Building(.Nr) | 对值类型的单射引用的缩写，例如<br>Country —(has / is of)— CountryCode |
| **具有基于单位的引用模式的实体类型**<br>Height (cm:) Mass (kg:) Salary (USD:) Price (EUR:)<br>Height (cm: Length) Salary (USD: Money) Price (EUR: Money) | 对引用类型的缩写，例如<br>Height —(has / is of)— cmValue<br>可选地，可以显示单位类型（如对面所示）。 |
| **具有常规引用模式的实体类型**<br>Book (ISBN) Website (URL) | 对引用类型的缩写，例如<br>Book —(has / is of)— ISBN<br>Website —(has / is of)— URL |
| **独立对象类型**<br>Country ! CountryCode ! | 该类型的实例可以存在，而无需扮演任何基本事实角色。 |
| **外部对象类型**<br>Address^ | 此表示法是暂定的，且不受 NORMA 支持。 |
| **谓语（一元、二元、三元等）**<br>smokes [ ] was born in [ ][ ] ... speaks ... well [ ][ ]<br>... played ... for ... [ ][ ] ... in ... on ... ate ... [ ][ ][ ] | 1个或多个角色框的有序集合，至少带有一个谓语读法。如果显示，对象占位符用“…”表示。如果未显示占位符，一元使用前缀表示法。二元使用中缀表示法。三元等使用混缀表示法。 |
| **重复类型或谓语形状**<br>Person [shadowed] StateCode [dashed shadowed] was born in [ ][ ] | 如果对象类型或谓语形状显示多次（在同一页面或不同页面上），则会被阴影化。 |
| **一元事实类型**<br>Person ▭ smokes<br>Person ▭ smokes [isSmoker] | 将角色框附加到对象类型形状意味着只有该对象类型的实例才能扮演该角色。角色名称可以添加在方括号中。 |
| **二元事实类型**<br>Person was born in Country<br>Person [employee] employs Company [employer]<br>Person made Product<br>Person reports to / manages Person<br>Car drives Person | 默认情况下，谓语读法（二元或更长）从左到右或从上到下读取。箭头尖端用于显示不同的读取方向。角色名称可以显示在其角色旁边的方括号中。二元的正向和逆向读法可以一起显示，并用“/”分隔。 |
| **三元事实类型**<br>Person [player] ... played ... for ... Country ... introduced ... to ... Sport<br>Person<br>Food Cat<br>Date ... on ... ate ... Cat ... Food ... Date<br>[Cat] ate [Food] on [Date] | 角色名称可以添加在方括号中。箭头尖端用于反转默认的左右或从上到下的读取顺序。除正向和逆向以外的读取顺序使用命名占位符显示。 |
| **四元事实类型**<br>City Date<br>Person ... in ... on ... ate ... Food | 上述关于三元情况的注释也适用于此。还允许具有更高元数（角色数量）的事实类型。 |
| **对象化（又称嵌套）**<br>"Enrolment !"<br>Student enrolled in Course<br>resulted in Grade<br>[ Enrolment ! ] | 注册*事实类型被对象化为实体类型，其实例可以扮演角色。在此示例中，对象化类型是独立的，因此我们可以在获得成绩之前了解注册情况。对象化对象类型也可以在没有其定义组件的情况下显示，使用包含小型谓语形状的对象类型形状，如所示。*此处使用澳大利亚拼写。* |
| **一元事实类型上的内部唯一性约束（UC）**<br>Diagram: Person - smokes | 这些示例是等效的。默认情况下，假设事实类型使用事实集合（而非事实多集）填充，因此不允许重复整个事实。 |
| **二元事实类型上的内部 UCs**<br>Diagrams: Gender/Person/Country and Language/Person/Country | 示例显示四种可能的模式：<br>1:n（一对多）；<br>n:1（多对一）；<br>m:n（多对多）；<br>1:1（一对一）。 |
| **三元事实类型上的内部 UCs**<br>Diagrams: Team/Competition/Place and Person/Country/Sport | 第一个示例有两个双角色 UC：顶部 UC 禁止平局。另一个 UC 确保每个团队在每次竞赛中最多获得一个名次（虚线将其角色从 UC 中排除）。第二个示例具有跨度 UC（多对多）。对于 n 元（n > 2）事实类型要为原子，其上的每个 UC 必须至少跨越 n-1 个角色。 |
| **简单强制角色约束**<br>Diagrams: Person and Country | 示例约束意味着每个人都出生在某个国家。强制角色点可以放在角色连接器的任一端。 |
| **包含或约束**<br>Diagram: Visitor, Passport, WorkVisa, Person | 包含或约束也称为析取强制角色约束。约束显示为连接受约束角色（或由同一对象类型托管的相邻角色的连接点）的圆点。第一个约束意味着模型中引用的每个访客必须持有护照或工作签证（或两者皆有）。第二个示例意味着每个人都是某人的父母或某人的子女（或两者皆有）。 |

