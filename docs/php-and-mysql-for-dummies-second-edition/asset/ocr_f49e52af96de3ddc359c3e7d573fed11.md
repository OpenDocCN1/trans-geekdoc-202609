+   - `CHAR(25)`: The data in this field is expected to be a character string that is 25 characters long.
+   - `PRIMARY KEY(petName,petColor)`: The primary key must be unique. For this table, two columns together are the primary key — this column and the `petColor` column. MySQL won’t allow two rows to be entered with the same `petName` and `petColor`.
+   - `NOT NULL`: This definition means that this field can’t be empty. It must have a value. The primary key must always be defined as `NOT NULL`.

✓ petColor: The color of the pet, such as orange or purple. The CREATE query defines the petColor in the following ways:

+   - `CHAR(15)`: This data type defines the field as a character string that’s 15 characters long.
+   - `PRIMARY KEY(petName,petColor)`: The primary key must be unique. For this table, two columns together are the primary key — this column and the `petName` column. MySQL won’t allow two rows to be entered with the same `petName` and `petColor`.
+   - `NOT NULL`: This definition means that this field can’t be empty. It must have a value. The primary key must always be defined as `NOT NULL`.

✓ pix: The filename containing the picture of the pet. The CREATE query defines pix in the following ways:

+   - `CHAR(15)`: This data type defines the field as a character string that is 15 characters long.
+   - `NOT NULL`: This definition means that this field can’t be empty. It must have a value. You need a picture for the pet. When a Web site tries to show a picture that can’t be found, it displays an ugly error message in the browser window where the graphic would go. You don’t want your catalog to do that, so your database should require a value. In this case, the CREATE query defines a default value so that a value will always be placed in this field.
+   - `DEFAULT "na.gif"`: The value "na.gif" is stored if you don’t provide a value for pix. In this way, a value is always stored for pix. The file na.gif might contain a graphic that reads something like picture not available.

# Adding data to the database

You can add the data to the database many ways. You can use SQL queries to add pets to the database, or you can use the application that I describe in this chapter. My personal favorite during development is to add a few sample items to the catalog by reading the data from a file. Then, whenever my data