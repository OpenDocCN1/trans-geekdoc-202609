The first step in building the Pet Catalog is to build the database. It’s pretty much impossible to write programs without a working database to test the programs on. First you design your database; then you build it; then you add the data (or at least some sample data to use while developing the programs).

![](bbox=[0.121, 0.216, 0.207, 0.287])

Some changes have been made to the database design in Chapter 3 for the Pet Catalog. Development and testing often result in changes. Perhaps you find that you didn’t take some factors into consideration in your design or that certain elements of your design don’t work with real-world data or are difficult to program. It’s perfectly normal for the design to evolve while you work on your application. Just be sure to change your documentation when your design changes.

# Building the Pet table

In your design for the Pet Catalog, the main table is the Pet table. It contains the information about the individual pets that you sell. The following SQL query creates the Pet table:

```
```sql
CREATE TABLE Pet (
    petID               INT(5)             NOT NULL AUTO_INCREMENT,
    petName             CHAR(25)            NOT NULL,
    petType             CHAR(15)            NOT NULL DEFAULT "Misc",
    petDescription      VARCHAR(255),
    price               DECIMAL(9,2),
    pix                 CHAR(15)            NOT NULL DEFAULT "na.gif",
    PRIMARY KEY(petID) );
```
```

Each row of the Pet table represents a pet. The columns are as follows:

+   - **petID:** A sequence number for the pet. In another catalog, this might be a product number, a serial number, or a number used to order the product. The `CREATE` query defines the `petID` column in the following ways:
+     - `INT(5)`: The data in the field is expected to be a numeric integer. The database won’t accept a character string in this field.
+     - `PRIMARY KEY(petID)`: This is the primary key, which is the field that must be unique. MySQL will not allow two rows to be entered with the same `petID`.
+     - `NOT NULL`: This definition means that this field can’t be empty. It must have a value. The primary key must always be set to `NOT NULL`.
+     - `AUTO-INCREMENT`: This definition means that the field will automatically be filled with a sequential number if you don’t provide a specific number. For example, if a row is added with 98 for a `petID`, the next row will be added with 99 for the `petID` unless you specify a different number. This is a useful way of specifying a column.