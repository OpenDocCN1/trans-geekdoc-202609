# # Chapter 1: Database Design with MySQL

| Contact_id | Contact_first_name | Contact_last_name |
|---|---|--|
| 1 | Jon | Doe |
| 2 | AI | Banks |

| Newsletter_id | Newsletter_name |
|---|---|n| 1 | Weekly |
| 2 | Bi-Weekly |
| 3 | Annual |
| 4 | Semi-annual |

| Client_id | Newsletter_id |
|---|--|
| 1 | 1 |
| 2 | 2 |
| 2 | 3 |
| 2 | 4 |

Figure 1-4: Tables with a many-to-many relationship

With this structure, any number of contacts can have any number of newsletters and any number of newsletters can be sent to any number of contacts.

# # Features MySQL Does Not Support

MySQL is a polarizing piece of software in the applications community. It has aspects that many developers like: it's free, it doesn't take up a whole lot in the way of resources, it's very quick, and it's easy to learn compared to packages Oracle or Sybase. However, MySQL achieves its speed by doing without features common in other databases, these shortcomings will keep many from adopting MySQL for their applications. But, for many, the lack of certain features shouldn't be much of a problem. Read and decide for yourself.

# ## Referential integrity

Every example used in the previous pages made of foreign keys. A foreign key is a column that references the primary key of another table in order to maintain a relationship. In Table 1-4, the Contacts table contains a company_id column, which references the primary key of the Companies table (Table 1-3). This column is a foreign key to the Companies table.