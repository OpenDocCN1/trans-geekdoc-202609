# Working with Other Databases

Apart from MySQL, PHP supports almost all relevant (and some not-so-relevant ones, as well) databases on Earth. This chapter features the basic techniques used with many of those systems, especially connecting to the database, executing SQL statements, and retrieving the return data. As in Chapter 8, “Working with MySQL Databases,” we are using a sample database called phrasebook and a sample schema/table from within it called quotes, with the following four fields:

+   - id—An integer value that is increased by one for each new entry entered into the database. Depending on the database system, the data type is either called IDENTITY, auto_increment, or something similar.
+   - quote—The quote, as a VARCHAR(255); this length works with all systems.
+   - author—The person who produced the quote, as a VARCHAR(50).
+   - year—The year the quote was produced, of type INT.