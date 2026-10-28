# The seven normal forms

| Normal form | Description |
|---|---|
| First (1NF) | The value stored at the intersection of each row and column must be a scalar value, and a table must not contain any repeating columns. |
| Second (2NF) | Every non-key column must depend on the entire primary key. |
| Third (3NF) | Every non-key column must depend only on the primary key. |
| Boyce-Codd (BCNF) | A non-key column can't be dependent on another non-key column. This prevents transitive dependencies, where column A depends on column C and column B depends on column C. Since both A and B depend on C, A and B should be moved into another table with C as the key. |
| Fourth (4NF) | A table must not have more than one multivalued dependency, where the primary key has a one-to-many relationship to non-key columns. This form gets rid of misleading many-to-many relationships. |
| Fifth (5NF) | The data structure is split into smaller and smaller tables until all redundancy has been eliminated. If further splitting would result in tables that couldn't be joined to recreate the original table, the structure is in fifth normal form. |
| Domain-key (DKNF) or Sixth (6NF) | Every constraint on the relationship is dependent only on key constraints and domain constraints, where a domain is the set of allowable values for a column. This form prevents the insertion of any unacceptable data by enforcing constraints at the level of a relationship, rather than at the table or column level. DKNF is less a design model than an abstract “ultimate” normal form. |

# The benefits of normalization

+   - Since a normalized database has more tables than an unnormalized database, and since each table has an index on its primary key, the database has more indexes. That makes data retrieval more efficient.
+   - Since each table contains information about a single entity, each index has fewer columns (usually one) and fewer rows. That makes data retrieval and insert, update, and delete operations more efficient.
+   - Each table has fewer indexes, which makes insert, update, and delete operations more efficient.
+   - Data redundancy is minimized, which simplifies maintenance and reduces storage.

# Description

+   - Each normal form assumes that the design is already in the previous normal form.
+   - A database is typically considered to be normalized if it is in third normal form. The other four forms are not commonly used and are not covered in detail in this book.