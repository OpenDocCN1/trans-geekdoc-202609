
The procedure body is made up of any legal combination of SQL statements. Stored procedures may make calls to other procedures, and a procedure may call itself recursively. An implementation may place restrictions on the number of levels of nesting permitted, for example, SQL Server allows nesting up to 32 levels deep. Stored procedures can also be called from within a trigger, which gives both the advantage of automatic invocation (when the relevant trigger event occurs) and the modularity offered by a stored procedure. For instance, we may want to apply the same constraint under several different circumstances, which we could do by having several different triggers call the same stored procedure.

One SQL statement that requires attention in a stored procedure is the return statement. Once a return is encountered, the stored procedure is exited immediately, so a return is often associated with a branch of a test condition, along the lines of “if x is the case then return, otherwise, ...”. Although not necessarily enforced by an implementation, a recommended practice is to use a value associated with the return statement to indicate status. Typically, a return code of zero indicates “all is well”, and a nonzero value is used to indicate a specific error condition that had been encountered. The results of any computation carried out by the stored procedure should be returned through out parameters rather than using the return value.

## Exercise 13.5

The following schema shows part of a database that holds information about repair technicians and the types of assemblies that they are competent to repair. Different technicians may be competent at repairing different assemblies.

![](img/1344db3eba3d550e6edb009556fcd95c_692_0.png)

- 1. Write a stored procedure that inserts a new row into the Technician table and returns a result of zero if it succeeds. If the new row would create a loop in the technician—supervisor hierarchy, the insert should not be performed and the procedure should return the result code 99. Use recursion to check for loops in the hierarchy. You can assume that no hierarchy will be more than 10 levels deep.

- 2. Most commercial systems provide a function that returns the last identity value used in the update of a table. The empNr column in the Technician table would be a typical application for an identity column. Write a stored procedure that adds a new row to the Technician table and returns as an **out** parameter the identity value that was generated for the new row.

- 3. Assume that we have a table with the schema Currency ( code, symbol, rate ), where code identifies a particular currency, symbol is a single Unicode character, and rate is a conversion rate. Write a function that takes a currency code and a decimal number as parameters and returns a string consisting of the number provided multiplied by the rate for the currency code appended to the appropriate currency symbol. For example, if the Currency table contains a row ("USD", "$", 2.0), given the parameters "USD" and 100.00 the function should return "$200.00". The returned amount should have two decimal digits.

## 13.6 More Database Objects

### Sequences

In SQL, a sequence is a database object that automatically generates a succession of values; note that this is a completely different meaning of the word “sequence” from its usage in XQuery, as we’ll see later. Sequence objects were first introduced in SQL:2003 and are useful whenever it’s necessary to produce a unique key value. Having the unique value generated inside the database, instead of in an external application, reduces the possibility of issues arising in areas such as performance and concurrency. Some SQL implementations may precompute the next values in a sequence and cache these ready for immediate use.

In some respects, a sequence is similar to an identity column in a table. However, unlike an identity column, a sequence is not tied to one specific table, and sequence values are unique within a database, rather than being unique within a table. Sequences can be created using the following syntax.

```
create sequence sequence-name
[ as data-type | start with start-value |
increment by increment-value |
maxvalue value | no maxvalue
minvalue value | no minvalue |
cycle | no cycle [ ... ] ]
```

The data type must be a numeric type with a scale of zero (e.g., integer). The options are similar to those for identity columns, which were discussed earlier. One additional feature of sequences is that some implementations also allow a zero increment, so that the sequence effectively becomes a global constant value.

The standard syntax for obtaining the next value from a sequence is:

```
next value for sequence-name
```

but some implementations may have variations on this. They may also provide some means of accessing the last sequence number generated without generating a new one, such as:

previous value for sequence-name

SQL also defines drop sequence and alter sequence commands, but because these work in the obvious way, we won’t discuss them here.

### Indexes

An index is typically an ordered binary tree of key values, with pointers to the locations of the full records used to store the data. Because indexes are relevant only for physical modeling, not logical modeling, the SQL standard will never mention them. However, most commercial systems allow users to explicitly create and drop indexes, using syntax such as create [ unique ] index indexname on tablename ( index-column [ asc | desc ] [...] ) and drop index indexname. Optimizers use indexes to improve performance and may create and drop indexes themselves. If supported, the unique index option provides one way of enforcing uniqueness constraints. However, most uniqueness constraints are better declared using primary key or unique declarations, although uniqueness constraints on optional columns usually require triggers. Indexes are often created automatically for primary and foreign keys.

Indexing can dramatically improve query performance, especially for large tables, because indexes often allow random access in main memory rather than sequential disk access. Some commercial systems may also allow a chosen index to be specified as clustered. This creates an alignment between the logical sequence of values in the indexed column(s) and the order in which rows are physically stored, potentially offering improved performance in retrieving row data. Obviously, if a table has multiple indexes, only one can be selected as the basis for clustering; typically, this will be the index on the primary key column(s).

Although query efficiency (and hence perhaps constraint enforcement performance) can be improved by indexing, there is a price to be paid. Indexing may slow down the updating of a table because any change to the data will involve not only a change to the base table, but also to any indexes that have been defined. However, this trade-off may still be acceptable, depending on the situation. Individual DBMSs may offer many different kinds of indexes, and strategies for choosing indexes may also vary from one DBMS to another. Because this book is primarily concerned with conceptual and logical modeling, index strategies will not be considered further.

### Cursors

A cursor is essentially a mechanism to provide row-at-a-time access to the results of a pre-specified select statement. The result is retained for as long as the cursor is being used (during which time the cursor is said to be open). Using a cursor is a four-stage process.

- 1. The cursor is *declared*, which defines the *select* statement and the mode of operation of the cursor.
- 2. The cursor is *opened*, at which time the associated *select* statement is executed and the temporary result table is formed.
- 3. The application navigates through the result table, typically row by row, to *fetch* the data needed for any required operations.
- 4. When the application has completed its work, the cursor is *closed*, which results in deletion of the results of the original *select* statement.

It's fairly common practice for these steps to be controlled directly from an application program. This is one reason why cursors have a reputation for sluggish operation, which is discussed in more detail later.

Most vendors support the basic SQL-92 syntax for cursor declaration, which is shown here. Some details were added in later versions of the standard, but these did not affect the basic SQL cursor concept.

```
declare cursor-name [ sensitive | insensitive ] [ scroll | no scroll ] cursor
for select_statement
    [ for { read only | update [ of column_name [, ... ] ] } ]
```

Optionally, the cursor can be declared as *for read only* (which improves performance if updating is not required) or *for update*, possibly restricted to specific columns. A cursor that is declared as *insensitive* makes a temporary copy of the data to be used, and all data requests are answered from this temporary table. Modifications therefore cannot be made to base tables. If *insensitive* is omitted, or the sensitive option is chosen, changes made to the underlying tables may be reflected in subsequent fetches. The *scroll* option specifies that a range of navigation operations should be enabled for the cursor. If omitted, or if the *no scroll* option is chosen, the cursor is limited to just fetching the next row of the result. Once a cursor is defined, it can be opened. The syntax could hardly be simpler:

```
open cursor-name
```

There's no option for the open clause to change the *select* statement; it simply executes the one already defined in the associated cursor declaration. It also positions the cursor to point just before the first row of the result set. Given an open cursor, data can be fetched from the results produced by the *select* statement.

```
fetch [ [ next | prior | first | last | { absolute | relative } ] from ] cursor-name
into target-specification [, ... ]
```

In the navigation options, *next* fetches the next row from the current cursor position; *prior* fetches the previous row; *first* and *last*, respectively, fetch the first and last rows of the result set; *absolute* retrieves a row by its row number in the result set; and *relative* moves the cursor the specified number of rows backward or forward in the result set. If none of the
