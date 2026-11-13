| StudentID | ClubTitle | TeacherName |
|---|---|---|
| 105 | Robotics | Bobby Williams |
| 202 | Taekwondo | Dima White |
| 101 | Robotics | Bobby Williams |
| 105 | Arts and Crafts | Jane Doe |

In the CLUB table, the StudentID is a foreign key (as it is a primary key in the STUDENT table). However, none of the fields in this table can act as a primary key, as they all have duplicates. But you could set the primary key to be a composite key, formed from the attributes StudentID and ClubTitle. On the other hand, you could add a new attribute ClubID to act as a primary key. In case there is a need for a single field to act as primary key, it is possible to combine data from several attributes into one to act as a concatenated key.

| TeacherClub | Location |
|---|---|
| Jane Doe Arts and Crafts | L101 |
| Bobby Williams Robotics | H203 |
| Dima White Taekwondo | B353 |

In the TEACHER table, the primary key is a concatenated key, formed from the attributes TeacherName and ClubTitle.

# A3.2.5 Differences between normal forms

+   * Normalization: the process of organizing data in a relational database in a way to reduce data redundancy and to improve data integrity.
+   * First normal form: the status of a relational database in which entities do not contain repeating groups of attributes.
+   * Atomic: each attribute in a table containing indivisible values (values that cannot be broken down into more detailed sub-values).

Data normalization represents the process of organizing data in a relational database in a way to reduce data redundancy and to improve data integrity. Data redundancy is reduced as each item of data only occurs in one location in the database. This can reduce the possibility of update anomalies occurring, and it makes more efficient use of memory. Normalization leads to smaller tables with less information in each row, which leads to a reduction of input / output transfers, and so the CPU can work at full capacity since the likelihood of CPU activities being suspended is reduced. Normalization is achieved through a series of stages called "normal forms", where each normal form has specific requirements for the table to be considered normalized at that level.

+   **First normal form (1NF)**
+   In first normal form, the table:
+   * has a primary key
+   * includes no duplicate attributes from the same table
+   * includes no repeated groups of attributes.

Therefore, you need to create separate tables for each group of related data, identifying each record by using the primary key, which is made of one single attribute or a set of attributes (composite or compound key), and ensure the entities do not contain repeated groups of attributes.

In 1NF, data in each field must be atomic. This means that each attribute contains indivisible values (values that cannot be broken down into more detailed sub-values). For example, could an attribute called TeacherName in the TEACHER table is not an atomic field as this could