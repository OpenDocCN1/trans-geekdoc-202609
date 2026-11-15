
![](img/1344db3eba3d550e6edb009556fcd95c_511_0.png)

FIG. 11.4 A more detailed ORM schema for employees.

The external uniqueness constraint on employee name and department maps to a composite uniqueness constraint spanning two attributes. In the horizontal layout, this is denoted by underlining the relevant columns as discussed before. The value constraint on gender codes and the frequency constraint that each employee drives at most three cars are specified in the horizontal layout by annotating the table schemes with an ORM-like notation, as shown in Fig. 11.5(a).

Most ORM constraint notations may be used in a similar way in setting out relational schemas. Sometimes we adapt these notations or introduce new ones (see later). While our semigraphical notation is compact and fairly intuitive, commercial tools usually depict relational schemas diagrammatically using a vertical layout, supplemented by textual rules stored in property sheets or code. Although it takes up more space, vertical layout is convenient for tables with many columns.

```
(a) Employee ( empNr, empName, deptCode, gender, salary, [tax] ) {M,F}
Drives ( empNr, carRegNr )
<= 3
```

| Employee | |
|---|---|
| PK empNr | |
| U1 empName | |
| U1 deptCode | |
| gender | |
| salary | |
| tax | |

| Drives | |
|---|---|
| PK, FK1 empNr | |
| PK carRegNr | |

| Employee |
|---|
| Column Name | Allow Nulls |
| empNr | |
| empName | |
| deptCode | |
| gender | |
| salary | |
| tax | [check] |

| Drives |
|---|
| Column Name | Allow Nulls |
| empNr | |
| carRegNr | |

FIG. 11.5 A relational schema in (a) horizontal layout and (b, c) some vertical layouts.

Fig. 11.5(b) shows one of the ways in which Visio diagrams the same example. Here, the table name is listed in the top compartment with the column names listed vertically below. Mandatory columns are shown in bold, so tax is the only optional column. Primary key columns are underlined and annotated with “PK”.

If desired, primary keys can also be displayed in a separate compartment. Foreign keys are annotated with “FKn” (n > 0), and an arrow depicts the subset constraint from the foreign key to the target table. Nonprimary uniqueness constraints are denoted by “Un”. The value constraint on gender and the frequency constraint on carRegNr are not displayed on the diagram but can be inspected in the associated code.

Fig. 11.5(c) shows one way in which Microsoft SQL Server diagrams the same example. Here, the primary key columns are marked with a key symbol, and the foreign key constraint is depicted as a relationship line with a key symbol at the target end and “∞” (infinity, for a cardinality of “many”) at the source end. The mandatory or optional nature of a column is indicated, respectively, by the absence or presence of an Allow Nulls check mark. Other constraints may be inspected in the associated code.

There is no industry standard that is uniformly adopted for diagramming relational schemas. When using a particular computer-aided software engineering (CASE) tool or DBMS, you need to familiarize yourself with its specific relational notation.

The same relational schema may be specified in SQL as set out later. Reserved words are shown in bold, but this is not required. To save some writing, domains on which more than one column are based are declared initially (EmpNr and Money), and constraint names are omitted. Ever since 1999, the ISO standard for SQL allows types to be declared instead of domains.

```
create domain EmpNr smallint;
create domain Money decimal(9,2);
create table Employee (
empNr      EmpNr      not null      primary key,
empName    varchar(30) not null,
deptCode   varchar(5)  not null,
gender     char(1)     not null    check( gender in ('M','F') ),
salary     Money       not null,
tax        Money,
unique ( deptCode, empName ) );
create table Drives (
empNr   EmpNr   not null   references Employee,
carRegNr char(6)  not null,
primary key ( empNr, carRegNr ),
check( not exists
(select empNr from Drives
group by empNr
having count(*) > 3 ) );
```

The create-table statements declare the schemes for the Employee and Drives tables. A not-null clause indicates that a column is mandatory for its table. Primary keys are declared with primary-key clauses. A unique clause specifies the alternate compound key. The intertable subset constraint is declared with a references clause. Check clauses are used to declare the value and frequency constraints. Further explanation of SQL syntax is given in the next chapter.

Although the above SQL syntax has been legal for years, some commercial SQL dialects do not yet support all this syntax. In practice, some features of a relational schema may need to be specified as procedural code rather than declaratively.

A conceptual schema comprises three sections: fact types, constraints, and derivation rules. Conceptual derivation rules may be specified in an appropriate language, using either relational or attribute style notation.

For example, in the schema shown in Fig. 11.6(a), an employee's net pay is derived using the ORM rule: **For each Employee, if tax exists then netpay = salary – tax else netpay = salary.**

As shown in Fig. 11.6(b), the derivation rule may be simplified to a simple subtraction if we make tax mandatory with a default of 0 (append “not null default = 0” to the SQL code above for the tax column) or assume that nulls are treated as zero for subtraction. The next chapter discusses in detail how SQL handles nulls.

![](img/1344db3eba3d550e6edb009556fcd95c_513_0.png)

Various options exist for mapping derivation rules to the relational level. One option is to declare a derivation rule within a view (virtual table), for example, create view NetSalary( empNr, netPay ) as select empNr, salary – tax from Employee.

A second option is to include a generated column in the relevant base table. In the SQL standard, this could be done by including the following definition in the table definition given earlier: netPay generated always as (salary – tax).

Not all DBMSs support generated columns, and some that do support this feature use a different syntax. For example, in SQL Server we may simply declare netPay as (salary – tax).

A third option is to include a triggered column in the relevant base table. As discussed in Chapter 13, triggers on a table specify actions taken automatically when relevant columns are changed in a given way. The syntax for triggers varies with the DBMS. Assuming that a netPay column is included in the Employee table, the following trigger may be used in SQL Server to derive the net pay:

```
create trigger DeriveNetPay on Employee
after insert, update as
if update(salary) or update(tax)
begin
    update Employee
    set netpay = salary – tax
end
```

A fourth option is to include the derivation rule in a *stored procedure* that is invoked when needed (see Chapter 13). The examples of SQL given earlier are intended simply for overview purposes. The next two chapters explain SQL in detail.

Once the relational schema has been declared, the initial data definition stage is over. We then perform data maintenance by adding or deleting elementary facts and perhaps some existential facts (by inserting, deleting, and modifying rows of data). Data retrieval to list base or derived facts of interest can then be carried out (e.g., by formulating appropriate SQL select statements).

Data presentation and data security tasks are also typically addressed by creating input screens and output reports, and assigning data access rights to various user groups. These operations are discussed in detail in the next two chapters.

## Exercise 11.2

- 1. The following table contains details about members of a martial arts club. A null “?” indicates that a member has no phone or is unranked in any martial art. Black belt ranks are known as dan grades and lower ranks are kyu grades.

| Member | Gender | Phone | Arts and ranks |
| :--- | :--- | :--- | :--- |
| Adams B | M | 2052777 | judo 3-dan; karatedo 2-kyu |
| Adams S | F | 2052777 | judo 2-kyu |
| Brown C | F | 3579001 | ? |
| Collins T | M | ? | aikido 2-dan; judo 2-dan |
| Dancer A | F | ? | ? |

- (a) Specify a conceptual schema for this universe of discourse (UoD), assuming that rank (e.g., 3-dan) may be stored as a single value. Many other martial arts are possible.

- (b) Explain why the table shown is not a relational table.

- (c) Given that any fact type with a composite uniqueness constraint must be stored as a separate table, map your conceptual schema to a relational schema. Underline keys, mark optional fields in square brackets, and show any
