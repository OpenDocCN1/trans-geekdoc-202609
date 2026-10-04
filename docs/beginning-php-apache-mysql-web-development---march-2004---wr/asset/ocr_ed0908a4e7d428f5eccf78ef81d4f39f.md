# Online Selling: A Quick Way to E-Commerce

# How It Works

Of course, there are comments throughout the code, but here is a rundown of what this script accomplishes.

+   Before we can enter anything else, we have to determine whether or not our customer is new or returning. If he or she is assigned a returning customer, we want to keep the existing customer number, and if new, he or she will be assigned the next customer number in line. Of course, this is a fail-safe plan: We check for the first name, last name, two lines of address, and city. A returning customer would just have to abbreviate differently to be considered "new." We talk more about later in this chapter.

We use the PHP function mysql_insert_id to get the auto-increment value that was just added to the database. This helps us make sure we are keeping all the information from the sample order together.

+   Once we have the customer information entered in the database, we can then enter the order-specific information. This includes the date and order number, as well as the shipping information associated with that order. We also tabulated the shipping costs as a percentage of total cost of the order (25 percent), but you can set your shipping costs to be whatever you like.

+   We can enter the order detail information with all the specific items that have been placed in the shopping cart.

+   We delete the temporary information, as we don't need it anymore.

+   We also send a confirmation email to our customer, and to ourselves to let us know an order was placed.

+   We display the order confirmation on the page to let the customer know immediately that the order was received and give to him or her order number.

This is the end of our simple shopping cart script.

# E-Commerce, Any You Slice It

As we briefly mentioned before, you can integrate e-commerce into your site the right way and you can do it the wrong way. Prevent yourself from looking like a idiot and virtually ensuring e-commerce failure, we recommend doing things the right way: Good-of-mouth travels slowly, but we know how quickly bad-of-mouth spreads. Also, with so many millions of sites out there competing for attention, we want elevate yours above the rest.

This may sound harsh, but there are some things to remember about some of the most challenging characteristics of your potential customers:

+   Your customers are impatient. They don't want to wait for your pages to load or for answers to their questions. They are busy people, just like you, and if they don't find what they need right away, they're out there and on something else.

+   Your customers are distrustful. Who wants their personal information strewn all over the Web? You certainly don't, and they don't. They don't want your credit card number to be used by every geek in your office, and they don't want to give tons of money and never see the product they purchased. They don't want to order from you one week and have you go bankrupt next.