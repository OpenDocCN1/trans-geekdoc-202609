+   - NOT NULL: This definition means that this field can't be empty. It must have a value. The primary key must always be set to NOT NULL.
+   
+   - typeDescription: A description of the pet type. The CREATE query defines the typeDescription in the following way:
+     - VARCHAR(255): The string in this field is expected to be a variable character string that can be up to 255 characters long. The field is stored in its actual length.

# Building the Color table

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