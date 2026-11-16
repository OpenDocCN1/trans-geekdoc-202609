A plain files based data model is really useful when dealing with large amounts of data or when very specific searches must be done over a big volume of information and the queries can't really be adapted to SQL or XML related common queries. For example, search engines such as Google (http://www.google.com/) use a data model based on plain files to maintain the repository of information that is collected from the Web. The extra time needed to design, code, and maintain the programs that manage this information is compensated with superb performance that is really specific to the application.

Using a plain file based data model in PHP is easy since PHP has plenty of file manipulation functions such as flock(), fwrite(), fgets(), fputs(), fopen(), fclose(), fseek(), ftell(), unlink(), file_exists(), filesize(), and so on. These have been explained in Chapter 9.

# # Relational Database Model

This is the most common approach for web applications today. SQL statements are used to insert, delete, and update the data. The model is defined by an entity relationship diagram (ERD), where you indicate the entities used and the relationship between them. Then you can convert the ERD into a table structure and use this structure to establish table relationships. Let's see how we can model our poll application using a relational database:

```
Polls table:
polid integer(4)
pollname varchar(40)
question varchar(200)

Options table:
polid integer(4)
option varchar(80)
votes integer(4)

Comments table:
polid integer(4)
comment text
```

This structure is similar to the plain file model except that tables replace files. We don't have to bother about the internal structure of tables since this is what a Database Management System (DBMS) is for. We don't have to update or delete each entity, since we do that with SQL statements.

DBMS gives these common advantages:

+   - Higher integrity of data (not guaranteed with files)

+   - Higher consistency of data using multiple access

+   - Higher security

+   - Common query language

+   - Different views using same structures for multiple uses

+   - Independence of file structures

+   - No redundancy of information

+   - Relational mapping with OO

+   - Less hard drive space from loss-less joins