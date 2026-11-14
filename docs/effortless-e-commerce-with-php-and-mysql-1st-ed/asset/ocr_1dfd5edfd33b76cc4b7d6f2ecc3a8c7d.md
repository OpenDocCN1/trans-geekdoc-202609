# # 3 FIRST SITE: STRUCTURE AND DESIGN

The first e-commerce site being developed in this book, Knowledge is Power, will provide content to paid subscribers. It will have these primary features:

+   - Straightforward use of HTML, PHP, and MySQL
+   - User accounts
+   - Ability for administrators to add HTML and PDF content
+   - PayPal for processing payments

This will be a relatively standard e-commerce example, applicable to most small- to medium-size businesses. By comparison, the more complex project, developed in Part Three, “Selling Physical Products,” of the book, will use HTML, PHP, and MySQL in more advanced ways, won’t require user accounts, will sell products that get shipped later (that is, the customer will not be billed immediately), and will integrate a different payment system. This is not to say that what you’ll learn in this part of the book won’t be applicable to real-world situations, quite the contrary.

The user account system will have several pieces: registering, logging in, logging out, retrieving forgotten passwords, and changing existing passwords. As a bonus, the user’s password will be handled with extra security, in a way that you perhaps have not yet seen.

The available content that the customer is paying to see will be in two formats: HTML and PDF. For the former, you’ll integrate a WYSIWYG editor into an HTML form so that administrators can easily create HTML without knowledge of