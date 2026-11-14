# DATABASE DESIGN

Since the *Coffee* site is more complex than the *Knowledge is Power* example, the database is correspondingly more involved. I've come up with 12 tables, evenly split between those for representing the catalog of products and those associated with the customers and orders.

# Product Tables

Six customer-related tables represent the specifics about all the products available on the *Coffee* site (Figure 7-3).

![](bbox=[0.305, 0.338, 0.765, 0.562])

Figure 7-3

The *non_coffee_categories* table represents the types of non-coffee products that will be sold: books, mugs, edibles, and so on. This table stores the category name, a description, and an image (the image will display on a page that lists the categories). The *non_coffee_products* table has a many-to-one relationship with *non_coffee_categories*. Each product will be in one category and each category will have multiple products (Figure 7-3). The *non_coffee_products* table has a foreign key, name, description, image, price, stock, and creation-date columns. This table represents the specific non-coffee products that customers will purchase, and its id field will become part of the product's SKU. The *stock* field contains an indication of the quantity of the item in stock, not a simple *Yes/No*.

**tip**

The *price* column is defined as `DECIMAL(5,2)`, meaning that it can have up to five numbers with up to three numbers to the left of the decimal and will have exactly two to the right.

**tip**

If you're selling variations on a product, like clothing in different sizes and colors, you'd use a structure similar to the coffee tables.

The *general_coffees* and *specific_coffees* tables have a parallel relationship to the two non-coffee tables. The *general_coffees* table is defined exactly like *non_coffee_categories* and will represent the primary types of coffee sold. For those types, I'm using a somewhat pedestrian organization, mixing roasts, bean types, and flavors: original, dark roast, vanilla, Kona, and so on. If the