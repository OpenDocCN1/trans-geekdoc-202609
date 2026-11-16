| series |
| :--- |
| PK | series_ID |
| | book_series |

In the series table, the primary key is series_ID. Note that the series_ID field also appears in the details table. In the details table, the series_ID field is a **foreign key**. It refers to the primary key of the foreign table, series, to establish a relationship between the records of this table and the foreign table. Like primary keys, foreign keys may consist of more than one field:

![](bbox=[0.34, 0.26, 0.7, 0.375])

There are two possible ways of determining a primary key:

+   **Natural or Logical Key**
+   The preferred way to allocate a primary key is to find something inherent in the data which uniquely identifies the record. In the details table, each book already has an ISBN, and each ISBN is unique, so it can be used as the unique identifier (the natural primary key).

+   **Surrogate Key**
+   When a logical key cannot be found, the alternative is to introduce a surrogate key. A surrogate key is an additional field whose only purpose is to provide a unique primary key. It is usually an integer field. In the series table, the series_ID integer field was added to guarantee unique records. It is therefore a surrogate primary key. Surrogate keys are often a good idea, even when dealing with a unique identifier, such as ISBN numbers. They can help make tables easier to manipulate because they don't correlate directly to any real data in the row. In other words, they help abstract the unique identifier from the actual data.

Surrogate keys are very common in database applications, partly because there are many instances when there is no derivable logic key. For instance, in a table of customer data, a numeric customer_ID field is normally necessary, since the data collected about customers, like their name and address, are not likely to contain uniquely identifying attributes.

# Normalization

Let's look at the table books:

| books |
| :--- |
| PK | book_ID |
| | ISBN |
| | book_title |
| | auth_name |