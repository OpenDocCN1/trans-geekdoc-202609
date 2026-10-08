# Database

To read data from a database, use the following function:
>>> pd.read_sql_table(table_name, con)
The previous command creates a DataFrame. Suppose a table name and an SQLAlchemy engine are provided, they return a DataFrame. This function doesn't support the DBAPI connection. Below is the description of the above parameters.

+   - Table_name: As the name suggests, it refers to the name of the SQL table within a database.
- Con: Refers to the SQLAlchemy engine.

The command below reads SQL query into a DataFrame:
>>> pd.read_sql_query(sql, con)
Below is the description of the parameters applied:

+   - Sql: References the sql query that is supposed to be executed.
- Con: Refers to the SQLAlchemy engine.

# Cleansing of Data

Data, while in row form, deserves some cleaning before it can be analyzed or a dashboard builds on it. There are many factors that may make data to have problems. For example, the Point of Sale system at a retail shop may have malfunctioned and entered some data with missing values. This section will teach you how to handle such data.

# Search for Missing Data

In general, most data will feature missing values. There could be different reasons for this: the source which gathers the data might not have collected the values, or the values may never have existed. Once you have data loaded, it is important to search for the missing features in the data. Based on the requirements, the missing data has to be handled. It can be taken care of by eliminating a row or replacing a missing value with an alternative value.

In the case of the Student Weight data, to verify whether the location column has missing value, you can use the command below:

```
>>> d['Location 1'].isnull()
```