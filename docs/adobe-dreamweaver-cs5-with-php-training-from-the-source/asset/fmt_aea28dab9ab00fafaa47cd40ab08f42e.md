
• The names of the states have been moved to a separate table that stores each state’s United States Postal Service (USPS) abbreviation as `state_id` as well as the state’s name spelled out in full.

• The relationship between the two tables is created by storing `state_id` in both tables.

At first glance, this might seem a cumbersome way of organizing the data, but the immediate gain is that it avoids the danger of someone entering “Missisipi” or “Massachusets” in the `places` table by mistake. Misspellings and inconsistent data are a major cause of database item search failures.

Separating the states into a table of their own has the added advantage of making it easier to store other details related to the state, such as time zone and the state tax rate. If you store the tax rate in the `places` table, you need to track down every entry to update it. By putting the state details in a separate table, you make the change in just one place.

The relationship between tables is managed using primary and foreign keys.

#### **Managing relations with primary and foreign keys**

Each record in a database table should have a unique identifier called a *primary key*. Usually, this is a number automatically assigned by the database when the record is inserted. The number is incremented by 1 for each new record. The `places` table uses this type of primary key and stores it in the `place_id` column. However, you can use any combination of letters and numbers as the primary key, as long as each one is unique. USPS state abbreviations are unique, so they act as the primary key in the `states` table.

You link the records by using the primary key from one table as a reference in the other table. When a primary key is used like this, it’s known in the other table as a *foreign key*. Although a primary key can be used only once in its own table, it can be used many times as a foreign key.

The role of `state_id` can be summarized as follows:

• The `state_id` column is the primary key in the `states` table. Each value is unique.

• In the `places` table, `state_id` is a foreign key. Some values, such as CA and UT, are repeated several times.

This type of relationship—where a primary key from one table refers to multiple items in another table—is known as a *one-to-many relationship*. It can be represented diagrammatically like this:

![Image](graphics/fig05_05.jpg)

The key symbol next to `place_id` in the `places` table and `state_id` in the `states` table indicates they are the primary keys of their respective tables. The 1 indicates that each `state_id` in the `states` table is unique. The infinity symbol (∞) indicates that `state_id` can be repeated many times in the `places` table.

### ![Image](graphics/note.jpg)**NOTE:**

There’s no standard for representing database relationships. However, you might come across another set of symbols known as Crow’s Foot notation, which is explained in the sidebar “Using Crow’s Foot Notation to Represent Relationships.”

### **Using Crow’s Foot Notation to Represent Relationships**

There’s a bewildering variety of ways to represent database relationships diagrammatically. You don’t need to learn them, but it’s useful to be able to recognize them if you encounter them elsewhere. The following diagram shows the relationship between the `places` and `states` tables using Crow’s Foot notation. The name comes from the three-pronged link to the `places` table.

![Image](graphics/fig05_06.jpg)

In a one-to-many relationship, the “one” side is represented by a vertical line through the link. The “many” side is represented by the three-pronged crow’s foot. The relationship is further refined by a second vertical line on the “one” side and an empty circle on the “many” side. These indicate that a record must exist on the “one” side before it can be used as a foreign key on the “many” side.

It’s quite common in a one-to-many relationship for there to be records on the “one” side that don’t have corresponding records on the “many” side. For example, the `states` table lists all 50 states plus the District of Columbia, but the `places` table has records for only a handful of states. As more records get added to the `places` table, the number of times a `state_id` is used on the “many” side will change, but on the “one” side, the `state_id` will always be associated with only one record. This aspect of the relationship is reflected in the numbers in parentheses next to each table.

The (1,1) next to the `states` table means that `state_id` in the `places` table must refer to at least one—and only one—record in the `states` table. The (0,N) next to the `places` table means that `state_id` in the `states` table can refer to an unlimited number of records in the `places` table—or to none at all. Sometimes, the Crow’s Foot symbols are used on their own, as are the numbers in parentheses.

Although one-to-many relationships are very common in database design, the task facing a database designer isn’t always that simple. Here’s a spreadsheet with details of several books.

![Image](graphics/fig05_07.jpg)

Each book has only one publisher, so it’s easy to split the publishers’ details into a separate table. But what about the authors? Some authors have written more than one book, and some books have more than one author. This is known as a *many-to-many relationship*.

The normal way to handle a many-to-many relationship is with an intermediate table that cross-references the primary keys in the other tables. The following diagram shows the same information distributed across four tables.

![Image](graphics/fig05_08.jpg)

### ![Image](graphics/note.jpg)**NOTE:**

The normal convention is to put the primary and foreign key columns at the beginning of each table. The order has been changed in the preceding diagram to make the continuity of the relationships easier to follow.

Details of the authors, book titles, and publishers have been stored in separate tables called `authors`, `books`, and `publishers`. Each table has its own primary key: `author_id`, `book_id`, and `pub_id` respectively.

To find who wrote which book, a cross-reference table called `author2book` lists `author_id` and `book_id` in pairs as foreign keys. So, `author_id` 1 is associated with both `book_id` 1 and `book_id` 6. Each pair in the cross-reference table is unique, so it acts as a combined primary key.

The one-to-many relationship between the `books` and `publishers` tables is the same as in the earlier example. The `pub_id` column is the primary key of the `publishers` table and is stored as a foreign key in the `books` table.

The following diagram shows how the cross-reference table converts the many-to-many relationship into separate one-to-many relationships.

![Image](graphics/fig05_09.jpg)

In addition, you can also have a *one-to-one relationship*, but this is relatively uncommon. Normally, data that goes logically together is stored in the same table. However, you might want to store data in a separate table for security reasons. For example, in a human resources database, an employee’s salary details might be kept in a separate table that only payroll staff is permitted to access.

### ![Image](graphics/tip.jpg)**TIP:**

If you have no previous experience working with databases, take some time to make sure you understand the principle of one-to-many and many-to-many relationships. They are indispensable to successful database design. At this stage, don’t worry about how primary and foreign keys are generated. Part of the process is automatic. The rest is handled by using simple database queries.

#### **Deciding how to organize your data**

As you’ve already seen, relational databases don’t store everything in one massive table. So, one of your first tasks is to decide on your table structure. There’s no single “right” way to do it. Each database is different, but the following guidelines should help:
