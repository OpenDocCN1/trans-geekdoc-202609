# Chapter 12: Introducing Databases and SQL

Here comes the clever bit. First, add the playerNumber column back into the matchLog table:

| playerNumber | datePlayed |
|---|--|
| 42 | 03/03/04 |
| 6 | 03/03/04 |
| 2 | 03/03/04 |
| 14 | 03/25/04 |
| 2 | 02/25/04 |
| 25 | 02/25/04 |
| 6 | 02/25/04 |
| 7 | 02/25/04 |

Now, by linking the values of the playerNumber fields in both the player and matchLog tables, you can associate each player with the date (or dates) he played. The two tables are said to be joined by the playerNumber field. The matchLog table is known as a foreign key because it references the primary key in the players table, and you can't have a playerNumber value in the matchLog table that isn't also in the players table.

Because the only repeating player information in the matchLog table is the playerNumber field, you've saved some storage when compared to the original table. It's now easy to change the nickname of a player, you only have to change it in one place: a single row in the players table.

This type of connection between the two tables is known as a one-to-many relationship, because one player may be associated with many matchLog records (assuming the player plays in more than one match). This is a very common arrangement of tables in a relational database.

You're probably wondering how to actually retrieve information from these two tables, such as the nicknames of the players who played on March 3, 2004. This is where SQL comes in. You are introduced to SQL in the next section.

# Talking to Databases with SQL

The Structured Query Language is a simple, standardized language for communicating with relational databases. SQL lets you do practically any database-related task, including creating databases and tables, as well as saving, retrieving, deleting, and updating data in databases.

As mentioned previously, this chapter concentrates on MySQL. The exact dialect of SQL does vary among different database systems, but because the basic concepts are similar, the SQL skills you learn on one system can easily be transferred to another. In this section you examine some basic features of SQL: data types, indexes (keys), statements, and queries.

343