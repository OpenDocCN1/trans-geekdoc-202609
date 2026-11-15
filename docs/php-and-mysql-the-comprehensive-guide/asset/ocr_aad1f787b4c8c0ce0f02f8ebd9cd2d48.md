has become common practice to introduce a new column containing the consecutive number of the entry; this ensures uniqueness. Table 17.2 is the updated form.

| Column Name | Description |
|---|---|
| id | Number of the entry, primary key |
| name | Name of the registrant |
| email | Email address of the registrant |
| date | Date of entry |
| entry | Text of the entry |

# Table 17.2 Updated Contents of the Table "entry"

Most databases offer a separate data type for such artificially generated primary keys, a so-called autovalue. Whenever you insert a new data record into the table, the autovalue is incremented by 1. This ensures that every new entry in the table has a new number that is one higher. So you don't have to worry about anything in this respect; the database takes care of everything.

# 17.1.2 Data Types

Each column requires a defined data type. Although there are also (a few) databases that only work with strings internally (SQLite is one such candidate), typing within the database generally ensures greatly improved performance. The SQL standard defines a whole range of data types, of which Table 17.3 shows a relevant selection of the most important types.

| Data Type | Description |
|---|---|
| BLOB | Binary Large Object; (large) binary data |
| BOOLEAN | Truth value |
| CHAR(length) | String with fixed length |
| DATE | Date value |
| DECIMAL | Decimal value |
| INT | Integer |
| TIMESTAMP | Timestamp |
| VARCHAR(length) | String with variable length (maximum in brackets) |

# Table 17.3 A Selection of SQL Data Types