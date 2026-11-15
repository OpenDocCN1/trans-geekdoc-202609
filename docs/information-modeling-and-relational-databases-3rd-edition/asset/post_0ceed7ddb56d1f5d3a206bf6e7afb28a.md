
Arguments about modeling approaches can become heated, and not everyone is as convinced of the virtues of ORM as we are. All we ask is that you look objectively at the ideas presented in this book and consider using whatever you find helpful.

Although the book focuses on ORM, it also covers data modeling in other popular notations (e.g., ER, IDEF1X, UML, and relational). These other notations have value too. Even if you decide to stay with ER or UML as your conceptual analysis approach, insight into ORM should make you a better modeler regardless.

## 1.3 Historical Background

This section briefly overviews the evolution of computing languages for information systems and outlines the historical development of the main kinds of logical data structures used in database systems. We begin with a simple example to illustrate how the level of a language impacts how easy it is to formulate questions.

Table 1.5 summarizes how **five generations of computing languages** might be used to request a computer to list the name, mass, and moons (if any) of each planet, assuming the information is stored in an astronomical database. The higher the generation, the closer to natural language, and usually the less you have to say. Nowadays, nobody uses machine code or assembler to access databases. Most database applications are coded using fourth-generation languages (4GLs), perhaps in combination with third-generation languages (3GLs).

| Generation | Language example | Sample code for same task |
| :--- | :--- | :--- |
| 5 | ConQuer | ✓Planet **that has** ✓Mass **and possibly is orbited by** ✓Moon |
| 4 | SQL | **select** X1.planetName, X1.mass, X2.moonName **from** Planet as X1 **left outer join** Moon as X2 **on** X1.planetName = X2.planetName |
| 3 | Pascal | Two pages of instructions like: **for** i := 1 to n do **begin** write (planetName[i], mass[i]); |
| 2 | 8086 Assembler | Many pages of instructions like: ADD1 AX, 1 |
| 1 | 8086 machine code | Many pages of instructions like: 00000101 00000001 00000000 |

Third-generation languages, such as C# and Java, are *procedural*, emphasizing the procedures used to carry out the task. With 3GLs, we typically need to specify how to access data one record at a time. Fourth-generation languages, such as SQL, are primarily *declarative* in nature: one declares *what* is to be done rather than *how* to do it. With a 4GL, a single statement can perform operations on whole tables, or sets of rows, at once. Hence, 4GLs are *set oriented* rather than record oriented.

Fifth-generation languages (5GLs), such as ConQuer (an ORM query language), allow you to specify queries naturally, without knowing the underlying data structures used to store the information. The widespread use of fifth-generation languages is still in the future.

The first DBMSs were developed in the early 1960s, starting with simple file managers. Various logical data architectures have been proposed as a basis for specifying the structure of databases. In the hierarchical data model, the database schema is basically a tree of linked record types, where each record type has a different structure (unlike many trees where each node is of the same type).

Records may include one or more fields, each of which can hold only a single value. Record types are related by parent-child links (e.g., using pointers), where a parent may have many children but each child has only one parent. Hence the type structure is that of a tree, or hierarchy.

For example, in Fig. 1.9 the parent record type Department has two child record types: Product and Employee. Each record type contains a sequence of named fields, shown here as boxes, and the parent-child links are shown as connecting lines. For discussion purposes, one record instance has been added below each record type. As an exercise, try reading off all the facts that are contained in this database before reading on.

To begin with, there are five facts stored in the record instances. To make these facts more obvious, Fig. 1.9 includes arcs connecting the relevant fields, one arc for each fact. Although these arcs are a useful annotation, they are not part of the schema notation. If we are familiar with the business domain, we can verbalize these arcs into relationships. For example, we might verbalize the five facts as follows:

- Department 10 is located in Building 69.
- Department 10 has Budget $200,000.
- Product “IS2” has ProductName “InfoStar 2”.
- Employee 357 has EmployeeName “Jones E”.
- Employee 357 is of Sex “F”.

Are there more facts? Yes! The parent-child links encode the following two facts:

- Department 10 develops Product “IS2”.
- Department 10 employs Employee 357.

![](img/1344db3eba3d550e6edb009556fcd95c_44_0.png)

FIG. 1.9 A hierarchic database schema with sample data, and fact arcs.

Hierarchic DBMSs such as IBM’s Information Management System can efficiently manage hierarchic structures (e.g., a file directory system). However, having to explicitly navigate over predefined record links to get the facts can be somewhat challenging. The complexity rises if the application is not hierarchic in nature.

Suppose that the same product may be developed by more than one department. Conceptually, the Department develops Product association is now *many:many*. Because parent-child links are always 1:*many*, a workaround is needed to handle this situation.

For example, to record the facts that departments 10 and 20 both develop product “IS2”, we could have the two department record instances point to separate copies of the record instance for product “IS2”.

Although the type and instance link structures are trees, the fact that product “IS2” is named “InfoStar 2” now appears twice in the database, so we need to control this redundancy. Moreover, while retrieving products developed by a given department is easy, retrieving all the departments that developed a product is not easy.

The *network data model* was developed by the Conference on Data Systems and Languages (CODASYL) Database Task Group. This model is more complex than the hierarchic model. Most of the data is stored in records, a single field of which may contain a single value, a set of values, or even a set of value groups. Record types are related by owner-member links, and the graph of these connections may be a network: a record type may have many owners and also own many record types.

As in the hierarchic model, facts are stored either in records or as record links. An owner-member link between record types is restricted to a 1:many association. To handle a many:many association, such as the case discussed earlier, we might introduce a new record type (e.g., Development) with many:1 associations to the other record types (in this case, Department and Product).

In general, encoding of facts in access paths such as interrecord links complicates the management of the application and makes it less flexible. For example, new queries will have to wait until access paths have been added for them, and internal optimization efforts can be undone as the application structure evolves.

Partly to address such problems, Dr. Edgar “Ted” Codd introduced the *relational data model*. A year after his original 1969 IBM research report on the subject, Codd published a revised version for a wider audience (Codd, 1970) where he first argued that relations should be normalized so that each data entry would be atomic; we now call this first normal form. Other normal forms were defined later.

The most significant feature of the relational model is that *all the facts are stored in tables*, treated as mathematical relations. For example, Fig. 1.10 shows the relational database for our application. Again, the database is annotated with arcs corresponding to the facts stored. Notice the extra deptNr columns in the Employee and Product tables. The facts that Department 10 employs Employee 357 and develops product “IS2” are stored in the table rows themselves. Access paths between tables are not used to specify facts (as allowed in hierarchic or network models).

To specify queries and constraints, table columns may be associated by name. This allows ad hoc queries to be specified at will and simplifies management of the application.
