

最近，GraphQL 作为一种 API 查询语言，引起了图数据库 [16,17] 和语义网 [18,19,20,21] 两个社区的关注。

语义网社区对 GraphQL 的关注主要集中于查询翻译工具的开发 [18,20,21]。这些工具将 GraphQL 查询翻译为 SPARQL 查询，然后发送到三元组存储（triple store）执行。此类解决方案的一个缺点是，三元组存储产生的结果需要被重写，因为 GraphQL 规定了严格的响应格式。这一过程会给查询执行带来显著的开销 [18, Table 3]，尤其是在结果集较大的情况下。据我们所知，目前还没有公开可用的、将 GraphQL 作为一等公民（first-class citizen）对待的三元组存储。

虽然大多数用于处理基本图模式的构造方法可以直接用于 GraphQL 处理，但 GraphQL 的形式语义 [22] 要求使用左连接（left-join）操作来求值 GraphQL 查询。然而，传统的两路左连接操作并不适合求值 GraphQL 查询，因为这类查询的结果可以增量构建 [22]。因此，我们专注于提出一种新颖的多路左连接算法，其灵感来源于最坏情况最优连接算法（worst-case optimal join algorithms）[23]，可用于增量枚举 GraphQL 查询。通过将我们的方法实现到一个最先进的三元组存储中，我们提供了第一个公开可用的、将 GraphQL 查询作为一等公民对待的三元组存储。我们使用合成基准生成器 LinGBM [24] 进行了广泛的评估，结果表明我们的实现能够优于提供 GraphQL 支持的先进图存储解决方案，即 Neo4j。

本文其余部分的结构如下。第 2 节给出预备知识。在第 3 节中，我们提出多路左连接算法，并展示如何原生地（natively）对 RDF 图求值 GraphQL 查询。我们在第 4 节评估我们的方法。第 5 节讨论相关工作，第 6 节总结全文。

## 2. 预备知识

在此，我们介绍本文所使用的 GraphQL 概念和语义，以及它们按照 [22] 给出的形式化定义。我们还简要介绍最坏情况最优多路连接算法，该算法启发了我们提出的算法。

### 2.1. GraphQL

GraphQL 是一种为简化客户端与应用服务器之间的通信而设计的查询语言。GraphQL 的主要特征之一是强类型。GraphQL 服务——即可通过 GraphQL 操作访问和修改其数据的服务器和数据源——会向客户端公开一个 GraphQL schema，传入的请求必须遵守该 schema。该 schema 定义了一个类型系统，它描述了 GraphQL 服务底层数据的结构以及服务所支持的操作。GraphQL 的另一个重要方面是其操作和响应的层次结构。GraphQL 操作形成一棵树结构，该结构指定了在底层图上的遍历方式，以及遍历每一步应从节点中提取的信息。相应地，响应应遵循各自操作所定义的层次结构。GraphQL 的语法和能力以及 GraphQL 服务的职责在语言的官方规范 [25] 中有详细说明。尽管该规范描述了服务应如何处理其接收到的请求，但它并未提供该语言语义的形式化规范。因此，研究该语言的表现力和复杂性仍然是一项挑战。为了应对形式语义缺失及其后果，Hartig 和 Pérez [22] 为由字段（fields）、字段别名（field aliases）和内联片段（inline fragments）组成的 GraphQL 查询提供了形式语义。这些语义依赖于 GraphQL schema 和图的形式化定义，以及 GraphQL 查询的形式化语法。在此，我们重新介绍 [22] 中给出的定义。

下面给出的形式化定义依赖于以下集合。设 Fields 为无限集，表示字段名，F ⊂ Fields 为 Fields 的有限子集。设 A 和 T 分别为有限的参数名集合和类型名集合，其中 T 是 O_T（对象类型名）、I_T（接口类型名）、U_T（联合类型名）和 Scalars（标量类型名）的不相交并集。最后，设 L_T = {[t] | t ∈ T} 为基于 T 构造的列表类型集合，Vals 为标量值集合。

**定义 2.1（GraphQL schema [22]）** 一个基于 (F,A,T) 的 GraphQL schema S 由以下组件组成：

- fields_S : (O_T ∪ I_T) → 2^F，为每个对象类型和每个接口类型分配一组字段，
- args_S : F → 2^A，为每个字段分配一组参数，
- type_S : F ∪ A → T ∪ L_T，为每个字段和参数分配一个类型或列表类型，其中参数被分配标量类型，
- union_S : U_T → 2^O_T，为每个联合类型分配一个非空的对象类型集合，
- impl_S : I_T → 2^O_T，为每个接口分配一组对象类型，
- root_S ∈ O_T，表示查询根类型。

**示例 2.1** 考虑以下 GraphQL schema S

```
interface Entity {
  id:String
  email:String
}
type Person impl Entity {
  id:String
  fname:String
  lname:String
  email:String
  age:Int
}
type Company impl Entity {
  id:String
  name:String
  email:String
  employees:[Person]
}
type Query {
  people(lname:String):[Person]
  companies:[Company]
}
schema { query:Query }
```

设 F = { people, companies, employees, fname, age, id, lname, email, name }，A = { lname }，O_T = { Query, Company, Person }，I_T = { Entity }，U_T = {}，Scalars = { String, Int }。GraphQL schema S 在 (F,A,T) 上形式化如下（为简洁起见，我们省略若干赋值）：

args_S(people) = {lname}, fields_S(Entity) = {id, email}, type_S(id) = String, fields_S(Person) = {id, fname, lname, email, age}, root_S = Query.

在实践中，GraphQL 服务实现于采用不同数据模型（例如关系数据库和图数据库）的数据源之上。为了以统一的方式提供 GraphQL 查询的语义，Hartig 和 Pérez [22] 引入了 GraphQL 图（GraphQL graph）的概念。GraphQL 图是抽象 GraphQL 服务底层数据源的逻辑构造。

**定义 2.2（GraphQL 图 [22]）** 一个基于 (F,A,T) 的 GraphQL 图是一个元组 G = (N,E,τ,λ,ρ)，包含以下元素：

- N 是节点集合，
- E 是形如 (u, f[a], v) 的边集合，其中 u, v ∈ N，f ∈ F，且 a 是从 A 到 Vals 的部分映射，
- τ : N → O_T 是一个为每个节点分配类型的函数，
- λ 是一个偏函数，它为某些形如 (u, f[a]) 的配对分配一个标量值 v ∈ Vals 或一个标量值序列 [v₁ ... vₙ]（vᵢ ∈ Vals），其中 u ∈ N，f ∈ F，且 a 是从 A 到 Vals 的部分映射，
- ρ ∈ N 是一个特殊的节点，称为根节点（root node）。

**定义 2.3（GraphQL 查询 [22]）** 一个基于 (F,A,T) 的 GraphQL 查询是由以下文法构造的表达式 φ，其中 [, ], {, }, : 和 on 是终结符，t ∈ O_T ∪ I_T ∪ U_T，f ∈ F，ℓ ∈ Fields，α 是从 A 到 Vals 的部分映射：

φ ::= f [α] | ℓ : f [α] | on t {φ} | f [α]{φ} | ℓ : f [α]{φ} | φ φ .

**示例 2.2** 符合示例 2.1 中 GraphQL schema S 的 GraphQL 查询示例如下：

```
φ₁ = people(lname: "Doe") { fname email } and
φ₂ = companies { name employees { id lname } } .
```

这两个查询都展示了 GraphQL 查询的层次结构。例如，φ₂ 在第一层访问属于对象类型 Company 的字段。在第二层，它访问对象类型 Person 的字段，因为 type_S(employees) = [Person]。

特别值得关注的是那些非冗余（non-redundant）且处于基类型范式（ground-typed normal form）的 GraphQL 查询。根据 [22, Theorem 3.8]，每个 GraphQL 查询都可以转换为等价的非冗余且处于基类型范式的查询。这类查询的一个重要特征是，其响应可以在不进行字段收集（field collection）[25, Section 6.3.2] 的情况下构建。这使得处于基类型范式的非冗余 GraphQL 查询能够在线性时间内完成求值，该时间与响应大小成正比 [22, Corollary 4.3]。

**定义 2.4（GraphQL 语义 [22]）** 设 G = (N,E,τ,λ,ρ) 是一个 GraphQL 图，φ 是处于基类型范式的非冗余 GraphQL 查询，两者都符合基于 (F,A,T) 的 GraphQL schema S。φ 在 G 上从节点 u ∈ N 开始的求值，记为 ⟦φ⟧_G^u，由公式 1 给出。φ 在 G 上的求值，记为 ⟦φ⟧_G，即为 ⟦φ⟧_G^ρ。

