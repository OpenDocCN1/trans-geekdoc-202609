
# Real-World Database Design

Now that you have a basic understanding of databases, SQL, and MySQL, this chapter begins the process of taking that knowledge deeper. The focus of this chapter, as the title states, is real-world database design. Like the work done in [Chapter 4](#ch04.html#ch04), "Introduction to MySQL," much of the effort herein requires paper and pen, and serious thinking about what your applications will need to do.

The chapter begins with thorough coverage of database *normalization*: a vital approach to the design process. After that, the chapter turns to design-related concepts specific to MySQL: indexes, table types, language support, working with times, and foreign key constraints.

By the end of this chapter, you'll know the steps involved in proper database design, understand how to make the most of MySQL, and plan a couple of multi-table databases. In the next chapter, you'll learn more advanced SQL and MySQL, using these new databases as examples.

## Normalization

Whenever you are working with a relational database management system such as MySQL, the first step in creating and using a database is to establish the database's structure (also called the database *schema*). Database design, aka *data modeling*, is crucial for successful long-term management of information. Using a process called *normalization*, you carefully eliminate redundancies and other problems that would undermine the integrity of your database.

The techniques you will learn over the next few pages will help to ensure the viability, usefulness, and reliability of your databases. The primary example to be discussed—a forum where users can post messages—will be more explicitly used in [Chapter 17](#ch17.html#ch17), "Example—Message Board," but the principles of normalization apply to any database you might create. (The *sitename* example as created and used in the past two chapters *was* properly normalized, even though normalization was never discussed.)

Normalization was developed by an IBM researcher named E.F. Codd in the early 1970s (he also invented the relational database). A relational database is merely a collection of data, organized in a particular manner, and Dr. Codd created a series of rules called *normal forms* that help define that organization. This chapter discusses the first three of the normal forms, which are sufficient for most database designs.

Before you begin normalizing your database, you must define the role of the application being developed. Whether it means that you thoroughly discuss the subject with a client or figure it out for yourself, understanding how the information will be accessed dictates the modeling. Thus, this process will require paper and pen rather than the MySQL software itself (although database design is applicable to any relational database, not just MySQL).

In this example, I want to create a message board where users can post messages and other users can reply. I imagine that users will need to register, then log in with an email address/password combination, in order to post messages. I also expect that there could be multiple forums for different subjects. I have listed a sample row of data in **[Table 6.1](#ch06.html#ch06table01)**. The database itself will be called *forum*.

**Table 6.1. Sample Forum Data**

![Image](graphics/06tab01.jpg)

> **Tip**
>
> One of the best ways to determine what information should be stored in a database is to think about what questions will be asked of the database and what data would be included in the answers.

> **Tip**
>
> Always err on the side of storing *more* information than you might need. It's easy to ignore unnecessary data but impossible to later manufacture data that was never stored in the first place.

> **Tip**
>
> Normalization can be hard to learn if you fixate on the little things. Each of the normal forms is defined in a very cryptic way; even when put into layman's terms, they can still be confounding. My best advice is to focus on the big picture as you follow along. Once you've gone through normalization and seen the end result, the overall process should be clear enough.

### Keys

As briefly mentioned in [Chapter 4](#ch04.html#ch04), *keys* are integral to normalized databases. There are two types of keys: *primary* and *foreign*. A primary key is a unique identifier that has to abide by certain rules. They must:

- Always have a value (they cannot be `NULL`)
- Have a value that remains the same (never changes)
- Have a unique value for each record in a table

A good real-world example of a primary key is the U.S. Social Security number: each individual has a unique Social Security number, and that number never changes. Just as the Social Security number is an artificial construct used to identify people, you'll frequently find creating an arbitrary primary key for each table to be the best design practice.

The second type of key is a foreign key. Foreign keys are the representation in Table B of the primary key from Table A. If you have a *cinema* database with a *movies* table and a *directors* table, the primary key from *directors* would be linked as a foreign key in *movies*. You'll see better how this works as the normalization process continues.

The *forum* database is just a simple table as it stands ([Table 6.1](#ch06.html#ch06table01)), but before beginning the normalization process, identify at least one primary key (the foreign keys will come in later steps).

#### To assign a primary key

**1.** Look for any fields that meet the three tests for a primary key.

In this example ([Table 6.1](#ch06.html#ch06table01)), no column really fits all of the criteria for a primary key. The username and email address will be unique for each forum user but will not be unique for each record in the database (because the same user could post multiple messages). The same subject could be used multiple times as well. The message body will likely be unique for each message but could change (if edited), violating one of the rules of primary keys.

**2.** If no logical primary key exists, invent one (**[Table 6.2](#ch06.html#ch06table02)**).

**Table 6.2. Sample Forum Data**

![Image](graphics/06tab02.jpg)

Frequently, you will need to create a primary key because no good solution presents itself. In this example, a *message ID* is manufactured. When you create a primary key that has no other meaning or purpose, it's called a *surrogate* primary key.

> **Tip**
>
> As a rule of thumb, I name my primary keys using at least part of the table's name (e.g., *message*) and the word *id*. Some database developers like to add the abbreviation *pk* to the name as well. Some developers just use *id*.

> **Tip**
>
> MySQL allows for only one primary key per table, although you can base a primary key on multiple columns (this means the combination of those columns must be unique and never change).

> **Tip**
>
> Ideally, your primary key should always be an integer, which results in better MySQL performance.

### Relationships

Database relationships refer to how the data in one table relates to the data in another. There are three types of relationships between any two tables: *one-to-one*, *one-to-many*, or *many-to-many*. (Two tables in a database may also be unrelated.)

A relationship is one-to-one if one and only one item in Table A applies to one and only one item in Table B. For example, each U.S. citizen has only one Social Security number, and each Social Security number applies to only one U.S. citizen; no citizen can have two Social Security numbers, and no Social Security number can refer to two citizens.
