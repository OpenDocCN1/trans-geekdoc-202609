# Summary

In this, the final application of the book, you've seen a few interesting things. You've learned that an application like a shopping cart requires some method of maintaining state. Probably the best way to maintain state with PHP for something like a shopping cart is with sessions.

If you wish to process credit cards, you will need a secure server, an SSL certificate, and a set of functions for processing cards. In this application we used the cURL functions for credit card processing, but there are two other function sets (PayfloPro and Cyberscash) that you should look into.

The final thing to note in this chapter is how classes were used. By extending existing classes, and writing methods to overwrite previous methods, we were able to flexibly use large blocks of code.