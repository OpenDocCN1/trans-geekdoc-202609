# Building Databases

You may have noticed that we have created a many-to-many (M:N) relationship between the characters and their powers (a character can have multiple powers, and many characters may have the same power). There are two tables with primary keys, and a linking table between them has foreign keys, one for each of the tables. The combination of the foreign keys is a primary key for the char_power table. This enables the M:N relationship.

Just for fun, let's add a small table that has the superheroes and villains, and vice versa. This is another M:N relationship because any superhero can have multiple villain enemies, and any villain can have multiple superhero enemies. Of course, we have the character table as one of the “many” sides of the equation—you figure out which table we use for the other “many” side? If you said the table, you are correct! This is just like the character-power relationship, but this time we refer the table to itself via a good_bad linking table. The good_guy_id and badguy_id columns each link the id column in the character table. Each column in the good_bad table is a foreign key, and both columns make up a composite key.

| goodguy_id* | badguy_id* |
|---|---|
| 1 | 3 |
| 2 | 3 |

And just like, you have created your database design. Congratulations! Now you have a “map” that will help you create your database tables on the server. Not only that, but you just normalized your database design by modifying your database structure so that dependencies make sense, and there is no redundant data. In fact, you have actually gone through the proper normalization steps of First, Second, and Third Form.

# What’s So Normal About These Forms?

Remember we that we were calling the first table “zero”? That's called Zero Form. It is basically the raw data, and it is a very flat structure, with lots of repeated data. You see like this-times when a small company keeps records of its customers in a spreadsheet.

The first pass through the table, which we called “one,” was the first step of normalization, called “First Normal Form,” or INF. This step requires that you eliminate all repeated data in columns (which we did with the power column), create separate rows for each group of related data, and identify each with a primary key. Our first step satisfies the requirements of INF.

You can see where we’re going with this, can’t? The Second Normal Form (2NF) requires that you put places of data in multiple rows in separate tables. We did that by separating the power data into its own table. Second Normal Form also requires that we create a relationship with the original table by creating a foreign key. We did that in pass “two,” when we satisfied the requirements for 2NF.

On our third pass, we removed all the columns not related to the primary key (City and State), and used the ZIP Code as the foreign key to the new city_state table. Third Normal Form (3NF) is then satisfied. Congratulations! You normalized a database like the pros do.

245