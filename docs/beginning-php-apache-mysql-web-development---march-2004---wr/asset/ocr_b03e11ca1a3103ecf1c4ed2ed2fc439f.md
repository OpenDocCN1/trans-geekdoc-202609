![](bbox=[0.396, 0.001, 0.603, 0.187])

# # Using PHP with MySQL

So now you've done some real stuff with PHP in Chapter 2, such as using includes and functions, it's time to make your site truly "dynamic" and show users some real data. You may or not have had experience with databases, so we'll take a look at what SQL is and how PHP can tap into the data. We will also show you what a MySQL database looks like in terms of different tables and fields, and give you some quick shortcuts to make your life much easier (you can thank us later for those).

By the end of this chapter, you will be able to:

+   - Understand a MySQL database
- View data contained in the MySQL database
- Connect to the database from your Web site
- Pull specific information out of the database, right from your Web site
- Use third-party software to easily manage tables
- Use the source Web to troubleshoot problems you may encounter

Although some of this information is expanded upon in later chapters, this chapter lays the groundwork for more complex issues.

# # Overview of MySQL Structure and Syntax

MySQL is a relational database system, which basically means that it can store information in separate areas and link those areas together. You can store virtually anything in a database. Information such as the contents of an address book, product catalog, or even a list of things you want for your birthday can be stored in your database.

In the sites you create as you work through this book, you are storing information pertinent to a movie review site (such as movie titles and years of release) and comic book fan information (as a list of authentic users/comic book fans and their passwords).