# # Chapter 14

# Shopping Cart

# ## IN THIS CHAPTER

+   - Creating a secure site
+   - Working with PHP sessions
+   - Communicating with a credit-card-authorization service

IN THIS CHAPTER YOU are going to learn what you need to create a shopping-cart application using PHP and MySQL. But this application is different from the others in this book in that it's really impossible to talk about what you need for it without delving into some other topics. In addition to understanding the schema and the PHP code, you need to have a basic understanding of how to maintain state between pages. (If you don't know what that means, don't worry, we'll get to it momentarily.) Also, you need to know how to securely process credit-card transactions.

Don't read another sentence if you have not read through Chapter 12. You must understand how the catalog works before you can take this on. For reasons that shouldn't be too tough to understand, we built the shopping cart atop the catalog.

# # Determining the Scope and Goals of the Application

Anyone familiar with the Web knows what a shopping cart does. But it will be a bit easier to understand what the code for this application is doing if we explicitly state some of its purposes.

First, the application is going to have to display your wares; for this you reuse the code from Chapter 12. Further, users have to be able to choose items that they want to buy. Obvious, we know. Note what must happen after a user chooses an item: The exact item must be noted, and the user should have the opportunity to continue shopping. The server must remember what has been ordered. As the user continues to browse, the server must keep track of the user and allow him or her to check out with his or her requested items.