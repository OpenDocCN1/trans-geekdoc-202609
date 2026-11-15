# Stored Procedures

Stored procedures, commonly referred to as “sprocs”, are bodies of code that are explicitly called from other code. In this section, we’ll assume that the body of the procedure is writ‑ ten in SQL, but it’s possible for the procedure actions to be written in some other language, such as “C”, and then called from SQL. Stored procedures can (and often do) have side effects, such as updating tables during their execution. Encapsulating code in a stored pro‑ cedure offers several potential benefits.

**Modularity.** Code in a stored procedure is readily reusable in other code. A well‑ maintained library of stored procedures can be a valuable resource when developing new applications. Modularity also helps to ensure consistency. For example, a business rule can be implemented once in a stored procedure and called as needed, instead of hav‑ ing the same rule implemented in perhaps slightly different ways in different places. The same argument applies to maintainability. If a change is needed, it need only be applied in one place. As long as the previous interface is maintained, other programs that call the stored procedure need not be aware of any changes that have been made.

**Security.** Users of a stored procedure are offered only the functionality that the proce‑ dure provides. Limiting access in this way drastically reduces the possibility of damage to the database, whether deliberate or accidental. The authority given to users of a stored procedure can be different from the authority to access any underlying tables, so any actions can only be taken in the context of the procedure. For example, all modifications to an “Orders” table can be channeled through a stored procedure that imposes business rules and other constraints on what changes can be made, instead of giving users direct access to the base table.

**Performance.** Stored procedures are typically compiled, optimized, and cached ready for use when needed. The details vary from one implementation to another, and extensions to the basic syntax are usually provided to address issues such as the need to redo compi‑ lation and optimization if the usage circumstances change. Stored procedures can also reduce network traffic: instead of constructing a query in an application and passing the resulting SQL across a network, only the parameters need be passed to a stored procedure.

The basic syntax for creating and dropping a stored procedure is as follows.

```
create procedure procedurename
( [{ | in | out | inout } parmname parmtype [...] ] )
procedure-body

drop procedure procedurename
```

A stored procedure takes zero or more parameters. Each parameter can be specified as in (external values are provided to the procedure), out (the procedure makes its results available externally), or inout (the input parameter may be modified by the procedure for external access). As usual, commercial systems may vary from the standard syntax. For example, in SQL Server any parameters of a stored procedure are considered as in parameters unless they are explicitly denoted as out, and there is no inout option.