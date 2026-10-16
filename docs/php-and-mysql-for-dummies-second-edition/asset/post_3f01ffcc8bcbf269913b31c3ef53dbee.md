
## Adding pets to the catalog

You can add items to your catalog several ways. However, the task of adding an item to the catalog is much easier if you use an application designed for adding your specific products. In many cases, you aren’t the person who will be adding products to your catalog. One reason for adding maintenance functionality to your catalog application is so that someone else can do those boring maintenance tasks. The easier it is to maintain your catalog, the less likely that errors will sneak into it.

An application to add a pet to your catalog should do the following:

- 1. **Prompt the user to enter a pet type for the pet.** A selection list of possible pet types would eliminate many errors, such as alternate spellings (*dog* and *dogs*) and misspellings. The application also needs to allow the user to add new categories when needed.
- 2. **Prompt the user to enter a name for the pet**, such as *collie* or *shark*. A selection list of names would help prevent mistakes. The application also needs to allow the user to add new names when needed.
- 3. **Prompt the user to enter the pet information for the new pet.** The application should clearly specify what information is needed.
- 4. **Store the information in the catalog.**

The catalog entry application can check the data for mistakes and enter the data into the correct locations. The person entering the new pet doesn’t need to know the inner workings of the catalog.

## Building the Database

The catalog itself is a database. It doesn’t have to be a database; it’s possible to store a catalog as a series of HTML (HyperText Markup Language) files that contain the product information in HTML tags and display the appropriate file when the customer clicks a link. However, it makes my eyes cross to think of maintaining such a catalog. Imagine the tedium of adding and removing catalog items manually . . . or finding the right location for each item by searching through many files. Ugh. For these reasons, putting your Pet Catalog in a database is better.

The PetCatalog database contains all the information about pets. It uses three tables:

- Pet table
- PetType table
- Color table

The first step in building the Pet Catalog is to build the database. It’s pretty much impossible to write programs without a working database to test the programs on. First you design your database; then you build it; then you add the data (or at least some sample data to use while developing the programs).

![](img/d82df0828cfbc6d6be1e9a991861f3b7_316_0.png)

Some changes have been made to the database design in Chapter 3 for the Pet Catalog. Development and testing often result in changes. Perhaps you find that you didn’t take some factors into consideration in your design or that certain elements of your design don’t work with real-world data or are difficult to program. It’s perfectly normal for the design to evolve while you work on your application. Just be sure to change your documentation when your design changes.

## Building the Pet table

In your design for the Pet Catalog, the main table is the Pet table. It contains the information about the individual pets that you sell. The following SQL query creates the Pet table:

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

Each row of the Pet table represents a pet. The columns are as follows:

- **petID:** A sequence number for the pet. In another catalog, this might be a product number, a serial number, or a number used to order the product. The `CREATE` query defines the `petID` column in the following ways:
- `INT(5)`: The data in the field is expected to be a numeric integer. The database won’t accept a character string in this field.
- `PRIMARY KEY(petID)`: This is the primary key, which is the field that must be unique. MySQL will not allow two rows to be entered with the same `petID`.
- `NOT NULL`: This definition means that this field can’t be empty. It must have a value. The primary key must always be set to `NOT NULL`.
- `AUTO-INCREMENT`: This definition means that the field will automatically be filled with a sequential number if you don’t provide a specific number. For example, if a row is added with 98 for a `petID`, the next row will be added with 99 for the `petID` unless you specify a different number. This is a useful way of specifying a column.

pix: The filename of the picture of the pet. Pictures on a Web site are stored in graphic files with names like dog.jpg, dragon.gif, or cat.png. This field stores the filename for the picture that you want to show for this pet. The CREATE query defines pix in the following ways:

- `CHAR(15)`: The data in this field is expected to be a character string that's 15 characters long. For some applications, the picture files might be in other directories or on other Web sites requiring a longer field, but for this application, the pictures are all in a directory on the Web site and have short names. The field will always take up 15 characters of storage, with padding if the actual string stored is less than 15 characters.
- `NOT NULL`: This definition means that this field can't be empty. It must have a value. You need a picture for the pet. When a Web site tries to show a picture that can't be found, it displays an ugly error message in the browser window where the graphic would go. You don't want your catalog to do that, so your database should require a value. In this case, you define a default value so that a value will always be placed in this field.
- `DEFAULT "na.gif"`: The value "na.gif" is stored if you don't provide a value for pix. In this way, a value is always stored for pix. The na.gif file might be a graphic that reads something like: "picture not available".

Notice the following points about this database table design:

![](img/d82df0828cfbc6d6be1e9a991861f3b7_318_0.png)

**Some fields are CHAR, and some are VARCHAR.** CHAR fields are faster, whereas VARCHAR fields are more efficient. Your decision will depend on whether disk space or speed is more important for your application in your environment.

In general, shorter fields should be CHAR because shorter fields don't waste much space. For instance, if your CHAR is 5 characters, the most space that you could possibly waste is 4. However, if your CHAR is 200, you could waste 199. Therefore, for short fields, use CHAR for speed with very little wasted space.

**The petID field means different things for different pets.** The petID field assigns a unique number to each pet. However, a unique number is not necessarily meaningful in all cases. For example, a unique number is meaningful for an individual kitten but not for an individual goldfish.

There are really two kinds of pets. One is the unique pet, such as a puppy or a kitten. After all, the customer buys a specific dog — not just a generic dog. The customer needs to see the picture of the actual animal. On the other hand, some pets are not especially unique, such as a goldfish or a parakeet. When customers purchase a goldfish, they see a

tank full of goldfish and point at one. The only real distinguishing characteristic of a goldfish is its color. The customer doesn’t need to see a picture of the actual fish in your catalog, just a picture of a generic goldfish, perhaps showing the possible colors.

In your catalog, you have both kinds of pets. The catalog might contain several pets with the name cat but with different petIDs. The picture would show the individual pet. The catalog also contains pets that aren’t individuals but that represent generic pets, such as goldfish. In this case, there’s only one entry with the name goldfish, with a single petID.

I’ve used both kinds of pets in this catalog to demonstrate the different kinds of products that you might want to include in a catalog. The unique item catalog might include such products as artwork or vanity license plates. When the unique item is sold, it’s removed from the catalog. Most products are more generic, such as clothing or automobiles. Although a picture shows a particular shirt, many identical shirts are available. You can sell the shirt many times without having to remove it from the catalog.

## Building the PetType table

You assign each pet a type, such as dog or dragon. The first Web page of the catalog lists the types for the customer to select from. A description of each type is also helpful to show. You don’t want to put the type description in the main Pet table because the description would be the same for all pets with the same category. Repeating information in a table violates good database design.

The PetCatalog database includes a table called PetType that holds the type descriptions. The following SQL query creates the PetType table:

```
CREATE TABLE PetType (
petType CHAR(15) NOT NULL,
typeDescription VARCHAR(255),
PRIMARY KEY(petType) );
```

Each row of this table represents a pet type. These are the columns:

petType: The type name. Notice that the petType column is defined the same in the Pet table (which I describe in the preceding section) and in this table. This makes table joining possible and makes matching rows in the tables much easier. However, the petType is the primary key in this table but not in the Pet table. The CREATE query defines the petType column in the following ways:

- CHAR(15): The data in this field is expected to be a character string that’s 15 characters long.
- PRIMARY KEY(petType): This definition sets the petType column as the primary key. This is the field that must be unique. MySQL will not allow two rows to be entered with the same petType.
