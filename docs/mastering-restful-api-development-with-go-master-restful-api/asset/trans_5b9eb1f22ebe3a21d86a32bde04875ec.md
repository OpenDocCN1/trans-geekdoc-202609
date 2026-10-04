

如果遍历对象及其字段是 GraphQL 的唯一功能，它仍然会成为一种高效的数据检索语言。然而，当你引入向字段传递参数的能力时，该语言变得更加强大和有趣。

```
{ 
 token(id: "20") { 
 name 
 address 
 } 
}
```
```
{ 
 "data": { 
 "token": { 
 "name": "WBTC", 
 "address": "0x2260FAC5E5542a773Aa44fBCfeDf7C193bc2C599" 
 } 
 } 
}
```

在基于 REST 的系统中，你传递参数的选项仅限于请求中的查询参数和 URL 段。然而，GraphQL 允许每个字段和嵌套对象都有其自己独特的参数集。这种能力使 GraphQL 成为执行多个 API 请求的全面替代方案。此外，你可以将参数应用于标量字段，从而在服务器上直接进行数据转换，而不是在每个客户端上单独进行。

```
{ 
 token(id: "20") { 
 name 
 address(blockchain: Ethereum) 
 } 
}
```
```
{ 
 "data": { 
 "token": { 
 "name": "WBTC", 
 "address": "0x2260FAC5E5542a773Aa44fBCfeDf7C193bc2C599" 
 } 
 } 
}
```

GraphQL 中的参数类型可以各不相同。在提供的示例中，我们使用了枚举类型，表示从有限的选项集中选择一个（这里是代币的地址，具体区块链）。虽然 GraphQL 包含一组标准类型，但 GraphQL 服务器可以定义自己的自定义类型，只要它们可以序列化为用于数据传输的格式即可。

## 别名

GraphQL 中的别名是一个强大的功能，允许你将字段的结果重命名为与查询中字段名称不同的名称。这在多种场景下特别有用，例如当你需要使用不同的参数查询同一个字段并需要区分结果时，或者当你在结果集中想要使用的名称比 GraphQL 模式中的字段名称更具描述性或更适合你的应用程序时。

下面是一个简单的示例来说明别名在 GraphQL 中是如何工作的：

```
{ 
 USDC: Token(id: "1") { 
 name 
 } 
 Bitcoin: Token(id: "20") { 
 name 
 } 
}
```

在此查询中，`token` 是根查询类型上的一个字段，它接受 `id` 作为参数并返回一个代币。通过使用别名，我们可以在同一个查询中查询两个字符（ID 为“1”和“20”），并分别将结果称为 `USDC` 和 `Bitcoin`。这使得查询返回的数据更易于理解，并在客户端应用程序中更易于使用，因为别名提供了每个字符在叙述中作用的上下文。

GraphQL 中的别名通过允许在结果中进行自定义命名来增强数据检索的灵活性，这可以简化客户端的数据处理，并使响应更直观。

## 片段

GraphQL 中的片段是可以共享在多个查询之间或在同一查询内以避免冗余的可重用查询片段。它们允许你构建字段集，然后在需要时将其包含在查询中。这对于确保多个查询和变更的一致性特别有用，尤其是在应用程序的不同部分需要检索相同数据时。

下面是 GraphQL 中片段使用方式的基础示例：

```
fragment tokenDetails on Token { 
 name 
 symbol 
 address 
 volume 
 price 
}
query getTokenDetailsById { 
 tokenById(id: "1") { 
 …tokenDetails 
 } 
}
query getAllTokens { 
 allTokens { 
 …tokenDetails 
 } 
}
```

`tokenDetails` 是一个片段，封装了与代币相关的字段。无需在 `getTokenDetailsById` 和 `getAllTokens` 查询中重复这些字段定义，它们在 `tokenDetails` 片段中只定义一次。然后通过指定 …`tokenDetails` 在查询中使用该片段。这种方法确保对代币详情的任何更改都只需在一个地方进行，从而简化查询的更新和维护。

## 操作名称

操作名称是赋予操作（如查询、变更或订阅）的有意义且明确的名称。此名称用于提高清晰度，并且在调试和服务器端日志记录时特别有用；它有助于在代码库中识别不同的 GraphQL 操作，并在分析日志或指标时提供帮助。

下面是一个示例来说明操作名称在 GraphQL 中是如何使用的：

```
query GetTokenDetails { 
 token(id: "1") { 
 name 
 symbol 
 address 
 volume 
 price 
 } 
}
mutation UpdateTokenPrice { 
 updateTokenPrice(id: "1", price: 100) { 
 id 
 price 
 } 
}
subscription OnTokenPriceChange { 
 tokenPriceChanged(id: "1") { 
 id 
 price 
 } 
}
```

在此示例中：

* `GetTokenDetails` 是获取代币详情的查询的操作名称。
* `UpdateTokenPrice` 是更新代币价格的变更的操作名称。
* `OnTokenPriceChange` 是监听代币价格变化的订阅的操作名称。
* 使用操作名称是 GraphQL 中的最佳实践，因为它增强了查询和变更的可读性，使代码更有序，并在调试和监控期间提高操作的追溯性。

## 变量

在 GraphQL 中，你可以使用变量将动态信息传递到查询或变更中。这种方法允许你使用不同的值重用相同的查询或变更。以下示例演示了如何使用变量与 GraphQL 操作一起使用，具体针对代币对象：

```
query GetTokenDetails($tokenId: ID!) { 
 token(id: $tokenId) { 
 name 
 symbol 
 address 
 volume 
 price 
 } 
}
```

在此示例中：

* `$tokenId` 是在操作 `GetTokenDetails` 中定义变量。它是类型 `ID!`，表示它是非空 ID。
* 在代币查询内部，`$tokenId` 用于动态指定正在请求详情的代币的 ID。
* 执行此查询时，你需要为 `$tokenId` 提供一个值，例如：{ `"tokenId": "123abc"` }。
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

