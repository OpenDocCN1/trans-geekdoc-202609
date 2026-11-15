| Name: | 1 | Alice |
| | 2 | Bob |
| | 3 | Carol |
| | 4 | Dave |
| | 5 | Edna |

| Diet: | 1 | glutenfree |
| | 4 | vegan |

| Weight: | 1 | 68 |
| | 2 | 92 |
| | 4 | 66 |
| | 5 | 78 |

FIG. 17.7 Column-oriented dietary data.

The example in Fig. 17.7 is laid out in separate tabular form for comparison with the relational version, but it is also possible to visualize the name, diet, and weight “tables” as rows in a column-oriented database, as shown in Fig. 17.8. From this perspective, it’s possible to see that rows in this representation can contain a variable number of columns.

| rowKey | values |
|---|---|
| name | (1, Alice), (2, Bob), (3, Clare), (4, Dave), (5, Edna) |
| diet | (1, glutenfree), (4, vegan) |
| weight | (1, 68), (2, 92), (4, 66), (5, 78) |

FIG. 17.8 Dietary data expressed in row form.

In this case, serializing the data into physical storage might look something like the following:

```
1, Alice, 2, Bob, 3, Clare, 4, Dave, 5, Edna, 1, glutenfree, 4, vegan, 1, 68, 2, 92, 4, 66, 5, 78
```

At this simple level, we can’t see the specific detail of the data layout in persistent storage. This depends very much on the specific database being considered. Even so, it’s obvious that in one case, a retrieval will find colocated information for an entity and the other will find colocated information for an attribute. Another way of saying this might be that row-oriented retrieval gets values for the attributes of an entity, but column-oriented retrieval gets values for the entities of an attribute.

Consider a query to find the average person’s weight from this information. The relational case would require the retrieval of each row and the weight column value within the row before calculating the average value. In the column-oriented case, we simply need to retrieve the weight row in the table shown in Fig. 17.8 to get all the necessary values for the calculation. Because data retrieval from persistent storage is the most time-consuming part of the operation, this shows that the column-oriented approach has the potential for much better performance on certain types of queries. Performance is probably the greatest single motivator for this type of database, especially as the database becomes larger. In a column-oriented database, increasing amounts of data result in rows becoming bigger, not a bigger number of rows, so these are sometimes referred to as “wide tables”.