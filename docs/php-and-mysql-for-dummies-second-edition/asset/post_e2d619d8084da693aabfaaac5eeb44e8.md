
- NOT NULL: This definition means that this field can't be empty. It must have a value. The primary key must always be set to NOT NULL.

- typeDescription: A description of the pet type. The CREATE query defines the typeDescription in the following way:
  - VARCHAR(255): The string in this field is expected to be a variable character string that can be up to 255 characters long. The field is stored in its actual length.

## Building the Color table

When I discuss building the Pet table (see “Building the Pet table,” earlier in this chapter), I discuss the different kinds of pets: pets that are unique (such as puppies and horses) and pets that are not unique (such as goldfish and turtles). For unique pets, the customer needs to see a picture of the actual pet. For pets that aren’t unique, the customer only needs to see a generic picture.

In some cases, generic pets come in a variety of colors, such as blue parakeets and green parakeets. You might want to show two pictures for parakeets: a picture of a blue parakeet and a picture of a green parakeet. However, because most pets aren’t this kind of generic pet, you don’t want to add a color column to your main Pet table because it would be blank for most of the rows. Instead, you create a separate table containing only pets that come in more than one color. Then when the catalog application is showing pets, it can check the Color table to see whether there’s more than one color available — and if there is, it can show the pictures from the Color table.

The Color table points to pictures of pets when the pets come in different colors so that the catalog can show pictures of all the available colors. The following SQL query creates the Color table:

```
CREATE TABLE Color (
  petName      CHAR(25)      NOT NULL,
  petColor     CHAR(15)      NOT NULL,
  pix          CHAR(15)      NOT NULL DEFAULT "na.gif",
  PRIMARY KEY(petName,petColor) );
```

Each row represents a pet type. The columns are as follows:

✓ petName: The name of the pet, such as lion, collie, or Chinese bearded dragon. Notice that the petName column is defined the same in the Pet table and in this table. This makes table joining possible and makes matching rows in the tables much easier. However, the petName is the primary key in this table but not in the Pet table. The CREATE query defines the petName in the following ways:

- `CHAR(25)`: The data in this field is expected to be a character string that is 25 characters long.
- `PRIMARY KEY(petName,petColor)`: The primary key must be unique. For this table, two columns together are the primary key — this column and the `petColor` column. MySQL won’t allow two rows to be entered with the same `petName` and `petColor`.
- `NOT NULL`: This definition means that this field can’t be empty. It must have a value. The primary key must always be defined as `NOT NULL`.

✓ petColor: The color of the pet, such as orange or purple. The CREATE query defines the petColor in the following ways:

- `CHAR(15)`: This data type defines the field as a character string that’s 15 characters long.
- `PRIMARY KEY(petName,petColor)`: The primary key must be unique. For this table, two columns together are the primary key — this column and the `petName` column. MySQL won’t allow two rows to be entered with the same `petName` and `petColor`.
- `NOT NULL`: This definition means that this field can’t be empty. It must have a value. The primary key must always be defined as `NOT NULL`.

✓ pix: The filename containing the picture of the pet. The CREATE query defines pix in the following ways:

- `CHAR(15)`: This data type defines the field as a character string that is 15 characters long.
- `NOT NULL`: This definition means that this field can’t be empty. It must have a value. You need a picture for the pet. When a Web site tries to show a picture that can’t be found, it displays an ugly error message in the browser window where the graphic would go. You don’t want your catalog to do that, so your database should require a value. In this case, the CREATE query defines a default value so that a value will always be placed in this field.
- `DEFAULT "na.gif"`: The value "na.gif" is stored if you don’t provide a value for pix. In this way, a value is always stored for pix. The file na.gif might contain a graphic that reads something like picture not available.

## Adding data to the database

You can add the data to the database many ways. You can use SQL queries to add pets to the database, or you can use the application that I describe in this chapter. My personal favorite during development is to add a few sample items to the catalog by reading the data from a file. Then, whenever my data

becomes totally bizarre during development (as a result of programming errors or my weird sense of humor), I can re-create the data table in a moment. Just DROP the table, re-create it with the SQL query, and reread the sample data.

For example, the data file for the Pet table might look like this:

```
<TAB>Pekinese<TAB>Dog<TAB>Small, cute, energetic. Good alarm system.<TAB>100.00<TAB>peke.jpg
<TAB>House cat<TAB>Cat<TAB>Yellow and white cat. Extremely playful.<TAB>20.00<TAB>catyellow.jpg
<TAB>House cat<TAB>Cat<TAB>Black cat. Sleek, shiny. Likes children.<TAB>20.00<TAB>catblack.jpg
<TAB>Chinese Bearded Dragon<TAB>Lizard<TAB>Grows up to 2 feet long. Fascinating to watch. Likes to be held.<TAB>100.00<TAB>lizard.jpg
<TAB>Labrador Retriever<TAB>Dog<TAB>Black dog. Large, intelligent retriever. Often selected as guide dogs for the blind.<TAB>100.00<TAB>lab.jpg
<TAB>Goldfish<TAB>Fish<TAB>Variety of colors. Inexpensive. Easy care. Good first pet for small children.<TAB>2.00<TAB>goldfish.jpg
<TAB>Shark<TAB>Fish<TAB>Sleek. Powerful. Handle with care.<TAB>200.00<TAB>shark.jpg
<TAB>Asian Dragon<TAB>Dragon<TAB>Long and serpentine. Often gold or red.<TAB>10000.00<TAB>dragona.jpg
<TAB>Unicorn<TAB>Horse<TAB>Beautiful white steed with spiral horn on forehead.<TAB>20000.00<TAB>unicorn.jpg
```

These are the data file rules:

- ✔ The <TAB> tags represent real tabs — the kind that you create by pressing the Tab key.
- ✔ Each line represents one pet and must be entered without pressing the Enter or Return key. The lines in the preceding example are shown wrapped to more than one line so that you can see the whole line. However, in the actual file, the data lines are one on each line.
- ✔ A tab appears at the beginning of each line because the first field is not being entered. The first field is the petID, which is entered automatically; you don’t need to enter it. However, you do need to use a tab so that MySQL knows there’s a blank field at the beginning.

You can then use an SQL query to read the data file into the Pet table:

```
LOAD DATA LOCAL INFILE "pets" INTO TABLE Pet;
```

Any time that the data table gets odd, you can re-create it and read the data in again.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_324_0.png)

**Figure 11-1:** The opening page of the Pet Store Web site.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_324_1.png)

**Figure 11-2:** The pet type page of the Pet Store Web site.

## Pets page

The pets page lists all the pets of the selected type. Each pet is listed with its petID, description, price, and picture. The pets page appears in a different format, depending on the information in the catalog database. Figures 11-3, 11-4, and 11-5 show some possible pets pages. Figure 11-3 shows a page listing three different dogs from the catalog.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_325_0.png)

Figure 11-3:
This pets page shows three different dogs.

Figure 11-4 shows that more than one pet can have the same pet name. Notice that the house cats have different petID numbers.

Figure 11-5 shows the output when pets are found in the Color table, showing more than one color is available.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_326_0.png)

**Figure 11-4:** This pet page shows three cats with the same pet name.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_326_1.png)

**Figure 11-5:** This pet page shows goldfish that are available in two colors.
