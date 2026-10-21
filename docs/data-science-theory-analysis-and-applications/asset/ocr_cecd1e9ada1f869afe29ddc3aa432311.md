We can also help the Neo4j planner incorporating additional information in our query. Since we know that the node is a Movie node instead of a Person node, we can pose this query in such a way that it is only executed for searches on the nodes of the Movie type. Figure 4.4 illustrates an example query where the type of node is specified into the match clause.

When the type of node is incorporated into the query, a better plan is obtained. In Figure 4.5, it can be noted that the NodeByLabelScan operator is applied rather than the AllNodeScan node. Since the NodeByLabelScan operator is only executed on Movie nodes, it produces 38 estimated nodes, i.e., it approximately discards 78% nodes in its search.

Intuitively, a small sample of physical design strategies has been introduced in this section as an example in Neo4j [3]. A physical design produces an implementation-level description of a database: the storage structures and methods used for efficient access to the data [4]. An adequate physical design is the key for quickly accessing the information. It depends on specific aspects of the DBMS on which it needs to be implemented and important clues must be followed to design an optimal physical database. Thus, we must know the internal workings of our DBMS well in order to understand what is happening and how we can optimize a query. In our motivating example, a rewritten query improved its performance; however, not all classic physical design strategies are successful in Neo4j. Particularly, Neo4j offers a native index version whose implementation is not clearly specified by Neo4j and is limited for certain data types such as spatial, temporal, and numeric. For the other data types, Neo4j uses Lucene which supports inverted indexing. Neo4j indexing differs from traditional systems such as PostgreSQL and Oracle, which include

```
MATCH (movie:Movie {title: "The Matrix"})
RETURN movie
```

FIGURE 4.4 Query for finding the movie matrix using the node label.

![](bbox=[0.33, 0.9, 0.68, 0.97])

FIGURE 4.5 Plan generated for executing a query using node labels.