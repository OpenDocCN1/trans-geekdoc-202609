# Chapter 9

# Survey

# IN THIS CHAPTER

+   - Learning functions for creating HTML tags
+   - Understanding data that use a relational structure
+   - Putting MySQL's date functions to work
+   - Working with PHP's error-handling functions

If GUESTBOOKS are the most common type of application on the Web, surveys are probably second in popularity. Many sites have some sort of widget that enables you to choose you favorite color or sports hero, or whatever, to see what percentage of voters take what stance.

This application will be a bit more complex than the guestbook application you saw in Chapter 8. The programming will get a bit trickier, and the administration of the application will require more work. Unlike the guestbook, this application will require some knowledge of database theory. Related tables, complete with the primary and foreign keys, appear in Part I of this book. This means that your SQL queries will include joins.

# Determining the Scope and Goals of the Application

The problem with the Web is that it can be mighty impersonal. You surf around, look at pages, search for information, and have advertisements try to sell you things. But you don't see much evidence of other human beings. A survey on a site gives surfers a clue that other people have been by and that it's possible to leave a mark that others will see later.

A survey application can be ultra-simple. If you want only to gather responses to a single question and return basic statistical information on the responses (how many votes for choice A, B, and so on), you don't need a whole lot of code (or a chapter explaining it). A single table to store answers would do the trick. The question can even be hard-coded into the HTML for the Web site. But that would not make for very interesting learning experience, would it?