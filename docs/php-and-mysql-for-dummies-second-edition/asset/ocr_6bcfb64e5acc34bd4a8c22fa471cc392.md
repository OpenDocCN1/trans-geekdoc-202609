# Creating relationships between tables

Some tables in a database are related to one another. Most often, a row in one table is related to several rows in another table. A column is needed to connect the related rows in different tables. In many cases, you include a column in one table to hold data that matches data in the primary key column of another table.

A common application that needs a database with two related tables is a customer order application. For example, one table contains the customer information, such as name, address, phone, and so on. Each customer can have from zero to many orders. You could store the order information in the table with the customer information, but a completely new row would be created each time that the customer placed an order, and each new row would contain all the customer’s information. It would be much more efficient to store the orders in a separate table. The `Order` table would have a column that contains the primary key from a row in the `Customer` table so that the order is related to the correct row of the `Customer` table. The relationship is shown in the tables in Figures 3-2 and 3-3.

The `Customer` table in this example looks like Figure 3-2 (see the preceding section). Notice the unique `cust_id` for each customer.

The related `Order` table is shown in Figure 3-3. Notice that it has the same `cust_id` column that appears in the `Customer` table. In this way, the order information in the `Order` table is connected to the related customer’s name and phone number in the `Customer` table.

| Order_no | cust_id | item_num | cost |
|---|---:|---|---:|
| 87-222 | 27895 | cat-3 | 200.00 |
| 87-223 | 27895 | cat-4 | 225.00 |
| 87-224 | 44555 | horse-1 | 550.00 |
| 87-225 | 44555 | dog-27 | 210.00 |
| 87-226 | 27895 | bird-1 | 50.00 |

Figure 3-3: A sample from the `Order` table.