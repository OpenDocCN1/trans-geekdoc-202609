The create-table statements declare the schemes for the Employee and Drives tables. A not-null clause indicates that a column is mandatory for its table. Primary keys are declared with primary-key clauses. A unique clause specifies the alternate compound key. The intertable subset constraint is declared with a references clause. Check clauses are used to declare the value and frequency constraints. Further explanation of SQL syntax is given in the next chapter.

Although the above SQL syntax has been legal for years, some commercial SQL dialects do not yet support all this syntax. In practice, some features of a relational schema may need to be specified as procedural code rather than declaratively.

A conceptual schema comprises three sections: fact types, constraints, and derivation rules. Conceptual derivation rules may be specified in an appropriate language, using either relational or attribute style notation.

For example, in the schema shown in Fig. 11.6(a), an employee's net pay is derived using the ORM rule: **For each Employee, if tax exists then netpay = salary – tax else netpay = salary.**

As shown in Fig. 11.6(b), the derivation rule may be simplified to a simple subtraction if we make tax mandatory with a default of 0 (append “not null default = 0” to the SQL code above for the tax column) or assume that nulls are treated as zero for subtraction. The next chapter discusses in detail how SQL handles nulls.

![](bbox=[0.22, 0.46, 0.8, 0.66])

Various options exist for mapping derivation rules to the relational level. One option is to declare a derivation rule within a view (virtual table), for example, create view NetSalary( empNr, netPay ) as select empNr, salary – tax from Employee.

A second option is to include a generated column in the relevant base table. In the SQL standard, this could be done by including the following definition in the table definition given earlier: netPay generated always as (salary – tax).

Not all DBMSs support generated columns, and some that do support this feature use a different syntax. For example, in SQL Server we may simply declare netPay as (salary – tax).

A third option is to include a triggered column in the relevant base table. As discussed in Chapter 13, triggers on a table specify actions taken automatically when relevant columns are changed in a given way. The syntax for triggers varies with the DBMS. Assuming that a