
* 使用 `$tokenId` 等变量使你的 GraphQL 查询更灵活、更安全，允许通过简单地更改变量的值来重用相同的查询结构以获取不同代币的详情。

## 指令

GraphQL 中的指令用于修改查询、变更或字段的执行。它们可以根据你指定的条件更改字段的行为或包含情况。指令提供了一种动态更改查询或模式执行的方式，使其成为控制数据如何检索或操作的有力功能。

GraphQL 中主要有两种指令类型：

* **执行指令：** 这些在查询和变更中使用，根据变量值有条件地包含或跳过字段。最常见的执行指令是 `@include(if: Boolean)` 和 `@skip(if: Boolean)`。

* **模式指令：** 这些在模式定义中使用，以修改类型、字段或其他模式元素的行为。模式指令可以自定义定义，更为复杂，通常用于实现身份验证、授权或数据格式化等功能。

下面是一个示例，展示执行指令如何在 GraphQL 查询中使用：

```
query GetTokenDetails($tokenId: ID!, $includeVolume: Boolean!) { 
 token(id: $tokenId) { 
 name 
 symbol 
 address 
 volume @include(if: $includeVolume) 
 price 
 } 
}
```

在此查询中：

`@include(if: $includeVolume)` 是应用于 `volume` 字段的指令。

`$includeVolume` 是一个布尔变量，用于确定 `volume` 字段是否应包含在响应中。

执行此查询时，您可以通过将 `$includeVolume` 变量设置为 `true` 或 `false` 来动态决定是否获取成交量信息。

因此，指令提供了一种灵活的方法来修改查询的执行方式，并根据应用程序的需求或当前用户的权限塑造返回的数据。

## Mutations

在 GraphQL 中，`mutation` 是用于修改服务器数据的操作，例如创建、更新或删除记录。与用于获取数据的查询不同，`mutation` 会更改数据，并且通常返回新的或修改后的数据。

以下是 `mutation` 在 GraphQL 中如何定义和使用的基本结构：

```
mutation MutationName($input: InputType!) {
  operationName(input: $input) {
    field1
    field2
    …
  }
}
```

以下是演示如何使用 `mutation` 更新代币信息的示例：

```
mutation UpdateToken($id: ID!, $price: Float!, $volume: Int!) {
  updateToken(id: $id, price: $price, volume: $volume) {
    name
    symbol
    price
    volume
  }
}
```

在此示例中：

* `UpdateToken` 是 `mutation` 的名称。

* `$id`、`$price` 和 `$volume` 是传入 `mutation` 的变量，允许您动态指定要更新的代币的 ID 以及价格和成交量的新值。

* `updateToken` 是在服务器上调用的操作，它接受 `id`、`price` 和 `volume` 作为参数。

* `mutation` 返回更新后的代币 `name`、`symbol`、`price` 和 `volume`，更新操作完成后即可获得。

* 通过使用 `mutation`，您可以执行创建、读取、更新和删除（CRUD）操作以及更多操作，有效地通过 GraphQL API 更改服务器上存储的数据。此机制确保数据操作是有意且明确的，有助于 API 的健壮性和可靠性。

## Type System

GraphQL 类型系统是定义 GraphQL API 模式的基础。它指定可以通过 API 查询和操作的数据类型，确保客户端以一致且类型安全的方式与数据交互。以下是概述：

* `Scalar Types`：这些是 GraphQL 中的基本数据类型。它们包括 `Int`、`Float`、`String`、`Boolean` 和 `ID`。标量类型代表查询的叶子节点——它们描述返回的原始数据。

* `Object Types`：这些是 GraphQL 中最常用的类型，表示一组字段。`Object Type` 中的每个字段可以是任何类型，包括 `Scalar`、`Enum`、`Interface`、`Union`，甚至是另一个 `Object Type`。对象类型用于定义 API 返回的对象的形状。

示例：

```
type Token {
  id: ID!
  name: String!
  symbol: String!
  price: Float
  volume: Int
}
```

* `Enum Types`：枚举，或 `Enum Types`，将值限制为一组预定义值。它们对于只能采用特定值集的字段非常有用。

示例：

```
enum Currency {
  USD
  EUR
  BTC
}
```

* `Interface Types`：这些定义了一组字段；对象类型可以实现这些接口，这确保它们将包含这些字段。接口对于在多个对象类型之间定义公共字段非常有用。

示例：

```
interface Character {
  id: ID!
  name: String!
}
```

* `Union Types`：联合类型与接口类似，但它们不指定类型之间的任何公共字段。相反，它们用于表示一个字段可以返回有限的不同类型之一。

示例：

```
union SearchResult = Book | Author | Magazine
```

* `Input Types`：虽然常规对象类型定义了可以从 API 获取的对象的形状，但 `Input Types` 指定了当您将它们作为 `mutation` 和查询的参数发送时对象可能的样子。

示例：

```
input TokenInput {
  name: String!
  symbol: String!
  price: Float
  volume: Int
}
```

* `List Types and Non-Null Types`：这些是包装类型，用于修改其他类型的行为。列表用于表示值数组，而 `Non-Null` 类型用于指示字段绝不能返回 `null`。

示例：

```
type Query {
  tokens: [Token]    # List of Token objects
  token(id: ID!): Token!  # Non-Null Token object
}
```

GraphQL 类型系统确保模式清晰地定义了可以交互的数据、客户端如何查询它以及响应将采取的形式，为构建和查询 API 提供了稳健的框架。

## Adopting a Graph-Based Mindset

图在建模各种现实世界情况方面非常有效，因为它们反映了我们天生的心理模型和对过程的口头描述。在 GraphQL 中，您通过创建模式将业务域结构化为图。此模式概述了不同类型的节点及其相互连接。对于客户端来说，这种方法创造了一种类似于面向对象编程的模式，其中类型引用其他类型。在服务器端，GraphQL 仅定义接口，为您提供与任何后端集成的灵活性，无论是新的还是遗留的。

## Shared Language

将您的 GraphQL 模式视为连接团队与用户的统一语言。要设计有效的模式，请反思在讨论业务背景时常用的语言。例如，让我们用简单的术语描述一个加密货币钱包应用程序：

* 一个用户可以持有多种加密货币代币。

* 每个代币都有独特的属性，例如 `symbol`、当前价值和交易历史。

* 每次交易都会记录详细信息，例如发送者、接收者、金额和时间戳。

* 用户在发起交易之前必须拥有足够的代币余额。

选择合适的术语是开发直观 API 的一项具有挑战性但至关重要的任务。花时间仔细评估与您的领域产生共鸣且用户易于理解的术语。您的团队必须就这些概念达成共同理解和一致至关重要，因为您必须为 GraphQL 模式中的对象及其关系选择清晰且有意义的名称。请考虑您可能需要的查询类型，例如获取所有用户账户中特定加密货币代币的总余额。

```
query GetUserTokens {
  user(id: "123") {
    name
    tokens {
      symbol
      balance
      currentValue
    }
  }
}
```

在此查询中，我们正在请求一个用户（假设 ID 为“123”）并请求其姓名以及其拥有的代币列表。对于每个代币，我们获取 `symbol`、用户持有的余额以及代币的当前价值。

查询特定代币的交易历史：

```
query GetTokenTransactions {
  token(symbol: "BTC") {
    transactions {
      sender
      receiver
      amount
      timestamp
    }
  }
}
```

## Business Logic Layer

核心业务逻辑应放置在哪里？验证和授权应在何处进行？解决方案在于建立一个专门的业务逻辑层。该层应作为应用和维护业务域规则的中央权威。

![](img/Figure6.2.jpg)

**Figure 6.2:** Placement of Business Logic

### 在 Go 中实现 GraphQL API

让我们深入探讨使用 Go 编程语言实现 GraphQL API 的过程。凭借其强大的并发模型和高效率，Go 已成为构建健壮且可扩展的 GraphQL 服务器的理想选择。在本次探索中，我们将讨论如何选择最合适的 GraphQL 库，详细说明定义 GraphQL 模式的步骤，并指导您完成查询的解析。

在各种编程语言中，有许多可用于实现 GraphQL 的库。对于 Go，我们将使用 `graphql-go` [`github.com/graphql-go/graphql`](https://github.com/graphql-go/graphql)，这是一个流行且全面的库，专门为 Go 生态系统量身定制。此选择将使我们能够利用 Go 的优势，同时遵守 GraphQL 的标准和实践，确保无缝集成和有效的 API 开发。

要设置项目以使用 GraphQL 库，您需要在 Go 环境中安装该库。首先在终端中执行以下命令：

```
go get github.com/graphql-go/graphql
```

此命令将获取并安装 `graphql-go` 库，使其可在您的 Go 项目中使用。通过集成此库，您将获得一套全面的工具和功能，旨在促进在 Go 编程语言中开发 GraphQL API。确保您的项目已正确配置以识别此新依赖项，您就可以开始构建 GraphQL 服务器了。

#### GraphQL 模式

GraphQL 模式通过指定客户端如何获取或修改数据来定义 API 的功能。它充当客户端与服务器之间的契约，详细说明允许的查询和变更类型、它们返回的数据类型以及它们如何相互连接。

以下是代币的简单 GraphQL 模式示例：

```
type Query {
  token(id: ID!): Token
  tokens: [Token]
}

type Mutation {
  createToken(name: String!, symbol: String!, price: Float!): Token
  updateTokenPrice(id: ID!, newPrice: Float!): Token
  deleteToken(id: ID!): Token
}

type Token {
  id: ID!
  name: String!
  symbol: String!
  price: Float!
  volume: Float
}
schema.graphql
```

此模式包括以下内容：

* **类型**

  `Token` 是一个自定义类型，表示加密货币代币。它包括 `id`、`name`、`symbol`、`price` 和 `volume` 等字段。

* **查询**

  `token`：通过其 `id` 获取单个代币。

  `tokens`：检索所有可用代币的列表。

* **变更**

  `createToken`：允许使用指定的 `name`、`symbol` 和 `price` 创建新代币。

  `updateTokenPrice`：更新由 `id` 标识的现有代币的价格。

  `deleteToken`：使用其 `id` 从系统中删除代币。

此模式为您的 GraphQL API 奠定了基础，详细说明了客户端如何与您的加密货币代币数据交互。通过遵循此模式，您的 GraphQL 服务器可确保所有查询和变更都遵循预定义的类型和结构，从而在整个应用程序中维护数据完整性和一致性。接下来，我们将利用此模式构建解析器和变更。同时，我们将基于此模式开发服务器和客户端，确保对加密货币代币上下文中 GraphQL 操作的全面理解和实现。

我们已经在名为 `schema.graphql` 的文件中定义了 GraphQL 模式。此文件将由 GraphQL 服务器用于解析。基于此 GraphQL 模式，我们将创建相应的查询。

**注意**：GraphQL 在 HTTP 上运行，使其能够利用网络的内置功能。

```
schema := graphql.MustParseSchema(schemaAsString, resolver, graphql.UseFieldResolvers())
```

`schemaAsString`：这是我们之前定义过的模式。为了将其纳入此处，我们将读取 `schema.graphql` 文件的内容并传递其内容。

**解析器**：GraphQL 解析器是一个用于为模式中的类型或字段解析值的函数。解析器负责获取客户端请求的数据。实质上，每当查询命中一个字段时，该字段的解析器就会被调用以获取相应的数据。

让我们考虑一个加密货币上下文中 `Token` 类型的简单示例。假设我们的 GraphQL 模式中有以下类型：

```
type Token {
  id: ID!
  name: String!
  symbol: String!
  price: Float!
  volume: Float
}
```

Go 中的 Token 解析器：

```
package resolver
import (
  "context"
  "github.com/graph-gophers/graphql-go"
)
// Token data structure,
type Token struct {
  ID     string
  Name   string
  Symbol string
  Price  float64
}
// TokenResolver corresponds to a GraphQL resolver for the Token type.
type TokenResolver struct {
  t *Token // Assume this represents a specific cryptocurrency token.
}
// ID resolves the 'id' field for the Token type.
func (tr *TokenResolver) ID(ctx context.Context) (*string, error) {
  return &tr.t.ID, nil
}
// Name resolves the 'name' field for the Token type.
func (tr *TokenResolver) Name(ctx context.Context) (*string, error) {
  return &tr.t.Name, nil
}
// Symbol resolves the 'symbol' field for the Token type.
func (tr *TokenResolver) Symbol(ctx context.Context) (*string, error) {
  return &tr.t.Symbol, nil
}
// Price resolves the 'price' field for the Token type.
func (tr *TokenResolver) Price(ctx context.Context) (*float64, error) {
  return &tr.t.Price, nil
}
```

在此示例中，`TokenResolver` 是一个与 `Token` 关联的结构。每个方法，例如 `ID`、`Name`、`Symbol` 和 `Price`，都对应于 `Token` GraphQL 类型中的一个字段，并从关联的 `Token` 实例 (`tr.t`) 中解析数据。这些方法旨在在查询中请求相应字段时由 GraphQL 服务器调用。上下文参数 `ctx` 由 GraphQL 服务器提供，可用于在 API 边界之间传递请求范围的值、取消信号和截止时间。

然后您将在 Go 代码中为此查询实现解析器函数，该函数将使用 `TokenResolver` 来获取和返回代币数据。以下是假设您有一些按 ID 获取代币的函数的示例：

```
func (r *RootResolver) Token(ctx context.Context, args struct{ ID graphql.ID }) (*TokenResolver, error) {
  token, err := fetchTokenByID(string(args.ID)) // Implement this function.
  if err != nil {
    return nil, err
  }
  return &TokenResolver{token: token}, nil
}
```
