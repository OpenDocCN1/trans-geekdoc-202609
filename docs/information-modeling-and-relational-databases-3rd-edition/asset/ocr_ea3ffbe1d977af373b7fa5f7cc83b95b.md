converted to a lower-level structure for efficient implementation. For a given application, an appropriate logical data model (e.g., relational, object-oriented) is chosen, and the conceptual schema is mapped to a **logical schema** expressed in terms of the abstract structures for data and operations supported in that data model. For example, in a relational schema, facts are stored in tables, and constraints are expressed using primary and foreign key declarations and so on.

The logical schema may now be realized as a **physical schema** in a specific database management system (DBMS), such as a relational schema might be implemented in Microsoft SQL Server or IBM's DB2. The physical schema includes details about the physical storage and access structures used (indexes, file clustering, etc.). Different physical choices can be made for the same DBMS, and different DBMSs often differ in what choices are possible, so different physical schemas might be chosen for the same logical schema. Operations at the external level are converted by the system into operations at the physical level. Logical and physical schemas reside at the *internal level*.

One advantage of the conceptual level is that it is the most *stable* of all the levels. It is unaffected by changes in user interfaces or storage and access techniques. Suppose a conceptual schema is implemented in a relational DBMS, and later we wish to use an object database instead. Unless the UoD has changed, the conceptual schema can remain the same. We need only apply a different mapping procedure and then migrate the data.

If a language is the object of study, it is said to be the *object language*. The language used to study it is then called the *metalanguage*. For example, you might use English as a metalanguage to study Japanese as an object language. An object language may be its own metalanguage, for example, English may be used to learn about English. Any conceptual schema may be expressed as a set of sentences, and hence may be viewed as a database in its own right.

This enables us to construct a *metaschema* for talking about conceptual schemas. This conceptual schema specifies the design rules that must be obeyed by any conceptual schema (e.g., each role is played by exactly one object type). Computer-aided software engineering (CASE) tools are used to assist in designing conceptual schemas of such a metaschema to ensure that schemas entered by the modeler are well formed or “grammatical”.

While on the subject of grammar, let us agree to accept both “schemas” and “schemata” as plural of “schema”. Although “data” is the plural of “datum”, we’ll adopt the common practice of allowing “data” to be used in both singular and plural senses. The first exercise in the book is shown next. Answers to exercises are included in the online supplement.

# Exercise 2.1

+   1. Classify each of the following as A (external), B (conceptual), or C (internal).
+   (a) This level deals with physical details of how to store and access data.
+   (b) This level is concerned with providing a convenient and authorized view of the database for an individual user.
+   (c) This level is concerned with representing information in a fundamental way.