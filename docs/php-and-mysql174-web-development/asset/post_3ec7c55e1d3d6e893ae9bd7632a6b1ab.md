
TO 'rep_slave@'%' IDENTIFIED BY 'password';

Obviously, you should change the password to something else.

# Performing the Initial Data Transfer

You can transfer data from master to slave by taking a snapshot of the database at the current time. You can do this by using the procedures described for taking backups elsewhere in this time. You should flush the master tables with the following statement:

```
mysql> FLUSH TABLES WITH LOCK;
```

The reason for the read lock is that you need to ensure the place server is up to its binary log when the snapshot was taken. You can do this by executing this statement:

```
mysql> SHOW MASTER STATUS;
```

You should see output similar to the following from this statement:

| File | Position | Binlog_DO_DB | Binlog_Ignore_DB |
| mysql-bin.000001 | 107 | | |

Note the File and Position; you will need this information to set up the slave.

Now take your snapshot and unlock the tables with the following statement:

```
mysql> UNLOCK TABLES;
```

# Setting Up the Slave or Slaves

Begin by installing your data snapshot on the slave server.

Next, run the following queries on your slave:

```
change master to
master-host='server',
master-user='user',
master-password='password',
master-log-file='logfile',
master-log-pos=logpos,
start slave;
```

You need to fill in the data shown in italics. The server is the name of the master server. The user and password come from the GRANT statement you ran on the master server. The logfile and logpos come from the output of the SHOW MASTER STATUS statement you ran on the master server.

You should now be up and running.

# Further Reading

In these chapters on MySQL, we have focused on the uses and parts of the system most relevant to web development and to linking MySQL with PHP. If you want to know more about MySQL administration, you can visit the MySQL website at http://www.mysql.com.

You might also want to consult Paul Dubois' book MySQL (Fifth Edition), available from Addison-Wesley.

# Next

In the next chapter, “Advanced MySQL Programming,” we look at some advanced features of MySQL that are useful when writing web applications, such as how to use the different storage engines, transactions, and stored procedures.

# 13
## Advanced MySQL Programming

In this chapter, you learn about some more advanced MySQL topics, including table types, transactions, and stored procedures.

Key topics covered in this chapter include:

- The LOAD DATA INFILE statement
- Storage engines
- Transactions
- Foreign keys
- Stored procedures

## The LOAD DATA INFILE Statement

One useful feature of MySQL that we have not yet discussed is the LOAD DATA INFILE statement. You can use it to load table data from a file. It executes very quickly.

This flexible command has many options, but typical usage is something like this:
LOAD DATA INFILE "newbooks.txt" INTO TABLE books;

This line reads data from the file newborns.txt into the table books. (This assumes the books database is in use. You may also specify the database.table notation.) By default, data fields in the file must be separated by tabs and enclosed in single quotation marks, and each row must be separated by a newline (\n). All these characteristics are configurable with the various options of the LOAD statement; see the MySQL manual for more details.

To use the LOAD DATA INFILE statement, a user must have the FILE privilege discussed in Chapter 9, "Creating Your Web Database."

# Storage Engines

MySQL supports a number of different storage engines, sometimes called table types. This means that you have a choice over the underlying implementation of the tables. Each table in your database can use a different storage engine, and you can easily convert between them.

You can choose a table type when you create a table using

```
CREATE TABLE table TYPE=type....
```

The commonly available table types are:

- InnoDB—This type is the default and the storage engine you should use for most applications. These tables are transaction safe; that is, they support COMMIT and ROLLBACK. InnoDB tables also support foreign keys. They have the best read-write performance, at least they support row-level locking.

- MyISAM—This type used to be the default in older versions of MySQL. It is based on the traditional ISAM type, which stands for Indexed Access Method, a standard method for storing records and files. MyISAM adds a number of advantages over the ISAM type. MyISAM tables can be compressed, and they support full text searching. They are not transaction safe and do not support foreign keys. They can outperform InnoDB on low-read or read-only applications, but because they use table-level locking, they do not perform as well as InnoDB on read-write applications.

- MEMORY (previously known as HE)—These tables are stored in memory, and their indexes are hashed. This makes MEMORY tables extremely fast, but in a crash, your data will be lost. These characteristics make MEMORY tables ideal for storing temporary or derived data for read-heavy applications. They support table-level locking which is not ideal for a heavy-write or mixed read-write workloads. They cannot have BLOB or TEXT columns.

- MERGE—These tables allow you to treat a collection of MyISAM tables as a single table for the purpose of querying. This way you can work around maximum file size limitations on some operating systems.

- ARCHIVE—These tables store large amounts of data with a small footprint. This type of storage only supports INSERT and SELECT queries, not DELETE, UPDATE, or REPLACE. Additionally,

- CSV—These tables are stored in a single file containing comma-separated values. In most web applications, you will almost always use InnoDB. You should always use InnoDB when transactions are important, such as for financial data or situations in which INSERTS and SELECTs are interleaved.

# Transactions

## Introduction

Transactions are mechanisms for ensuring database consistency, especially in the event of error or a server crash. In the following sections, you learn what transactions are and how to implement them with InnoDB.

## Understanding Transaction Definitions

First, let's define the transaction. A transaction is a query or set of queries guaranteed either to be completely executed or not executed at all. The database is left in a consistent state or not the transaction completed.

To see why this capability might be important, considering a banking database. Imagine the situation in which you transfer money from one account to another. This action involves moving the money from one account and placing it in another, which would involve at least two queries. It is vital that these two queries are both executed or not. If you take the money out of one account and the power goes before you put it into another account, what happens? Does the money disappear?

You may have heard about ACID compliance. ACID is a way of describing requirements that transactions should satisfy:

- Atomicity—A transaction should be atomic; that is, it should be either completely or not executed.
- Consistency—A transaction should leave the database in a consistent state.
- Isolation—Uncommitted transactions should not be visible to other users of the database; that is, until transactions are complete, they should remain isolated.
- Durability—Once written to the database, a transaction should be permanent or durable.
