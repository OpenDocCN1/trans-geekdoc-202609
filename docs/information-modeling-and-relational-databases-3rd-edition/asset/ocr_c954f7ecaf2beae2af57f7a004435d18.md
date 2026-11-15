# # NoSQL and Other Nonrelational Databases

# ## Chapter Outline

+   - 17.1 The Growth of the NoSQL Movement
+   - 17.2 Key-Value Stores
+   - 17.3 Column-Oriented Databases
+   - 17.4 Document Databases
+   - 17.5 Graph Databases
+   - 17.6 Other Nonrelational Databases
+   - 17.7 Summary

# ## 17.1 The Growth of the NoSQL Movement

Following the publication of E.F. Codd’s ground-breaking relational paper in 1970 (Codd, 1970), it was not until the 1980s that commercial relational database systems became widely available. Since that time, they have become the dominant data storage model. Other data resources are used at smaller scales, such as spreadsheets, text files, and so on, but for large-scale data, relational systems have reigned supreme.

The NoSQL movement started to emerge in the 2010s in response to perceived shortcomings in the relational approach (Leavitt, 2010). It’s worth noting straight away that “NoSQL” is not a particularly good choice of name. The crucial point is not really an issue with the structured query language (SQL). In fact, some NoSQL vendors try very hard to provide languages that are as similar as possible to SQL. Instead, NoSQL approaches rely on data models that are nonrelational to provide their distinctive features. There are some suggestions that “NoSQL” should be interpreted as “Not Only SQL”, but this would include every kind of database, rendering it completely meaningless.

The driving forces behind the movement did not result from a failure of the relational model as such but from new challenges and opportunities exposed by the general evolution of technology. The following trends are especially relevant:

+   - The cost of data storage has fallen dramatically. In the 1980s, there was a preoccupation with minimizing storage requirements because of the expense of the hardware involved. Today, consumers are commonly offered services that include gigabytes of free data storage space, which would have been unthinkable in earlier times. The decreasing incentives to minimize storage have contributed to the continual increase in database sizes.