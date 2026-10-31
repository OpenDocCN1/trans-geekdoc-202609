![](bbox=[0.18, 0.11, 0.78, 0.45])

Figure 1-4: Tables with a many-to-many relationship

With this structure, any number of contacts can have any number of newsletters and any number of newsletters can be sent to any number of contacts.

# Features MySQL Does Not Support

MySQL is a polarizing piece of software in the applications development community. It has aspects that many developers like: it’s free, it doesn’t take up a whole lot in the way of resources, it’s very quick, and it’s easy to learn compared to packages like Oracle and Sybase. However, MySQL achieves its speediness by doing without features common in other databases, and these shortcomings will keep many from adopting MySQL for their applications. But, for many, the lack of certain features shouldn’t be much of a problem. Read and decide for yourself.

# Referential integrity

Every example used in the previous pages made use of foreign keys. A foreign key is a column that references the primary key of another table in order to maintain a relationship. In Table 1-4, the Contacts table contains a company_id column, which references the primary key of the Companies table (Table 1-3). This column is a foreign key to the Companies table.