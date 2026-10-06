# 9.3 APPLICATIONS OF HASH TABLES

Some applications of hash tables are:

# 1. Database Systems

Generally, database systems try to optimise between two types of access method: sequential and random. Hash tables are an important part of efficient random access because they provide a way to locate data in a constant amount of time.

# 2. Symbol Tables

The tables used by compilers to maintain information about symbols from a program. Compilers access information about symbols frequently. Therefore, it is important that symbol tables be implemented very efficiently.

# 3. Tagged Buffers

A mechanism for storing and retrieving data in a machine - independent manner. Each data member resides at fixed offset in the buffer. A hash table is stored in the buffer so that the location of each tagged member can be ascertained quickly. One use of tagged buffer is sending structured data across a network to a machine whose byte ordering and alignment may not be same as the original host's. The buffer handles these concerns as the data is stored and extracted member by member.

# 4. Data Dictionaries

Data Structures that support adding, deleting, and searching for data. Although the operations of a hash table and a data dictionary are similar, other data structures may be used to implement data dictionaries. Using a hash table is particularly efficient.

# 9.4 HASHING

Hashing is a technique to convert a range of key values into a range of indexes of an array. We're going to use modulo operator to get a range of key values. Consider an example of hash table of size 20 with following items stored in it. Item are in (key, value) format.

![](bbox=[0.223, 0.715, 0.776, 0.831])

| Index | Value |
|---|---|
| 0 | Value_1 |
| 1 | Value_2 |
| 2 | Value_3 |
| 3 | Value_4 |

+   - (1,20)
- (2,70)
- (42,80)