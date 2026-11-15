
Even with no joins, similar problems with nulls arise if the view excludes a column used in its search condition. For example, suppose we try the following insertion on our FemaleCompScientist view:

```
insert into FemaleCompScientist
values ( 105, 'Bird', 'L', 'Lec' )
```

If we allow this update, is "Bird, L" included in the result? Given our earlier view definition, if the update were accepted it would translate into the following row being inserted into the Academic table: (105, “Bird, L”, null, null, “Lec”). The new row fails the view definition because the condition ( dept = 'CS' and gender = 'F' ) evaluates to unknown. So, if the update is accepted, it is not part of the view!

It is better to reject any update that fails to satisfy the view definition. This is done by appending “with check option” to the view definition. For example, the following view may be used for computer science professors:

```
create view CSProfessor ( empNr, name, dept, rank ) as
select empNr, empName, dept, grade
from Academic
where grade = 'Prof' and dept = 'CS'
with check option
```

The following attempts to update this view would now have the results shown.

```
insert into CSProfessor
values ( 106,'Wirth N','CS','Prof' ) → accepted
insert into CSProfessor
values ( 107,'Russell B','MA','Prof' ) → rejected
update CSProfessor
set rank = 'Lec'
where empNr = 103 → rejected
```

The type of view we have considered so far is basically a predefined query on one or more base tables. The result of the query is not stored in the view, only the query definition. A subsequent query on the view is combined with the query in the view definition, and the composite query is run against the base table(s). This ensures that the result is always up to date with the content of the base tables, but may be inefficient if a view is queried frequently.

Another option is to execute the query defined for the view and cache the result. Now, the view represents an actual data structure held in physical storage, not just the definition of a data structure. This is known as a _materialized view_. Such views have obvious advantages in efficiency, but subsequent changes to data in the base table(s) can lead to the view becoming increasingly unrepresentative of the “real” data. Commercial systems that support materialized views normally provide some mechanism for periodically refreshing them.

SQL:2003 added a new option to the create table statement to allow for the creation of tables based on the result of a select statement. This provides functionality somewhat similar to a materialized view. The basic syntax is:

```
create table tablename as select-statement
{ with data | with no data }
```

If the intention is to populate the table with data at the time of its creation, the with data option must be specified. If it is not, an empty table will be created with the appropriate columns but no data. A better description of the result is a materialized query table because no dependency is established between the new table and the underlying query expression. After the table is initially populated, updates to the tables in the query expression will not automatically be reflected in the new table.

## Exercise 13.3

### 1. Specify SQL DDL statements to create the following relational schema.

Movie ( movieCode, title, categoryCode ) { G, PG, M, MA, R }
VideoTape ( movieCode, copyNr, purchaseDate, status, [comment, writtenOff] ) { Good, OK, Poor, X } { Y, N } writtenOff exists iff status = 'X'
LoanItem ( loanNr, movieCode, copyNr, cost, [returnDate] )
Loan ( loanNr, issueDate, cardNr )
Customer ( cardNr, customerName, address )

### 2. A conceptual subschema, its relational tables, and a sample population are shown.

ParentOf:

| parent | child |
|--------|-------|
| Ann | Chris |
| Ann | David |
| Bill | Chris |
| Bill | David |
| Bill | Ernie |
| Chris | Fred |
| David | Gina |
| Gina | Helen |

BrotherOf:

| brother | sibling |
|---------|---------|
| Ian | Ann |
| John | Ann |
| Ken | Bill |
| Bill | Ken |
| David | Chris |
| Ernie | Fred |
| Fred | Ernie |

is a parent of
Person (firstname)
is a brother of

- (a) Complete the following derivation rule: Person₁ is an uncle of Person₂ if ...
- (b) Specify this rule as a view *UncleOf* ( uncle, child ) in SQL.
- (c) Formulate the query “Who is an uncle of whom?” in SQL, using the view.
- (d) Formulate (c) in SQL without using the view.
- (e) Formulate in SQL: Who is recorded as having a parent but not an uncle?

### 3. The following schema shows part of a database that holds information about repair technicians and the types of assemblies that they are competent to repair. Different technicians may be competent at repairing different assemblies. Assemblies may be parts of other assemblies, unless, of course, they are a top-level assembly.

![](img/1344db3eba3d550e6edb009556fcd95c_686_0.png)

- (a) Create the tables for this schema in the most convenient SQL form. Assume that empNr is some unique integer, assemblyCode is some unique 10-character string, complexityNr is an integer, and firstName, lastName, and certificationRef are varchar strings of appropriate length. isTopLevel and hasReport are flags that reflect a Boolean condition. For this exercise, specify certificationRef simply as a unique column.
- (b) Is the order of creation of the tables important?
- (c) Both of the Technician and Assembly tables could represent hierarchies (how can you tell?). What would be the distinguishing characteristics of a node at the top of a Technician hierarchy and a node at the top of an Assembly hierarchy?

### 4. Given the schema defined in Q1, we want to identify technicians with high-level skills.
- (a) Define a view for all technicians that are competent to work on an assembly of complexity 6 or higher. This should list only the Technician's firstName and lastName, assemblyCode, and complexityNr.
- (b) Is this view updateable? Explain your reasoning.

### 5. Do you agree or disagree with the following statements about ordinary SQL views? Explain your reasoning.
- (a) Views create temporary tables that can be queried using select statements.
- (b) A select statement associated with a view may not reference other views.
- (c) Defining a large number of views will create additional demands for data storage.
- (d) A view defined on exactly one base table is always materialized.
- (e) A view can be queried in much the same way as a table, but updates are more restricted.

## 13.4 SQL: Triggers

Triggers provide yet another way to change table populations. Although not included in the standard until SQL:1999, triggers have been used by commercial dialects for many years. As well as enforcing constraints, triggers may be used to perform other actions, including computation of derived columns, maintaining audit or summary data in other tables, and initiating external actions such as sending email.

A trigger specifies a set of SQL statements that will be executed automatically when a given event takes place on a table (or, in some circumstances that we'll discuss shortly, a view). The event causing the execution of the trigger can be an attempt to insert new rows, delete existing rows, or update existing rows in the table. The trigger actions can be specified to take place either immediately before or immediately after the related operation (insert, update, or delete) takes place.

Multiple triggers can be defined on a table. All before triggers will execute before any operation is carried out on the table, including constraint checking. This provides an opportunity to examine the action that is about to take place and to modify it if necessary. All after triggers will execute after constraint checking has been performed and the action has taken place, but before any changes are committed. This provides an opportunity to examine changes that have been made and to roll back the associated transaction if required. Different vendors may provide facilities for specifying the trigger sequence if there are multiple before triggers, and similarly for after triggers.

Within the body of a trigger, it's possible to reference the contents of one or two transition tables. These contain rows that are being affected by the trigger event. The columns of the transition tables match the column definitions of the table on which the trigger is based. For a delete trigger, there is an old transition table containing the rows being deleted. For an insert trigger, there is a new transition table containing the rows being inserted. An update trigger has both an old transition table containing the row data prior to the update and a new transition table containing the row data after the update. In the update case, every row in the old transition table will have a corresponding row in the new transition table. Transition tables only exist for the duration of the trigger and cannot be accessed from outside the trigger.

The trigger action can be specified to take place either at the row level or at the statement level. In the former case, the action takes place for each row of the transition table. In the latter case, the action occurs just once, when the trigger event takes place. Depending on whether the trigger has been defined at the row level or the statement level, the trigger code can access transition variables that are either individual rows from the old/new transition tables or the complete transition tables.
