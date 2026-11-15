Arguments about modeling approaches can become heated, and not everyone is as convinced of the virtues of ORM as we are. All we ask is that you look objectively at the ideas presented in this book and consider using whatever you find helpful.

Although the book focuses on ORM, it also covers data modeling in other popular notations (e.g., ER, IDEF1X, UML, and relational). These other notations have value too. Even if you decide to stay with ER or UML as your conceptual analysis approach, insight into ORM should make you a better modeler regardless.

# ## 1.3 Historical Background

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