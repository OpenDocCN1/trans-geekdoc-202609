# # STORED PROCEDURES REVISITED

The modestly complex **add_order()** stored procedure demonstrates the security and performance benefits that can be had by using stored procedures. The procedure takes just four arguments—the customer ID, the customer's cart session ID, the shipping total, and the credit card representation—and does a lot of work with that little information. The procedure could even be cut down to just two inbound arguments if the shipping were to be calculated by a database-stored function and the credit card numbers were omitted (they'll be stored in the **transactions** table anyway). From a performance standpoint, there's very little information that PHP needs to send to the database, and, more critically, the PHP script only needs to execute a single query—the procedure call itself. Since query executions are one of the most demanding things a PHP script does, limiting those

can have a huge performance gain. (Although that burden is therefore moved to the database server.) From a security standpoint, much of the key information—like the price a product is sold for—never leaves the database, making it that much harder to be manipulated. And no PHP script directly accesses any of the database tables, adding a layer of obfuscation. I should add that you might logically use transactions in this stored procedure, which stored procedures do support. By using transactions, every query would have to work properly or else the entire process would be reverted. Such an approach prevents an incomplete order from being recorded. Still, I opted not to use transactions, because they would further complicate an already complicated process.

# # TAKING THE SHIPPING INFORMATION

Once the customer is finished shopping and is ready to purchase items, he or she will click a button on the shopping cart page that will go to **checkout.php** (over HTTPS). This page needs to:

+   1. Take the customer's shipping information.
+   
+   2. Validate the provided data.
+   
+   3. If valid, store the data and send the customer on to the next step in the checkout process.
+   
+   4. If invalid, redisplay the form with errors.

In terms of displaying and validating the form, **checkout.php** behaves like **register.php** from Chapter 4. But there are some additional considerations that make this script more complicated than that one. Let's first define the PHP script, then the two view files it uses.