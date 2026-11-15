# # Other Database Features

+   Chapter Outline
+   13.1 SQL: The Bigger Picture
+   13.2 SQL: Defining Tables
+   13.3 SQL: Views
+   13.4 SQL: Triggers
+   13.5 SQL: Routines
+   13.6 More Database Objects
+   13.7 Transactions and Concurrency
+   13.8 Security and Metadata
+   13.9 Summary

# ## 13.1 SQL: The Bigger Picture

In the previous chapter, we looked at structured query language (SQL) statements that retrieve data (select...) and modify data (insert..., update..., delete...). This set of statements is traditionally known as the data manipulation language (DML). We now turn our attention to other aspects of SQL. We’ll look at statements used to define the various elements of a database schema, which uses a subset of SQL that is traditionally known as the data definition language (DDL).

Tables are, of course, fundamentally important to any schema, but we’ll also discuss several other types of database objects and the roles they play in the realization of a conceptual schema. In particular, database objects such as views and triggers are often used to implement constraints and derivation rules that may have been defined initially at the conceptual level.

The widespread adoption of extensible markup language (XML) has been fueled primarily by its use for the interchange of structured data. However, this has created a corresponding need for better integration between relational and XML data. A later chapter discusses the ways in which the SQL standard has been adapted and extended to add XML-related features and how non-SQL data manipulation (such as in XQuery) can be accommodated in a relational framework.