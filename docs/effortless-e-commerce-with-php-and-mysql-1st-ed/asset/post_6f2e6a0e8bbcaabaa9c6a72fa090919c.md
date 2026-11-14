
In PHP, you can use the mysql_query() function to execute a stored procedure:

```
$r = mysql_query("CALL get_non_coffee_products($id)");
```

Then you can use the mysql_fetch_array() function to get the results.

The last thing you should know is that you can create stored procedures, using phpMyAdmin, the mysql command-line client, or whatever, just as you can execute any other query, provided that you're connected to the database as a user with that permission. This is to say that the MySQL user involved must have **CREATE ROUTINE** permissions, which will normally also mean they have **ALTER ROUTINE** and **EXECUTE** permissions. Unfortunately, I can't personally say how common it is for different Web hosts to allow stored procedures.

MySQL permissions with respect to stored procedures are more complicated than I'm presenting here. See the MySQL manual if you want all the details.

If your server environment makes using stored procedures impossible, you'll need to move all the logic and SQL back into your PHP scripts, and execute the SQL commands as you would standard queries.

## 8 | CREATING A CATALOG

After preparing the server for the site (see the previous chapter), the next step is to start creating the catalog, because the customer can’t shop without it. To do so, you’ll need to prepopulate the database with some products, since you won’t develop the administrative scripts for adding products until Chapter 11, “Site Administration.” Then you can write the two PHP scripts for generating the catalog: one for browsing by category and a second for listing specific products.

After that, the chapter demonstrates better ways to show the availability of products and any applicable sale prices. From there, you’ll write new PHP scripts for showing the sale items on their own.

If you have intermediate PHP and MySQL experience, nothing in this chapter should be too challenging for you, although you will learn some new tricks. The SQL queries in this chapter are some of the most complex in the book, and they’ll be wrapped inside stored procedures to boot. You’ll also see a real-world way of implementing the MVC design pattern in a moderately complex site.

### PREPARING THE DATABASE

Half of the database tables will be used by the code in this chapter. In order to see any results in the Web browser, you’ll need to insert some records into these first. For three of these tables — general_coffees, non_coffee_categories, and sizes, there will not be an administration page. The data in all three tables should be fairly stable, and if you want administrative capability over them, it would be easy enough for you to create corresponding administrative pages yourself. For the other three tables — specific_coffees, non_coffee_products,

and sales, you'll create administrative scripts, but not until Chapter 11. For now, you'll populate these tables using just SQL, and then create the three stored procedures used by the PHP scripts in this chapter.

### Populating the Tables Using SQL

You can populate any database table via any interface to the MySQL database, the two most common being the Web-based phpMyAdmin and the command-line mysql client. With phpMyAdmin, which is what your Web host likely provides (perhaps indirectly through another control panel), you can use the SQL tab or the SQL query window (Figure 8.1) to enter SQL commands.

> phpMyAdmin also provides an insert option that presents forms through which you can add multiple records to a table.

![](img/4f47e47c67bd619ac73250f11c9fc7ce_209_0.png)

Figure 8.1

With the command-line mysql client, you first need to access the server via a command-line interface (even if that's your own computer). How you do this will depend upon the operating system you're using:

- On Windows, click Start, and then Run. Enter cmd in the Run prompt and click OK.
- On Mac OS X, open the /Applications/Utilities/Terminal program.
- Most versions of Linux also have a Terminal application.

Once you're in the command-line environment, you can access the database using:

```
mysql -u username -p ecommerce2
```

> You can also use your computer's command-line interface to access your server via the command-line using ssh.

Provide a real username and, at the prompt, enter that user's password. This command, should it work (that is, should the username and password be correct), will also select the ecommerce2 database automatically. Change that part of the command if your database is named differently.

If you're using an all-in-one installer, such as XAMPP (www.apachefriends.org) or MAMP (www.mamp.info), you'll need to specify the full path to that version of the mysql client (Figure 8.2 on the next page):

```
/Applications/MAMP/Library/bin/mysql -u username -p ecommerce2
```

![](img/4f47e47c67bd619ac73250f11c9fc7ce_210_0.png)

Figure 8.2

Once you've accessed the database via any interface, you can start populating the tables (assuming you've already defined them).

> > **tip**
> > All the SQL commands can be downloaded from www.DMCinsights.com/ecom/.

- 1. Populate the sizes table:

```sql
INSERT INTO `sizes` (`size`) VALUES
('2 oz. Sample'), ('Half Pound'), ('1 lb.'), ('2 lbs.'), ('5 lbs.');
```

The sizes table is used by the specific_coffees table to indicate in what quantities someone can buy coffee. The table only has a primary key column and a size column. This query adds five values to the table.

- 2. Populate the non_coffee_categories table:

```sql
INSERT INTO `non_coffee_categories` (`category`, `description`, `image`)
VALUES
('Edibles', 'A wonderful assortment of goodies to eat. Includes biscotti,
baklava, lemon bars, and more!', 'goodies.jpg'),
('Gift Baskets', 'Gift baskets for any occasion! Including our many coffees
and other goodies.', 'gift_basket.jpg'),
('Mugs', 'A selection of lovely mugs for enjoying your coffee, tea, hot
cocoa or other hot beverages.', '781426_32573620.jpg'),
('Books', 'Our recommended books about coffee, goodies, plus anything
written by Larry Ullman', 'books.jpg');
```

The non_coffee_categories table represents the categories of non-coffee items the site will sell. The three non-primary key columns are category, description, and image. For the images, you’ll need to create a representative image for each category, with a matching image name. The images should be placed within the products directory (see Figure 7-5). You can, of course, just copy the images available in the downloadable code from the book’s corresponding Web site.

> > **tip**
> > See Chapter 7, “Second Site: Structure and Design,” for a discussion of the database’s tables.

- 3. Populate the general_coffees table:

```sql
INSERT INTO `general_coffees` (`category`, `description`, `image`) VALUES
('Original Blend', 'Our original blend, featuring a quality mixture of bean and a medium roast for a rich color and smooth flavor.', 'original_coffee.jpg'),
('Dark Roast', 'Our darkest, non-espresso roast, with a full flavor and a slightly bitter aftertaste.', 'dark_roast.jpg'),
('Kona', 'A real treat! Kona coffee, fresh from the lush mountains of Hawaii. Smooth in flavor and perfectly roasted!', 'kona.jpg');
```

This table has the exact same structure as non_coffee_categories. Again, grab the images from the downloadable stuff and place them in your products folder.

- 4. Populate the non_coffee_products table:

```sql
INSERT INTO `non_coffee_products` (`non_coffee_category_id`, `name`, 
`description`, `image`, `price`, `stock`, `date_created`) VALUES 
(3, 'Pretty Flower Coffee Mug', 'A pretty coffee mug with a flower design on a 
white background.', 'd9996aee56392093bfb618b07e10a34b27baad12.jpg', 
6.50, 100, NOW()),
(3, 'Red Dragon Mug', 'An elaborate, painted gold dragon on 
a red background. With partially detached, fancy handle.', 
'847a1a3bef0bf5c2f2299b06dd6366900f5c6c4.jpg', 7.95, 4, NOW());
```

In Chapter 11, you'll create a PHP script that does all the heavy lifting for you, so let's just create a couple of records in this table for now. Each product has a non_coffee_category_id of 3, which is Mugs. A specific name and description is provided, along with an image's name (also to be placed in the products directory). Next come the price and the quantity in stock. To test how stock availability will be handled, one product has plenty of stock and another very little.

- 5. Populate the specific_coffees table:

```sql
INSERT INTO `specific_coffees` (`general_coffee_id`, `size_id`, 
`caf_decaf`, `ground_whole`, `price`, `stock`, `date_created`) VALUES 
(3, 1, 'caf', 'ground', 2.00, 20, NOW()),
(3, 2, 'caf', 'ground', 4.50, 30, NOW()),
(3, 2, 'decaf', 'ground', 5.00, 20, NOW()),
(3, 3, 'caf', 'ground', 8.00, 50, NOW()),
(3, 3, 'decaf', 'ground', 8.50, 20, NOW()),
(3, 3, 'caf', 'whole', 7.50, 50, NOW()),
(3, 3, 'decaf', 'whole', 8.00, 20, NOW()),
(3, 4, 'caf', 'whole', 15.00, 30, NOW()),
(3, 4, 'decaf', 'whole', 15.50, 15, NOW()),
(3, 5, 'caf', 'whole', 32.50, 5, NOW());
```

To create specific coffee products to sell, you're actually creating multiple products of one coffee type (Kona, with a general_coffee_id of 3).
