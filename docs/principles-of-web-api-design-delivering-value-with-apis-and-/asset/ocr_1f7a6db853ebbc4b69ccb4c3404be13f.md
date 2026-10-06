# Step 1: Designing Resource and Graph Structures

The first and most important step for query-based APIs is to design the graph structure of all resources. If the API modeling work outlined in Chapter 6 has been done, then this step is already complete. If the API modeling work hasn't been completed, go back to Chapter 6 and complete those steps before proceeding. Figures 8.5 and 8.6 revisit the resources and relationships identified in Chapter 6 for the bookstore example.

Once all top-level resources, along with related resources, have been identified, proceed to the next step to design the query and mutation operations.

# Step 2: Design Query and Mutation Operations

The next step is to migrate all operations captured in the API profile modeling in Chapter 6. The API profiles capture each operation and include a safety classification of safe, idempotent, or unsafe. Classify each operation marked as safe as a query. Operations marked as idempotent or unsafe will be mutations. For the Shopping Cart API, there are both query and mutation operations, as shown in Figure 8.7.

| Book Resource |
| Property Name | Description |
--- | --- |
 title | The book title |
 isbn | The unique ISBN of the book |
 authors | List of Book Author resources |

| Book Author Resource |
| Property Name | Description |
--- | --- |
 fullName | The full name of the author |

**Figure 8.5** The Book resource is the first top-level resource that needs to be supported for the Shopping Cart API modeled in Chapter 6.