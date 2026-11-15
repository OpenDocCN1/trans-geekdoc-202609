Documents are typically expressed using the structural capabilities of JSON, previously described in Chapter 16. Internally, the information storage may adopt BSON, a binary form of JSON that incorporates additional metadata to make data scans faster and can also reduce storage requirements, but we will ignore this detail.

A document database is formed from collections. Each collection contains documents of a similar kind: for example, Products, Orders, Customers, and so on. Each document can contain several fields, but the data in a field need not be single-valued as it would be in a normalized relational database—a field can contain a structure that, in turn, can contain other structures and so on. There is a rough correspondence between these concepts and their relational equivalents, as shown in Table 17.1.

Table 17.1 Comparison of RelationalDB and Document DB concepts.

| Relational DB | Document DB |
|---|---|
| Table | Collection |
| Row | Document |
| Column | Field |

To illustrate some features of this type of structure, the following example shows two documents from a hypothetical Contracts collection:

```
Contracts: [
  {
    _id: ObjectId("6481d941f682789c3b8d71ef"),
    contractRef: 9876,
    activeDate: "Jan 1 2024",
    customerId: "DE876",
    staffAllocation: [ { person: "Alice123", hours: 15 },{ person: "Bob456", hours: 35 } ]
  },
  {
    _id: ObjectId("64820117f682789c3b8d71f0"),
    contractRef: 8765,
    startDate: "Jan 12 2024",
    customerId: 2024002,
    staffAllocation: {
      marketing: [ { person: "Carol999", hours: 5 } ],
      operations: [ { person: "Bob456", hours: 5 }, { person: "Dave666", hours: 30 } ]
    },
    contractType: "FP"
  }
]
```