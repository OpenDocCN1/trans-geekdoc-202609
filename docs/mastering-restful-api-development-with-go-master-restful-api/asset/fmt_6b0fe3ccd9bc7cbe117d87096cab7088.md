
`@include(if: $includeVolume)` is a directive applied to the volume field.

`$includeVolume` is a Boolean variable that determines whether the volume field should be included in the response.

When executing this query, you can dynamically decide whether to fetch the volume information by setting the `$includeVolume` variable to true or false.

Directives thus offer a flexible approach to modifying the execution of queries and shaping the returned data according to the needs of your application or the permissions of the current user.

# [ Mutations ]

In GraphQL, mutations are operations used to modify data on the server, such as creating, updating, or deleting records. Unlike queries, which are used to fetch data, mutations change data and typically return the new or modified data.

Here is a basic structure of how mutations are defined and used in GraphQL:

```
mutation MutationName($input: InputType!) {
  operationName(input: $input) {
    field1
    field2
    …
  }
}
```

Here is an example demonstrating how to use a mutation to update a token’s information:

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

In this example:
* `UpdateToken` is the name of the mutation.
* `$id`, `$price`, and `$volume` are variables passed into the mutation, allowing you to dynamically specify the ID of the token you want to update and the new values for the price and volume.
* `updateToken` is the operation being called on the server, which takes the id, price, and volume as arguments.
* The mutation returns the updated name, symbol, price, and volume of the token succeeding the update operation is completed.
* By using mutations, you can perform Create, Read, Update, and Delete (CRUD) operations and more, effectively changing the data stored on the server through your GraphQL API. This mechanism ensures that data manipulation is intentional and explicit, contributing to the robustness and reliability of the API.

# [ Type System ]

The GraphQL type system is fundamental to defining the schema of a GraphQL API. It specifies the types of data that can be queried and manipulated through the API, ensuring that clients interact with the data in a consistent and type-safe manner. Here is an overview:

* `Scalar Types`: These are the basic data types in GraphQL. They include `Int`, `Float`, `String`, `Boolean`, and `ID`. Scalar types represent the leaves of the query - they describe the primitive data that gets returned.
* `Object Types`: These are the most common types used in GraphQL and represent a group of fields. Each field in an Object Type can be of any type, including Scalar, Enum, Interface, Union, or even another Object Type. Object types are used to define the shape of objects returned by your API.

Example:
```
type Token {
  id: ID!
  name: String!
  symbol: String!
  price: Float
  volume: Int
}
```
* `Enum Types`: Enumerations, or Enum Types, restrict a value to a set of predefined values. They are useful for fields that can only take on a specific set of values.

Example:
```
enum Currency {
  USD
  EUR
  BTC
}
```
* `Interface Types`: These define a list of fields; Object types can then implement these interfaces, which ensures they will contain those fields. Interfaces are useful for defining common fields across multiple object types.

Example:
```
interface Character {
  id: ID!
  name: String!
}
```
* `Union Types`: Union types are similar to interfaces, but they do not specify any common fields between the types. Instead, they are used to denote that a field can return one of a finite set of different types.

Example:
```
union SearchResult = Book | Author | Magazine
```
* `Input Types`: While regular object types define the shape of objects you can fetch from your API, Input Types specify what objects might look like when you send them in as arguments to mutations and queries.

Example:
```
input TokenInput {
  name: String!
  symbol: String!
  price: Float
  volume: Int
}
```
* `List Types and Non-Null Types`: These are wrapper types that modify the behavior of other types. Lists are used to represent an array of values, while Non-Null types are used to indicate that a field must never return null.

Example:
```
type Query {
  tokens: [Token]    # List of Token objects
  token(id: ID!): Token!  # Non-Null Token object
}
```

The GraphQL type system ensures that the schema clearly defines what data can be interacted with, how it can be queried by the clients, and the form that the responses will take, providing a robust framework for building and querying your API.

# [ Adopting a Graph-Based Mindset ]

Graphs are effective in modeling various real-world situations as they mirror our innate mental models and verbal descriptions of processes. In GraphQL, you structure your business domain as a graph by creating a schema. This schema outlines different types of nodes and their interconnections. For clients, this approach creates a pattern akin to Object-Oriented Programming, with types referencing other types. On the server side, GraphQL merely defines the interface, offering you the flexibility to integrate it with any backend, whether new or legacy.

# [ Shared Language ]

View your GraphQL schema as a unifying language that bridges your team with your users. To devise an effective schema, reflect on the language commonly employed when discussing your business context. For instance, let us describe a cryptocurrency wallet application in straightforward terms:
* A user can hold multiple cryptocurrency tokens.
* Each token has unique attributes such as symbol, current value, and transaction history.
* Each transaction records details such as sender, receiver, amount, and timestamp.
* Users need to have enough token balance prior to initiating a transaction.

Selecting the right terminology is a challenging yet crucial task for developing intuitive APIs. Invest time to carefully evaluate the terms that resonate with your domain and are easily understood by your users. It is vital for your team to achieve a shared understanding and agreement on these concepts since you will have to pick clear and meaningful names for the objects and their relationships within your GraphQL schema. Consider the types of queries you might need, such as fetching the total balance of a specific cryptocurrency token across all user accounts.

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

In this query, we are asking for a user (with a hypothetical ID of “123”) and requesting their name along with the list of tokens they own. For each token, we are fetching the symbol, the balance the user has, and the token’s current value.

Query to Fetch Transaction History for a Specific Token:

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

# [ Business Logic Layer ]

Where should the core business logic be situated? Where should validation and authorization be conducted? The solution lies in establishing a dedicated business logic layer. This layer should serve as the central authority for applying and upholding the rules of your business domain.

![](images/Figure6.2.jpg)

**Figure 6.2:** Placement of Business Logic
